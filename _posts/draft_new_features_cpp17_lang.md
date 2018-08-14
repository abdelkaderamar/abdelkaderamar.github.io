---
layout: single
title:  "C++17 : Résumé des nouveautés du langage"
date:   2000-07-22 16:00:00 +0100
categories:
  - Posts
tags:
  - C++, C++17
---

{% include toc %}

Ce post est similaire à celui déjà posté sur le [C++14](https://abdelkaderamar.github.io/posts/2018/07/19/cpp14_language_new_features.html)
mais concerne comme le titre l'indique les nouveautés de la norme C++17 pour le
langage et non la STL qui sera traité dans un autre article. Les exemples
sont disponibles dans ce [repository](https://github.com/abdelkaderamar/cpp-samples/tree/master/src/c%2B%2B17).

J'ai également réalisé une cheatsheet qui peut être télécharger ci-dessous :

![C++17 Language Cheatsheet]({{ site.url }}{{ site.baseurl }}/assets/images/cheatsheets/c++17_lang_cheatsheet.png )  
**Download**  
[PDF]({{ site.url }}{{ site.baseurl }}/assets/pdf/cheatsheets/c++17_lang_cheatsheet.pdf) (A4) |
[Latex](https://github.com/abdelkaderamar/cheatsheets/blob/master/cpp/c%2B%2B17_lang_cheatsheet.tex)

# Déduction des arguments des templates de classe
Avant le C++17, la déduction des types des templates était possible uniquement
pour les fonctions, mais pas pour les classes. Par exemple pour instancier un
objet `pair<int, double>`, il fallait expliciter les types
`pair<int, double>(1, 2.0)` ou passer par des fonctions utilitaires
(comme `make_pair`) qui utilise la déduction de paramètres pour les fonctions.
Il est maintenant possible de déduire le type à partir des paramètres du
constructeur (par exemple `pair(1, 2)`).

```cpp
pair p1{1, 2.0};
// before c++17
pair<int, double> p1{1, 2.0};
auto p2 = make_pair(1, 2.0);

// with c++17
pair p3{1, 2.0};
```

# Fold expressions

Les *Fold expressions* permettrent d'écrire un code plus compact avec les
*variadic templates* sans devoir utiliser une récursivité explicite.  
Par exemple pour écrire une fonction `sum` avant le C++17 :

```cpp
// before c++17
auto sum() {
  return 0;
}

template<typename T, typename ... Ts>
auto sum(const T& t, const Ts& ... ts) {
  return t + sum(ts ... );
}
```
Avec les *fold expressions*, l'écriture d'une telle fonction est plus simple :

```cpp
// with c++17
template<typename ... Ts>
auto sum_fold_exp(const Ts& ... ts) {
  return (3 + ... + ts);
}
```

# Déclarer les paramètres des templates avec `auto`

```cpp
```

# Nouvelles règles de déduction pour l'initialisation par {}

```cpp
```

# constexpr lambda

```cpp
```

# Constantes UTF-8

```cpp
char c1 = u8'x';
```

# Capture de `this` par valeur dans les lambda

```cpp
```

# Variable inline

```cpp
struct S { int x; };
inline S x1 = S{321};
```

# Namespaces imbriqués
L'écriture des namespaces imbriqués devait déclarer chaque namespace
séparément. Le résultat était parfois pas très élégant, en particulier pour les
*forward declaration*.

```cpp
// Before c++17
namespace A
{
  namespace
  {
    namespace C
    {
      class foo;
    }
  }
}
```
L'écriture du code précédent peut se faire plus simplement comme ci-dessous :
```cpp
namespace A::B::C {
  class foo;
}```

# Structured bindings

```cpp
template<typename T>
pair<T, bool> racine(T d) {
  if (d<0) return pair(-1, false);
  return pair(sqrt(d), true);
}

int main(int argc, char *agrv[])
{
  auto [s, success] = racine(1998.0);
  if (success) cout << s << endl;
}
```

# Déclaration et initialisation dans les conditions `if` et `switch`

```cpp
map<int, int> m;
for (int i=0; i<10; ++i) m[i] = i+(i/2);

auto insert = [&](int key, int value) {
  if (auto res = m.insert({key, value}); res.second) {
    cout << key << "/" << value << " inserted" << endl;
  }
};
```

# Suppression des trigraphes

```cpp
```

# constexpr if

```cpp
struct foo {
  void bar() { cout << "calling bar" << endl; }
};

template <typename T> int compute(T x) {
  if constexpr (std::is_integral<T>::value) {
    return x * x;
  } else if constexpr (std::is_same<T, string>::value) {
    return x.size();
  } else if constexpr (std::is_base_of<foo, T>::value) {
    x.bar();
    return 0;
  }
  return 0;
}
int main(int argc, char *agrv[]) {
  cout << compute(5) << endl;
  cout << compute(string{"constexpr if"}) << endl;
  struct foo f;
  compute(f);
}
```

# Constantes hexadécimale en virgule-flottante

```cpp
cout << 0x10.1p0 << endl // 16.0625
  << 0X0.8p0 << endl     // 0.5
  << 0X50.8p5 << endl;   // 2576
```

# Initialisation directe des enums

```cpp
enum class color : char { red, blue, green };

color c1 { 3 }, c2 { 88 };
```

# [[fallthrough]]

L'attribut `fallthrough` peut être utilisé dans les instructions `switch` pour
supprimer le message d'avertissement lorsque deux `case` se suivent sans
instruction `break` entre les deux. Dans l'exemple suivant, le compilateur
affichera un message d'erreur pour le `case 2`, alors qu'il ignorera le
`case 3`.

```cpp
  int i;
  cin >> i;
  switch (i) {
  case 1:
    cout << "one" << endl;
  case 2:
    cout << "two" << endl;
  [[fallthrough]];
  case 3 : cout << "three" << endl;
  }
```

**Remarque** : sous *gcc* activer l'option `-Wimplicit-fallthrough` ou `-Wextra`.

# [[nodiscard]]
L'attribut `nodiscard` permet d'avoir un message d'avertissement du compilateur
si la valeur retourné par une fonction n'est pas utilisée.

```cpp
[[nodiscard]] int foo() { return 1; };
void bar() {
  foo(); // Warning
}
```

On peut également marquer un type avec l'attribut `nodiscard`. Dans ce cas, le
message d'avertissement sera affiché pour toutes les fonctions qui retournent
ce type.

```cpp
```


# [[maybe_unused]]
L'attribut `maybe_unused` permet de supprimer le message d'avertissement du
compilateur si la fonction ou la variable n'est pas initialisé.

```cpp
static void f() {  } // Compilers may warn about this
[[maybe_unused]] static void g() {  } // Warning suppressed

int x = 42;
[[maybe_unused]] int y = 42; // Warning suppressed
```

# static_assert sans message

Le mot clé `static_assert` peut être utilisé maintenant sans avoir à spécifier
un message d'erreur.

```cpp
static_assert(VERSION >= 2);
```
