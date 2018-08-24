---
categories:
- Tutorials
- Posts
classes: wide
date: 2018-06-13T23:48:00Z
'tags:':
- C++
- C+17
title: '*C++17 : Fold Expressions*'
---

Le C++ a introduit dans la norme C++11 les *variadic templates* qui permettent
d'écrire des fonctions templates avec un nombre variable de paramètres. Leur
utilisation passait par l'écriture d'une fonction récursive. Par exemple pour
écrire une fonction qui calcule la somme d'un nombre variable de paramètres,
on pouvait faire ceci :

```cpp
auto sum() {
  return 0;
}

template<typename T, typename ... Ts>
auto sum(const T& t, const Ts& ... ts) {
  return t + sum(ts ... );
}
```

Avec la nouvelle norme C++17, l'écriture de telles fonctions devient plus
simple avec les *fold expressions*. Les appels récursifs sont remplacés
par une expressions contenant les variables et l'opérateur appliqué.  
La fonction précédente peut être écrite comme la fonction suivante :

```cpp
template<typename ... Ts>
auto sum_fold_exp(const Ts& ... ts) {
  return (ts + ...);
}
```

La *fold expression* est la suivante : `(ts + ...)` et elle peut être
interprétée comme l'expression `pack op ...` où on a :
- `ts` est pack
- `+` est `op`
- `...` pour l'expansion de l'expression.

Donc l'expression `ts + ...` sera interprété comme l'expression
`t1 + t2 + ... + tn`

A noter que les parenthèse sont nécessaires autour de l'expression.

```cpp
(ts + ...); // Ok
ts + ...; // syntax error
```


Le tableau suivant décrit les différentes *fold expression* et leur expansion.

| Fold expression        | Description                                     |
|------------------------|-------------------------------------------------|
| pack op ...            | pack1 op (... op (packN-1 op packN))            |
| ... op pack            | ((pack1 op pack2) op ...) op packN              |
| init op ... op pack    | (((init op pack1) op pack2) op ...) op packN    |
| pack op ... op init    | pack1 op (... op (packN-1 op (packN op init)))  |

Prenons un second exemple d'une fonction qui affiche un nombre variable de
paramètres dans la sortie standard. Cette fonction peut s'écrire comme
ci-dessous en utilisant les *variadic templates* :

```cpp
auto print() {}

template <typename T, typename ... Ts>
auto print(const T& t, const Ts& ... ts) {
  cout << t << " ", print(ts ...);
}
```

En utilisant les *fold expressions*, nous pouvons l'écrire comme suit :
```cpp
template<typename ... Ts>
auto print_fold(const Ts& ... ts)
{
  ((cout << ts << " "), ... );
}
```

Cette fois-ci le *pack expression* n'est pas seulement l'argument `ts`, mais
l'expression `cout < ts << " "`. L'opérateur est `,` et l'expression sera
transformé en
```cpp
((cout << t0 << " "), ((cout << t1 << " "), .... ((cout << tn << " "))))
```

Par exemple, l'appel `print_fold(1, 3, 5)` sera transformé en
```cpp
((cout << 1 << " "), ((cout << 3 << " "), ((cout << 5 << " "))))
```
