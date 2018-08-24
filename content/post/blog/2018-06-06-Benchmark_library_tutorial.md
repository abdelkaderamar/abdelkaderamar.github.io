---
categories:
- Tutorials
- Posts
classes: wide
date: 2018-06-06T21:30:00Z
'tags:':
- C++
title: La bibliothèque *Benchmark*
---

{% include toc %}

## Introduction
*Benchmark* est une bibliothèque C++ développée par *Google* pour faire des
mesures de performances de fonctions. Son installation sous linux peut se faire
soit par compilation du code source disponible sur *Github* ou si la
distribution la propose en utilisant le gestionnaire de package. *Ubuntu* dans
sa version 18.1 propose la version 1.36 dans ses sources *apt*.

## utilisation
L'utilisation de base est simple. On commence par une fonction qui a le
prototype suivant :

```cpp
void benchmark_function_1(benchmark::State& state)
{
    for (auto _ : state) {
        // Code a mesurer
    }
}
```

Après, il suffit d'enregistrer la fonction en appelant la méthode
*RegisterBenchmark*, initialiser la librarie, puis de lancer l'exécution
avec un appel à *RunSpecifiedBenchmark*.

```cpp
int main(int argc, char* argv[])
{
  benchmark::RegisterBenchmark("benchmark_function_1", benchmark_function_1);
  benchmark::Initialize(&argc, argv);
  benchmark::RunSpecifiedBenchmarks();
}
```

Le screenshot ci-dessous montre le résultat d'exécution :

![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/google-benchmark-screenshot-01.png )

Les deux colonnes *Time* et *CPU* correspondent respectivement au temps
d'exécution moyen de la fonction et au temps d'exécution CPU moyen. La dernière
colonne montre le nombre d'exécution de la fonction à mesurer (le code à
  l'intérieur de la boucle `for (auto _ : state)`).

Par défaut, c'est la bibliothèque qui détermine le nombre d'itération. La règle utilisée (pour la version testée) est de faire un nombre d'itération
qui respecte les deux conditions suivantes :
- Pas plus d'un milliard d'itérations.
- Le temps d'exécution CPU total dépasse le paramètre
`benchmark_min_time` (il est de 0.5 seconde par défaut) ou le temps
d'exécution total dépasse cinq fois le temps `benchmark_min_time`.

Dans les détails, la règle est un peu plus complexe. Le code suivant
(tiré du fichier `benchmark.cc`) montre la condition complète :

```cpp
      // Determine if this run should be reported; Either it has
      // run for a sufficient amount of time or because an error was reported.
      const bool should_report =  repetition_num > 0
        || has_explicit_iteration_count  // An exact iteration count was requested
        || results.has_error_
        || iters >= kMaxIterations  // No chance to try again, we hit the limit.
        || seconds >= min_time  // the elapsed time is large enough
        // CPU time is specified but the elapsed real time greatly exceeds the
        // minimum time. Note that user provided timers are except from this
        // sanity check.
        || ((results.real_time_used >= 5 * min_time) && !b.use_manual_time);
```

Prenons par exemple ces deux fonctions :

```cpp
int inc(const int x) { return x + 1; }
int inc_and_wait(const int x) {
  std::this_thread::sleep_for(3s);
  return x + 1;
}
```

Le résultat du benchmarking est le suivant :
![Benchrmark - Deuxième test]({{ site.url }}{{ site.baseurl }}/assets/images/google-benchmark-screenshot-02.png )

La première a été exécutée jusqu'à ce que le temps CPU consommé dépasse
0.5 seconde (43801038 x 15 ns), alors que la seconde s'est exécutée une
fois car le temps global d'exécution a dépassé 2.5 secondes (3 secondes).

Reprenons l'exemple `inc_and_wait` et modifions le temps d'attente de 3 à 2 secondes :
```cpp
int inc_and_wait(const int x) {
  std::this_thread::sleep_for(2s);
  return x + 1;
}
```

![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/google-benchmark-screenshot-03.png )

On remarque que le nombre d'itération n'est pas de 2 (2x2=4 > 2.5) mais
de dix. En effet, la bibliothèque utilise un facteur d'expansion de 10
pour les fonctions dont le temps d'exécution est inférieur à 10% du
`benchmark_min_time`.

Pour la fonction suivante, le nombre d'itérations sera de 1000 (avec un
  temps d'exécution global de 10s).

```cpp
int inc_and_wait(const int x) {
  std::this_thread::sleep_for(0.01s);
  return x + 1;
}
```

![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/google-benchmark-screenshot-04.png )

## Macros

La bibliothèque fournit quelques macros qui permettent d'enregistrer et d'exécuter des benchrmarks. La macro `BENCHMARK`
permet d'enregistrer la fonction et de donner automatiquement un
nom au benchmark.

```cpp
BENCHMARK(benchmark_function);
```
Et à la place de la fonction main, on peut utiliser la macro `BENCHMARK_MAIN`.
```cpp
BENCHMARK_MAIN();
```
## Génération de plusieurs benchmarks

Dans le cas où on veut effectuer le benchmarking d'une fonction plusieurs fois
avec des paramètres différents, la bibliothèque propose deux méthode de le faire :
- En faisant appel à la méthode `Arg(int)`. Le paramètre de cette dernière est
passé à l'objet `state` et peut être récupéré avec la méthode `state.range(0)`.
```
    bench->Arg(32)
```
- L'inconvénient de la méthode précédente est qu'elle ne génère qu'un seul
benchmark. Si on veut générer plusieurs benchmarks, il faut faire appel autant de
fois à la méthode `Arg`. Dans ces cas, on peut utiliser la méthode
`Range(start, end)` qui permet de générer des benchmarks ayant comme arguments
les entiers de `start` à `end` avec un facteur multiplicateur de 8. Par exemple,
l'appel suivant :
```
    bench->Range(1, 4096)
```
Va générer des benchmarks avec les arguments (`state.range(0)`) 1, 8, 64, 512,
4096.
On peut aussi modifier le facteur multiplicateur avec la méthode
`RangeMultiplier`.
```
    bench->RangeMultiplier(2)
```

Les différentes méthodes `Arg`, `RangeMultiplier` et `Range` retournent
l'objet `benchmark`. Ceci permet de faire appel à plusieurs méthodes dans la
même instruction. Par exemple, on peut définir 4 benchmarks avec `Arg` comme
ceci :
```cpp
   bench->Arg(5)->Arg(16)->Arg(27)->Arg(38)
```
Ou générer des benchmark sur l'intervalle [1, 4096] avec un facteur
multiplicateur de 2
```cpp
   bench->Range(1, 4096)->RangeMultiplier(2)
```

La valeur du paramètre de la fonction `Arg` ou les nombres générés par la
fonction `Range` peut être récupérée comme ceci :

```cpp
int sz = state.range(0);
```

## Passage de paramètres

Prenons la fonction suivante comme exemple :
```cpp
void benchmark_with_arguments(benchmark::State &state, const int x,
                              const string &s) {
  for (auto _ : state) {
  }
}
```
On peut passer des paramètres de deux manières différentes syntaxiquement (mais
  équivalentes).

Avec la `RegisterBenchmark`, il suffit d'ajouter les paramètres dans l'appel :
```cpp
benchmark::RegisterBenchmark("benchmark_with_arguments",
                             benchmark_with_arguments, 1, std::string("foo"));
```

On peut aussi utiliser la macro `BENCHMARK_CAPTURE` pour enregister le
benchmark et lui passer des paramètres.
```cpp
BENCHMARK_CAPTURE(benchmark_with_arguments, "benchmark_with_arguments", 1,    
                                    std::string("foo"));
```

## Complexité
La bibliothèque permet aussi de mesurer la complexité *O(n)*. Généralement,
cette complexité est calculé en fonction d'un paramètre passé avec la méthode
`Range`. Pour la mesurer il faut faire appel à la méthode `state.SetComplexityN(...);`. Dans l'exemple suivant, nous allons mesurer la
complexité d'insertion dans un `vector` et une `map`.

```cpp
void benchmark_insert_vector(benchmark::State &state) {
  int sz = state.range(0);
  for (auto _ : state) {
    vector<int> v;
    for (int i = 0; i < sz; ++i)
      v.push_back(i);
  }
  state.SetComplexityN(state.range(0));
}

void benchmark_insert_map(benchmark::State &state) {
  int sz = state.range(0);
  for (auto _ : state) {
    map<int, int> m;
    for (int i = 0; i < sz; ++i)
      m[i] = i + 1;
  }
  state.SetComplexityN(state.range(0));
}
```

Pour pouvoir mesurer la complexité, il faut fournir au moins deux benchmarks.
Nous allons utiliser la méthode `Range` pour définir un ensemble de benchmarks.
Le calcul de la complexité est activé en appelant la méthode `Complexity`.

```cpp
BENCHMARK(benchmark_insert_vector)
    ->RangeMultiplier(2)
    ->Range(1 << 10, 1 << 11)
    ->Complexity();

BENCHMARK(benchmark_insert_map)
    ->RangeMultiplier(2)
    ->Range(1 << 10, 1 << 11)
    ->Complexity();
```
Le résultat est illustré dans le screenshot ci-dessous:
![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/google-benchmark-screenshot-05.png )
