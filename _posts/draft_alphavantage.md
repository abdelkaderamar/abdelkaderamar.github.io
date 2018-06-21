---
layout: single
title:  "Alphavantage"
date:   2018-06-12 16:00:00 +0100
categories:
  - Posts
tags:
  - C++
---

{% include toc %}

[AlphaVantage](https://alphavantage.co) est un service web qui donne la possibilité de récupérer (gratuitement) des données historiques sur des instruments financiers. Ce service qui rappelle *Yahoo Finance* offre une API web REST pour consulter les données suivantes :
- Données intraday : OHLC (*Open*, *High*, *Low* et *Close*) et volume de la journée courante (ou précédente si le marché est fermée). On doit préciser l'intervalle de temps (1, 5, 15, 30 ou 60 minutes) et le nombre de données à récupérer (les 100 dernières par défaut ou toute la journée). Maleureseument, ce service n'est proposé que pour les actions américaines.
- Données journalières : le volume et l'OHLC de l'instrument pour les 100 derniers jours ou depuis Janvier 2000.
- Données hebdomadaires : le dernier jour de la semaine courante et les données des vendredi depuis Janvier 2000.
- Données mensuelles. 

Pour les données journalières, hebdomadaires et mensuelles, le service propose deux type de fonction, adjustée et non adjustée pour prendre en compte les dividendes. Ces informations (le montant du dividende et le close adjusté) ne sont pas proposées pour les instruments européens.

Pour utiliser le service, il faut obtenir une clé. Cette opération est très simple et ne nécessite que compléter un formulaire. 

> Screenshot 

Voici quelques exemple de requêtes (remplacer API_KEY par votre clé) :
1. Les données journalières de *Saint-Gobain* des 20 dernières années
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=SGO.PA&outputsize=full&apikey=API_KEY
```
2. Les données journalières de *Société Générale* des 100 derniers jours
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=GLE.PA&apikey=XD6HTE47G8ZZIDRB
```
3. Les données mensuelles de *LVMH* 
```
https://www.alphavantage.co/query?function=TIME_SERIES_MONTHLY&symbol=MC.PA&apikey=API_KEY
```
