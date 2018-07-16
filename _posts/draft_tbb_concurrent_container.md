---
layout: single
title:  "Intel Threading Building Blocks : Les Conteneurs Concurrents"
date:   2018-07-01 16:00:00 +0100
categories:
  - blog
tags:
  - C++
  -
---

{% include toc %}

# Introduction
La bibliothèque *Intel Threading Building Blocks* connue sous le nom de *TBB*
est une bibliothèque C++ développée par Intel pour la programmation parallèle
sur des architectures multi-processeurs ou multi-coeurs.

Parmi les composantes de cette bibliothèque, on trouve des conteneurs
*thread-safe*, des algorithmes parallèles, des mécanismes de programmation
par tâches ou graphes de tâches ainsi que des mécanismes d'ordonnancement et
de synchronisation.

# Installation
Sur la page [Github](https://github.com/01org/tbb/releases), on trouve les
versions compilées pour les architectures suivantes : linux, MacOS, Android et
Windows. Le package linux contient les versions 32 et 64 bits compilées avec
différents gcc (le plus récent est le gcc 4.7).
Le code source est également disponible. On remarque que le projet ne contient
qu'un simple *Makefile* sans règle pour installer la librairie.
La compilation génère des fichiers de configuration contenants des variables
d'environnement (*CPATH*, *LD_LIBRARY_PATH* et *LIBRARY_PATH*) qui peuvent être
utiles pour la compilation ou l'exécution de programme utilisant la librairie.

De mon côté j'ai opté pour une installation manuelle :
- copier le répertoire *include* dans le répertoire d'installation *prefix* (`/opt`,
  `/usr/local` ou `$HOME/.local`)
- copier les bibliothèques générés dans les répertoires
`build/linux_intel64_gcc_cc7_libc2.27_kernel4.15.0_...` vers le repertoire
`prefix/lib`.

# Conteneurs Thread-Safe
La bibliothèques fournit plusieurs types de conteneurs thread-safe. Ces
conteneurs ressemblent à ceux de la STL :
1. concurrent_vector
2. unordered_set
- unordered_map
- concurrent_queue
- lru_cache
- priority_queue
- hash_map

## Utilisation

## Performance
