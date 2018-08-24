---
categories:
- Posts
date: 2018-08-21T10:00:00Z
tags:
- C++, C++17
title: 'C++17 : Résumé des nouveautés du langage (+Cheatsheet)'
---

{% include toc %}

Ce post est similaire à celui déjà posté sur le [C++14](https://abdelkaderamar.github.io/posts/2018/07/19/cpp14_language_new_features.html)
mais concerne comme le titre l'indique les nouveautés de la norme C++17 pour le
langage (et non la STL qui sera traité dans un autre article). Les exemples
sont disponibles dans ce [repository](https://github.com/abdelkaderamar/cpp-samples/tree/master/src/c%2B%2B17).

J'ai également réalisé une cheatsheet qui peut être téléchargéé ci-dessous :

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

Plus de détails sur cette fonctionnalité sont disponibles dans ce
[post](https://abdelkaderamar.github.io/tutorials/posts/2018/06/13/fold_expression.html).

# Déclarer les paramètres des templates (*template non-type arguments*) avec `auto`

Il est possible maintenant des déclarer les paramètres des templates (*template
non-type arguments*) avec le mot-clé `auto`. Avant cette fonctionnalité, pour
écrire une constante template :

```cpp
template <typename Type, Type value> constexpr Type constant = value;
constexpr auto const my_constant = constant<int, 42>;
```

Maintenant cela peut s'écrire :

```cpp
template <auto value> constexpr auto constant = value;
constexpr auto const my_constant = constant<42>;
```
Voici un autre exemple d'utilisation avec les *variadic template* :

```cpp
template <auto ... vs> struct heterogenous_list {};
using list = heterogenous_list<1, 2, 'A', 4>;
```
*Remarque* : le standard n'accepte pas les types en virgule-flottante (float,
  double) et les string pour les *"template non-type arguments"*.


# Nouvelles règles de déduction pour l'initialisation par {}

Les règles de déduction pour les `{}` avec auto ont été changées. Auparavant
`auto x{1}` déduisait un `x` de type `std::initializer_list<int>`, avec la
nouvelle norme, `x` est de type `int`.

```cpp
auto x1 {1};
static_assert(is_same<decltype(x1), int>::value == 1);

auto x2 = {1};
static_assert(is_same<decltype(x2), initializer_list<int>>::value == 1);

// auto x3 {1, 2, 3}; // syntax error
// gcc error message :
//    direct-list-initialization of ‘auto’ requires exactly one element

auto x4 = {1, 2, 3};
static_assert(is_same<decltype(x4), initializer_list<int>>::value == 1);
```

# constexpr lambda

Les expressions lambda peuvent être marquées avec `constexpr` pour permettre au
compilateur d'évaluer les appels à la compilation.

```cpp
auto identity = [](int n) constexpr { return n; };
static_assert(identity(123) == 123);
```

```cpp
constexpr auto inc(auto n) { return n + 1; }

// ...

static_assert(inc(1) == 2);
```

# Capture de `this` par valeur dans les lambda

La capture de `this` étaient jusqu'au C++17 par référence uniquement. Ce mode de
passage peut poser des problèmes dans certaines situations comme celles d'appel
de code asynchrone où la callback peut avoir besoin de l'objet appelant, même
après sa destruction éventuelle. Il est maintenant possible de faire une copie
de `this` en utilisant la syntaxe `[*this]`. L'exemple suivant n'utilise pas du
code asynchrone mais montre la copie de l'objet appelant.

```cpp
struct foo
{
  foo() : x{0} {}
  int _x;
  auto log_by_ref() {
    return [this]() { cout << x << endl; };
  }
  auto log_by_val() {
    return [*this]() { cout << x << endl; };
  }
};

struct foo f;
f._x = 1234;
auto ref = f.log_by_ref();
auto val = f.log_by_val();
ref();  // print 1234
val();  // print 1234
f.x = 4321;
ref();  // print 4321
val();  // print 1234, the copy of is not modified
```

<!-- *comment* -->

# Variable inline

Avec cette fonctionnalité, les variable peuvent être déclarées avec le mot-clé
*inline* comme pour les fonctions. Ceci peut s'avérer utile pour les
bibliothèques à base de fichiers entêtes seulement.  

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
Avec le C++17, l'écriture du code précédent peut se faire plus simplement comme
ci-dessous :

```cpp
namespace A::B::C {
  class foo;
}
```

# Structured bindings

Avec cette fonctionnalité, il est possible d'écrire des expressions de type
`auto [x, y, z] = expr` où le type de `expr` est un type *tuple like* (`pair`,
`tuple`, `array` ou structure)

**Example avec `pair`**
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
**Example avec `tuple`**
```cpp
tuple<int, int, int> make_random_tuple()
{
  return tuple(rand(), rand(), rand());
}

//...

auto [a, b, c] = make_random_tuple();
```

**Example avec une structure**
```cpp
struct foo {
  int i;
  double d;
  char c;
};

foo make_foo() {
  foo f{rand(), rand(), 32 + rand() % 128};
  return f;
}

//...

foo f = make_foo();
auto [i, d, c] = f;
cout << "i = " << i << endl << "d = " << d << endl << "c = " << c << endl;
```

**Example avec `array`**
```cpp
array<int, 4> make_random_array() {
  return array{rand(), rand(), rand(), rand()};
}

// ...

auto [i0, i1, i2, i3] = make_random_array();
cout << "i0 = " << i0 << endl;
```


# Déclaration et initialisation dans les conditions `if` et `switch`

Pour réduire le scope des variables, il maintenant possible de les déclarer
à l'intérieur de la condition du `if` ou du `switch`.

**if**
```cpp
map<int, int> m;

// ...

auto insert = [&](int key, int value) {
  if (auto res = m.insert({key, value}); res.second) {
    cout << key << "/" << value << " inserted" << endl;
  }
};
```

**switch**
```cpp
enum class color : char { red, blue, green };

//...

switch (auto c = get_color()) {
case color::red:
  cout << "red" << endl;
  break;
case color::blue:
  cout << "blue" << endl;
  break;
case color::green:
  cout << "green" << endl;
  break;
default:
  cout << "unknown color" << endl;
  break;
}
```

# Suppression des trigraphes

Les trigraphes sont un héritage des anciens systèmes qui ne supportaient pas
l'ASCII 7 bits. Ils consistent en une séquence de caractères qui sont
transformés par le préprocesseur du compilateur en un autre caractère. Par
exemple `??/` sont transformés en `\` et `??<` en `{`

# constexpr if

Cette nouvelle fonctionnalité est très intéressante car elle permet au
compilateur d'interpréter le résultat de la condition d'un `if` et de ne
garder que la partie qui satisfait la condition. Dit autrement, cette
fonctionnalité permet d'avoir un `if` statique.

Avec cette fonctionalité, il n'est plus nécessaire de passer par le mécanisme
de *SFINAE* (ou même dans certains cas par des *#ifdef*).

A noter que la syntaxe est la suivante (les parenthèses sont autour de la
condition seulement):

```cpp
if constrexpr (cond)
  statement
else
  statement
```

Dans l'exemple ci-dessous, la fonction *template* `compute` est générée
différemment en fonction du type fourni. Si c'est un type entier qui est
utilisé, le compilateur gardera l'instruction `x * x`, et supprimera les deux
autres branches. Si c'est le type `foo` ou un type dérivé de `foo` qui est
utilisé, les deux premières branches sont supprimées et c'est les instructions
`x.bar(); return 0;` qui seront gardées.

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

Les constantes en virgule flottante peuvent être définies avec la syntaxe
suivante :

```cpp
0x<hex digit sequence><exponent><suffix>
0x<hex digit sequence>.<exponent><suffix>
0x<hex digit sequence>.<hex digit sequence><exponent><suffix>
```
Avec *exponent* qui a la syntaxe suivante :
```cpp
p|P<exponent sign><digit sequence>
```
Par exemple, si on convertit en décimal la constante `0x50.8p5` :
```cpp
0x50.8p5 = (5*16 + 0 + 0.5) * 2^5 = 80.5 * 32 = 2576
```


```cpp
cout << 0x10.1p0 << endl // 16.0625
  << 0X0.8p0 << endl     // 0.5
  << 0X50.8p5 << endl;   // 2576
```

# Initialisation directe des enums

Les *enums* de type *class* peuvent être initialisés avec des entiers
directement en utilisant les accolades `{}`

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
si la valeur retournée par une fonction n'est pas utilisée.

```cpp
[[nodiscard]] int foo() { return 1; };
void bar() {
  foo(); // Warning
}
```

On peut également marquer un type avec l'attribut `nodiscard`. Dans ce cas, le
message d'avertissement sera affiché pour toutes les fonctions qui retournent
ce type.


# [[maybe_unused]]
L'attribut `maybe_unused` permet de supprimer le message d'avertissement du
compilateur si la fonction ou la variable n'est pas utilisée.

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

# Constantes UTF-8
Les constantes UTF-8 de type `char` commence par le préfixe `u8`.

```cpp
char c1 = u8'x';
```
