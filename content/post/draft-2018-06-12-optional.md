---
categories:
- Posts
date: 2018-06-12T16:00:00Z
tags:
- C++
title: std::optional
---

{% include toc.html %}

`std::optional` est une classe utilitaire qui permet de contenir un type et
d'indiquer si la valeur contenue a été initialisée ou non. Cette fonctionnalité,
appelée souvent *nullable types* peut être obtenue aussi en utilisant des
valeurs spéciales(-1, `nullptr`, chaine vide, ect.).
Ce type est déjà disponible dans d'autres langages comme *Java*, mais le type
`boost::optional` a été introduit dans la fameuse bibliothèque C++ bien avant (
  en 2003).


## Création
La création d'un objet `optional` est simple. La STL fournit la constante
`std::nullopt` qui n'est pas de type `optional` mais qui permet de réinitialiser
un objet de type `optional` ou d'en créer un vide.
Ceci est possible car le type `optional`possède un opérateur `=(nullopt_t)` qui
réinitialise l'objet.
```cpp
optional<int> o_empty1;
std::optional<string> o_empty2 = std::nullopt;
```

Considérons la classe suivante :
```cpp
class foo {
public:
  foo(int id, int n) : _id(id), _n(n) { cout << "ctor of " << _id << endl; }

  foo(const foo &f) : _id(f._id) { cout << "copy ctor of " << _id << endl; }

  const int id() const { return _id; }

protected:
  int _id, _n;
};
```
On peut créer des objets `optional` de plusieurs manières :
```cpp
foo f{1, 11};
auto o1{f};
optional<foo> o2{{2, 12}};
optional<foo> o3 = make_optional<foo>(3, 13);
optional<foo> o4{in_place, 4, 14};
```

Le constructeur d'un objet `optional` possède un tag `in_place` qui permet de
construire l'`optional` dans passer par la création d'un objet temporaire. La
méthode `make_optional` utilise aussi le même mécanisme et l'objet est créé
directement sans la création d'un objet temporaire.

## Lecture
Pour lire la valeur d'un `optional`, on dispose de trois méthodes :
- la méthode `value`
- la méthode `value_or(default_value)`
- l'opérateur `*` et `->`

## Mise à jour
La modification d'un objet `optional` se fait via la méthode `emplace`. Il y a
également la méthode `reset` qui réinitialise le contenu de l'objet `optional`,
c'est équivalent à affecter la valeur `nullopt`.
