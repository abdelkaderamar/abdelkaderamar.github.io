---
layout: single
title:  "Utilisation de *Boost Multi-index*"
date:   2018-05-16 12:10:11 +0100
categories:
  - Draft
  - C++
  - Boost
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

## Accès aléatoire


# Liens
[Boost Multi-Index](http://www.boost.org/libs/multi_index)
