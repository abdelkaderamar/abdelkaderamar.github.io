---
layout: single
title:  "C++14 : Résumé des nouveautés du langage"
date:   2000-07-13 16:00:00 +0100
categories:
  - blog
tags:
  - C++, C++14
---

{% include toc %}

# `auto f(...)` : type de retour de fonction auto
Il est possible avec la norme C++14 de déclarer des fonctions avec un type de
retour `auto`. Ceci est rendu possible aussi pour les fonctions lambda.

```cpp
```

# Contrainte sur les fonctions constexpr
Avec le C++11, il était possible de déclarer une fonction *constexpr* à
condition qu'elle ne contienne qu'une seule expression. Cette contrainte est
assouplie avec le C++14.

```cpp
```

# Variable template
Jusqu'au C++14, seule les fonctions et les classes peuvent être templatées.
Maintenant il est possible de déclarer des variables de type template.

```cpp
```

# Initialisation regroupée de membres
Avec le C++11, les classes possédant une Initialisation de membre ne pouvait
pas être initialisée en utilisant l'initialisation groupée.
Le C++14 supprime cette contrainte et permet d'utiliser l'initialisation groupée
même pour ces classes.

```cpp
```
