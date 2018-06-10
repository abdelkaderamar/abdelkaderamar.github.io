---
layout: single
title:  "Hack News Digest (01-06-2018 au 08-06-2018)"
date:   2018-06-12 16:00:00 +0100
categories:
  - Posts
tags:
  - hackernews
---

{% include toc %}

Ma sélection personnelle des sujets de la semaine sur
[Hacker News](https://news.ycombinator.com/). La semaine qui vient de s'écouler
a vu la plupart des sujets tourner autour de l'acquisition de Github par
Microsoft. Cette nouvelle a généré une myriades de sujets où les anti
et les pro Microsoft ont échangé leurs arguments.


### [Want More Time? Get Rid of the Easiest Way to Spend It](https://www.raptitude.com/2017/06/want-more-time-get-rid-of-the-easiest-way-to-spend-it/)
L'auteur parle de l'utilisation qu'il fait depuis Mai dernier des réseaux
sociaux (*Facebook*, *Twitter* et *Reddit*) et comment il a gagné du temps
pour faire d'autres activités. L'auteur n'a pas abandonné ses services
complètements, mais il est revenu à leur usage d'il y a une dizaine d'années
quand ils étaient de simples sites webs. Au lieu de les consulter constamment
sur sont téléphone, il les utilise depuis son ordinateur de bureau. En plus du
temps gagné à ne pas les consulter, il fait remarqué qu'il s'est débarassé de
toutes ces micro-interruptions causées par les notificatios.

- [Commentaires HN](https://news.ycombinator.com/item?id=17228480)

### [GitTorrent: A Decentralized GitHub](https://blog.printf.net/articles/2015/05/29/announcing-gittorrent-a-decentralized-github/)
Une idée qui date de 2015 qui présente une sorte de Github décentralisé basé
sur le protocole BitTorrent et la technologie Blockchain.
- [Commentaires HN](https://news.ycombinator.com/item?id=17234498)

### [Use Emacs Org Mode and REST APIs for an up-to-date stock portfolio](http://www.sastibe.de/2018/05/2018-05-11-emacs-org-mode-rest-apis-stocks/)
L'auteur présente comment il utilise Emacs pour suivre l'évolution de  son
portefeuille d'actions en utilisant [org-mode](https://orgmode.org/) et l'API
REST du site [Alpha Vantage](https://www.alphavantage.co/). L'auteur qui n'utilise Emacs que depuis quelques semaines montre qu'Emacs n'est pas un simple éditeur de texte évolué comme beaucoup le pense.
C'est en lisant l'article que j'ai découvert les services de *Alpha Vantage* et
leur API est intéressante. L'obtention d'un clé se fait sans
s'enregistrer et les données semblent couvrir les marchés européens. Je n'ai
pas pu trouver comment obtenir la liste des symboles, mais les actions
françaises (au moins celles que j'ai testées) sont présentes :
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=SGO.PA&apikey=<Key>
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=AF.PA&apikey=XD6HTE47G8ZZIDRB
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=AF.PA&apikey=XD6HTE47G8ZZIDRB
```
![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/alphavantage-screenshot.png )

- [Commentaires HN](https://news.ycombinator.com/item?id=17268715)

### [How I Automated My Job Using Node.js](https://medium.com/dailyjs/how-i-automated-my-job-with-node-js-94bf4e423017)
- [Commentaires HN](https://news.ycombinator.com/item?id=17265458)

### [For more and more people, work appears to serve no purpose](https://www.newyorker.com/books/under-review/the-bullshit-job-boom)
- [Commentaires HN](https://news.ycombinator.com/item?id=17260911)

### [GitHub Alternatives](https://tutswiki.com/github-alternatives/)
- [Commentaires HN](https://news.ycombinator.com/item?id=17241487)

### [Why Development Teams Struggle to Deliver on Time, on Budget, or at All](https://www.7pace.com/blog/software-development-planning-fallacy)
- [Commentaires HN](https://news.ycombinator.com/item?id=17237468)
