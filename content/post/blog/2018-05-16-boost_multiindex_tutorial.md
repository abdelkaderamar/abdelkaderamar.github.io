---
categories:
- Tutorials
- Posts
classes: wide
date: 2018-05-16T21:30:00Z
'tags:':
- C++
- Boost
title: Utilisation de *Boost Multi-index*
---

{% include toc %}

# Introduction
[Boost Multi-Index](http://www.boost.org/libs/multi_index) est une librairie
qui fournit un type de conteneur de données appelé `multi_index_container`.
La particularité de ce type est de fournir un ou plusieurs index permettant
ainsi plusieurs méthodes d'accès dans le même conteneur.
Par exemple, on peut indexer des données en définissant deux clés distinctes.
Avec les conteneurs STL, il faut utiliser deux `map`, une pour chaque clé et
s'assurer que les deux conteneurs sont mis à jours simultanément.

Avec `multi_index_container`, on peut aussi avoir des accès de type aléatoire (
comme dans `vector`), séquentiel (comme dans `list`) ou par hachage (comme
dans `unordered_map`)

# Les différents type d'index

Commençons par utiliser un seul index. L’intérêt dans ce cas est limité, mais
l'objectif est de voir les différents types d'accès que propose cette librairie.

La syntaxe générale du type `multi_index_container` est la suivante

```cpp
multi_index_container<
    TYPE,
    indexed_by <
      {INDEX(ES)}
    >
  >
```

Où :
- `TYPE` est le type de données manipulé par le conteneur.
- `{INDEX(ES)}` est un ou plusieurs index.

Dans les exemples qui vont suivre, nous allons utiliser le type *stock* dont la
définition est la suivante :
```cpp
class stock {
public:
  std::string _isin;
  std::string _cusip;
  std::string _ric;
  std::string _mic;

  bool operator<(const stock &s) const { return _isin < s._isin; }

  const std::string key() const { return _cusip + "/" + _mic; }
};
```
[comment]: __

## Accès aléatoire
L'index `random_access` permet de proposer un accès aléatoire au conteneur. En
d'autres termes, il permet de transformer le contenur `multi_index_container` en
`vector`. Voici un exemple d'utilisation :

```cpp
typedef multi_index_container<stock, indexed_by<sequenced<>>>
    stock_container_t;
stock_container_t container{generate_stock(), generate_stock(),
                            generate_stock()};
stock_container_t;
cout << "Container size = " << container.size() << endl;
```

## Accès séquentiel
L'index `sequenced` offre un accès séquentiel au conteneur. C'est l'équivalent
de l'accès proposé par le conteneur `list` de la *STL*. Voici un exemple
d'utilisation :

```cpp
typedef multi_index_container<stock, indexed_by<sequenced<>>>
    stock_container_t;
stock_container_t container{generate_stock(), generate_stock(),
                            generate_stock()};
stock st_gobain{"FR0000125007", "undefined", "SGOB.PA", "XPAR"};
container.push_back(st_gobain);
cout << "Container size = " << container.size() << endl;
```

## Conteneur trié
Pour définir des types de conteneurs triés,la bibliothèque propose deux types
d'index selon que les éléments sont uniques ou pas. Si on veut des éléments
uniques, c'est l'index `ordered_unique` qu'il faut utiliser. Dans le cas
contraire, c'est l'index `ordered_non_unique`.

Pour le critère de tri, l'API propose plusieurs méthodes utilitaires selon les
besoins :
1. **Tri selon les éléments stockés :** si on veut que les éléments soient triés (
  dans ce cas, le type d'élément doit avoir l'opérateur `<` défini), on utilise
  la méthode utilitaire `member`. Voici un exemple d'utilisation où on obtient
  l'équivalent d'un `set` de la *STL*.
```cpp
ordered_unique<identity<stock>>
```
Dans l'exemple suivante, c'est l'équivalent du conteneur `multi_set` de la STL.
```cpp
ordered_non_unique<identity<stock>>
```
La définition complète est :
```cpp
typedef multi_index_container<stock,
    indexed_by<ordered_non_unique<identity<stock>>>
  >  stock_container_non_unique_t;
```

2. **Tri selon un attribut :** pour trier les éléments selon un attribut du type
d'élément stocké, on peut utiliser la fonction utilitaire `member`. La syntaxe
est la suivante:
```cpp
member< ELEMENT_TYPE, ATTRIBUTE_TYPE, &ELEMENT_TYPE::ATTRIBUTE_TYPE>
```
Par exemple, pour trier les éléments selon l'attribut `_isin`
```cpp
ordered_non_unique<member<stock, string, &stock::_isin>>
```
La définition complète
```cpp
typedef multi_index_container<
    stock,
    indexed_by<ordered_non_unique<member<stock, string, &stock::_isin>>>>
    stock_container_t;
```

3.  **Tri selon une fonction membre :** au lieu d'utiliser un attribut, on peut
utiliser une fonction qui retourne une valeur qui déterminera le tri. Ceci
s'avère utile si l'attribut du tri est protégé ou si la valeur du tri est le
résultat d'un calcul. Pour y parvenir, on utilise la fonction `mem_fun` ( ou
  `const_mem_fun` si la fonction est *const*). La syntaxe est la suivante :
```cpp
mem_fun<ELEMENT_TYPE, FUNCTION_RETURN_TYPE, &ELEMENT_TYPE::FUNCTION_NAME>
```
ou
```cpp
const_mem_fun<ELEMENT_TYPE, FUNCTION_RETURN_TYPE, &ELEMENT_TYPE::FUNCTION_NAME>
```
Par exemple :
```cpp
ordered_non_unique<const_mem_fun<stock, const string&, &stock::key>>
```
La définition complète :
```cpp
typedef
multi_index_container<
    stock,
    indexed_by<ordered_non_unique<
      const_mem_fun<stock, const string, &stock::key>>
    >
  > stock_container_t;
```

3. **Accès par hachage :** De la même manière que pour les index triés, la
bibliothèque propose des index de hachage avec les types `hashed_unique` et
`hashed_non_unique`
```cpp
typedef multi_index_container<
    stock,
    indexed_by<hashed_non_unique<member<stock, string, &stock::_isin>>>>
    stock_container_t;
stock_container_t container{generate_stock(), generate_stock(),
                            generate_stock()};
copy(container.begin(), container.end(), ostream_iterator<stock>(cout, "\n"));
```


# Utilisation de plusieurs index

L'utilisation de plusieurs index dans le même conteneur se fait simplement en
définissant les différents index dans la partie `indexed_by`. Voici comment
définir un conteneur qui propose les accès suivants :
- Accès aléatoire.
- Triés sur les éléments (uniques).
- Tri sur l'attribut `_isin`.

```cpp
typedef multi_index_container<
    stock,
    indexed_by<
      random_access<>,
      ordered_unique<identity<stock>>,
      ordered_non_unique<member<stock, string, &stock::_isin>>
    >> stock_container_t;
```

# Lecture
L'accès aux éléments se fait par l'intermédiaire du conteneur ou par l'index
qu'on veut utiliser.

Pour récupérer un index d'un conteneur `multi_index_container`, la syntaxe est
la suivante :

```cpp
CONTAINER_TYPE::nth_index<RANK>::type &VAR = CONTAINER.get<RANK>();
```
Par exemple pour obtenir les index du `stock_container` défini précédemment,
on utilise ceci :
```cpp
stock_container_t::nth_index<0>::type &random_index = container.get<0>();
stock_container_t::nth_index<1>::type &identity_index = container.get<1>();
stock_container_t::nth_index<2>::type &isin_index = container.get<2>();
```
A partir de là, on peut accéder au premier élément
```cpp
random_index[0]
```
Ou accéder à la liste triée des éléments :
```cpp
for (auto &s : identity_index)
```
Ou accéder à la liste triée des éléments selon l'attribut `_isin` :
```cpp
for (auto &s : isin_index)
```

On peut aussi accéder au éléments via le conteneur, mais dans ce cas les
méthodes disponibles sont seulement celles du premier index défini. Dans
l'exemple précédent, le type `stock_container` propose les méthodes de
l'index `ordered_unique`. On peut donc utiliser la variable `container` sans
passer par l'index `identity_index`
```cpp
container.begin()
```

# Mise à jour
La mise à jour du conteneur peut s'effectuer de deux manières :

1. La méthode *replace* : à partir d'un itérateur sur l'élément à modifier, on
peut mettre à jour le conteneur comme ceci :
```cpp
auto it = container.begin();
stock st_gobain = *it;
st_gobain._ric = "SGOB.PA";
container.replace(it, st_gobain);
```
2. Utilisation d'un functor ou d'une fonction avec la méthode *modify*
  - functor
```cpp
struct change_ric {
        change_ric(const string &ric) : _new_ric(ric) {}
        void operator()(stock &s) { s._ric = _new_ric; }
private:
        string _new_ric;
};
container.modify(it, change_ric{"BNPP.PA"});
```
  - fonction
```cpp
  auto upd_func = [](stock &s) { s._ric = "TOTF.PA"; };
  container.modify(it, upd_func);
```

[comment]: __

# Suppression
La suppression des éléments se fait via la méthode `erase` avec comme paramètre
l'itérateur vers l'élément à supprimer. Voici un exemple dans lequel on supprime
le premier élément.

```cpp
typedef multi_index_container<
    stock,
    indexed_by<random_access<>,
               ordered_non_unique<member<stock, string, &stock::_ric>>>>
    stock_container_t;
stock_container_t container{
  {"FR0000120271", "undefined", "TOTF.PA", "XPAR"},
                            {"undefined", "undefined", "undefined", "undefined"},
                            {"FR0000127771", "undefined", "undefined", "XPAR"},
                            {"FR0000045072", "undefined", "undefined", "XPAR"},
                            {"undefined", "undefined", "undefined", "XPAR"}};
stock_container_t::nth_index<0>::type &random_index = container.get<0>();
stock_container_t::nth_index<1>::type &ric_index = container.get<1>();

auto it = identity_index.begin();
identity_index.erase(it);
```

Dans ce qui suit, nous utilisons les méthodes `lower_bound` et `upper_bound`
(proposées par le type `ordered_non_unique`) pour trouver une plage d'éléments
à supprimer. La méthode `lower_bound` permet de trouver le premier élément
donc la clé est égale au paramètre de la fonction. La méthode `upper_bound`
retourne l'élément suivant le dernier élément. Par exemple,
`ric_index.upper_bound("undefined")` retourne le *stock* suivant le dernier
dont le *ric* est égal à *"undefined"*

```cpp
auto it_begin = ric_index.lower_bound("undefined");
auto it_end = ric_index.upper_bound("undefined");
ric_index.erase(it_begin, it_end);
cout << "Size after 2nd erase " << container.size() << endl;
copy(ric_index.begin(), ric_index.end(), ostream_iterator<stock>(cout, "\n"));
```

# Liens
[Boost Multi-Index](http://www.boost.org/libs/multi_index)
