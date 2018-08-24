---
categories:
- Posts
date: 2018-07-19T17:15:00Z
tags:
- C++, C++14
title: 'C++14 : Résumé des nouveautés du langage (+Cheatsheet)'
---

{% include toc %}

La norme C++14 qui a été standardisée il y a déjà quatre ans, est
considérée comme mineure si on la compare au C++11 et le C++17. Dans ce post,
je vais décrire brièvement les changements apportés au langage (mais pas la
  STL). Des programmes exemples son disponible dans ce
  [projet](https://github.com/abdelkaderamar/cpp-samples/tree/master/src/c%2B%2B14).

J'ai également réalisé une cheatsheet qui peut être télécharger ci-dessous :

![C++14 Language Cheatsheet]({{ site.url }}{{ site.baseurl }}/assets/images/cheatsheets/c++14_lang_cheatsheet.png )  
**Download**  
[PDF]({{ site.url }}{{ site.baseurl }}/assets/pdf/cheatsheets/c++14_lang_cheatsheet.pdf) (A4) |
[Latex](https://github.com/abdelkaderamar/cheatsheets/blob/master/cpp/c%2B%2B14_lang_cheatsheet.tex)

# `auto f(...)` : type de retour de fonction `auto`
Il est possible avec la norme C++14 de déclarer des fonctions avec un type de
retour `auto`. Ceci est rendu possible aussi pour les fonctions lambda.

```cpp
auto f_cpp14() {
  return 1;
}

auto f_cpp11() -> int {
  return 1;
}
```

# Contrainte sur les fonctions constexpr
Avec le C++11, il était possible de déclarer une fonction *constexpr* à
condition qu'elle ne contienne qu'une seule expression. Cette contrainte est
assouplie avec le C++14.

```cpp
constexpr int f_cpp14(int x) {
  if (x % 2 == 0)
    return x * 10;
  return x;
}
```

# Variable template
Jusqu'au C++14, seule les fonctions et les classes peuvent être templatées.
Maintenant il est possible de déclarer des variables de type template.

```cpp
template<typename T>
constexpr T pi = T(3.141592653589793238462643383);

template<>
constexpr const char* pi<const char*> = "pi";

cout.precision(numeric_limits< long double >::max_digits10);

cout << pi<long double> << endl;
cout << pi<double> << endl;
cout << pi<float> << endl;

cout << pi<const char*> << endl;
```

# Initialisation regroupée de membres
Avec le C++11, les classes possédant une Initialisation de membre ne pouvait
pas être initialisée en utilisant l'initialisation groupée.
Le C++14 supprime cette contrainte et permet d'utiliser l'initialisation groupée
même pour ces classes.

```cpp
struct foo_2 {
  int x{10}, y, z;
};
struct foo_2 f2 { 1, 2 };  // error with c++11

struct foo_3 {
  int x{1}, y{2}, z{3};
};
struct foo_3 f3_a { 1, 2 }; // error with c++11

```

# Lambda générique
Les paramètres d'une lambda peuvent être déclarés avec le type `auto`.

```cpp
auto lambda = [](auto x, auto y) { return x + y; };

cout << lambda(1, 2) << endl;
cout << lambda(1.6, 2.5) << endl;
string s1{"1"}, s2{".5"};
cout << lambda(s1, s2) << endl;
```

# Littéraux binaires
Les nombres binaires peuvent être définis avec les préfixes `0b` ou `0B`.

```cpp
short i = 0b0101010101010101;
short j = 0B1101010101010101;
```
# Les séparateurs de chiffres
Il est possible d'utiliser une apostrophe (*single quote*) comme séparateur de
chiffres pour améliorer la lisibilité des grands nombres. La position de ce
séparateur est libre

```cpp
int i = 1'928'229'292;
int j = 1928'2'292'92;
```

# L'attribut *deprecated*
L'attribut `deprecated` permet de marquer une fonction ou un attribut comme
obsolète. C'est à la compilation que l'avertissement est remonté. Un message
optionnel peut être défini qui s'ajoutera au message d'avertissement standard
du compilateur.

```cpp
[[deprecated]] void f() {};

[[deprecated("g will not be supported from next release")]] void g() {};

class foo
{
public:
  [[deprecated("x is not protected. Use getter instead")]]
  int x;
};
```

# Capture des variables dans une lambda
Le C++11 permettait à une lambda de capturer les valeurs des variables soit par
valeur soit par référence. Le C++14 améliore cette fonctionnalité en permettant
de déclarer de nouvelles variables initialisées par `move` ou avec une
expression quelconque.

```cpp
auto lambda_func_call = [value = f(argc)](int x) { return value * x; };

string s{"foo"};
auto lambda_move = [value = move(s)](int x) { return value + to_string(x); };
```

# Déduction de type `decltype(auto)`
La norme C++14 permet d'avoir la déclaration `decltype(auto)`. Cette
fonctionnalité peut être utile dans certains cas où la fonction doit transférer
le bon type (référence ou valeur) sans le transformer. En effet, `auto` déduit
toujours un type *non référence*, ce qui n'est pas le cas de `decltype`.
L'utilisation dans ce genre de situation de `decltype(auto)` permet de retourner
le type référence ou valeur selon l'expression utilisée.

Voici quelques exemples tirés du standard :

```cpp
int i;
int&& f();
auto x3a = i;                  // decltype(x3a) is int
decltype(auto) x3d = i;        // decltype(x3d) is int
auto x4a = (i);                // decltype(x4a) is int
decltype(auto) x4d = (i);      // decltype(x4d) is int&
auto x5a = f();                // decltype(x5a) is int
decltype(auto) x5d = f();      // decltype(x5d) is int&&
auto x6a = { 1, 2 };           // decltype(x6a) is std::initializer_list<int>
decltype(auto) x6d = { 1, 2 }; // error, { 1, 2 } is not an expression
auto *x7a = &i;                // decltype(x7a) is int*
decltype(auto)*x7d = &i;       // error, declared type is not plain decltype(auto)
```
