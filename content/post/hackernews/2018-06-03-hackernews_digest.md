---
categories:
- hackernews
date: 2018-06-03T16:00:00Z
tags:
- hackernews
title: Hacker News Digest (26-05-2018 au 01-06-2018)
---

{% include toc %}

Ma sélection personnelle des sujets de la semaine sur
[Hacker News](https://news.ycombinator.com/)


### [Why Is Front-End Development So Unstable?](https://www.breck-mckye.com/blog/2018/05/why-is-front-end-development-so-unstable/)
Dans cet article l'auteur parle du changement rapide dans les technologies du
web côté *frontend*, et donc dans les changements fréquents dans les bibliothèques
*Javascript*. En étudiant les dix projets les plus populaire sur *Github*, la
plus jeune bibliothèques a seulement deux ans, et les deux premières, React et
  Vue, ont respectivement 3 et 2,5 ans. L'auteur identifie trois facteurs
  principaux pour cette instabilité des technlogies :
  - *L'architecture micro-bibliothèques* : cette architecture utilisée par
  *React* et d'autres bibliothèques Javascript permet une grande flexibilité,
  mais en même temps augmente les risque de *breaking changes*.
  - *NPM* : le problème avec NPM est le choix de la *bonne* bibliothèque à
  utiliser pour un certain besoin. Le (très) large choix implique souvent que les
  développeurs utilisent la popularité d'une bibliothèque pour faire leur choix.
  - Le troisième facteur est une conséquence des deux premiers. Comment choisir
  une bibliothèque lors de la conception d'une application web ? En faisant des
  recherche sur le web. Le problème, est que le web est
  rempli d'articles de promotions sur les nouvelles technologies *Javascript*
  qui rendent difficiles de faire un choix sur les outils.

L'article a soulevé pas mal de débats sur HN. Ce n'est pas le commentaire le
plus constructif mais j'ai retenu celui-ci :

> Programming industry is the only one more fashion-driven than the fashion industry. This is a known issue going back to the dawn time.

- [Commentaires HN](https://news.ycombinator.com/item?id=17190992)

### [How Scrum disempowers developers](https://www.lambdacambridge.com/blog/how-scrum-disempowers-developers-and-destroys-agile)
Cette critique de la méthode Agile *Scrum* et la façon dont cette méthode traite
le rôle des développeurs dans le processus de développement d'un produit.
Dans le processus *Scrum*, une grande partie des responsabilités est donnée aux
développeurs, mais à l'opposé, une grande partie du pouvoir est attribuée aux
deux autres acteurs principaux : le *Product Owner* et le *Scrum Master*.
L'auteur est très critique sur ce dernier, et en particuliers sur les
pseudo-certifications de quelques jours pour obtenir le titre de *Scrum Master*.
Selon l'auteur, le rôle du *Scrum Master* devrait être attribué à un leader
technique avec des capacité de management.
- [Commentaires HN](https://news.ycombinator.com/item?id=17186591)

### [Show HN: Cost of a 51% Attack on Popular Cryptocurrencies](https://www.crypto51.app)
Après l'attaque de *Bicoin Gold* au mois de Mai, le concepteur de ce site s'est
intéressé au coût de puissance de calcul pour mener des attaques de
type [51% attack](https://www.investopedia.com/terms/1/51-attack.asp). Pour
estimer le coût, le site de minage [Nicehash](https://www.nicehash.com/) a été
utilisé et l'auteur a calculé le coût d'une attaque pendant une heure. Ce coût
reste théorique car ce n'est possible que dans le cas de petites cryptomonnaies,
car dans le cas des cryptomonnaies importantes, *Nicehash* ne propose pas assez de puissance
de calcul pour mener l'attaque. Par exemple, dans le cas du *Bicoin*, *Nicehash*
 n'a que 2% de la puissance de calcul nécessaire. Mais dans l'hypothèse où
 Nicehash offrait une puissance de calcul suffisante, une attaque d'une heure sur le Bitcoin
 coûterait moins de 600.000$. Le tableau présenté, montre que *Niceshash* propose
 une puissance de minage suffisante pour attaquer plusieurs cryptomonnaies (
   ces cryptomonnaies sont celles où *Nicehash* propose plus que 100% de la
   puissance de minage.)
- [Commentaires HN](https://news.ycombinator.com/item?id=17173051)

### [Macron Vowed to Make France a ‘Startup Nation.’ Is It Getting There?](https://www.nytimes.com/2018/05/23/business/emmanuel-macron-france-technology.html)
Le point de vue du *New York Times* sur le concept de *"France nation startup"*
lancé par *Emmanuel Macron*. L'article parle des efforts de la France pour
rattraper son retard sur ces voisins européens et en particulier sur la
Grande Bretagne. Un point intéressant soulevé par l'article est celui de la
banque d'investissement publique
[Bpifrance](https://fr.wikipedia.org/wiki/Bpifrance). Vue de l'étranger, cet
organisme qui soutient le développement des entreprise, rend difficile
l'estimation de la rentabilité d'un investissment en France.  
En plus de l'avis du *New York Times*, les commentaires de *Hacker News* sont
l'occasion de lire l'avis des lecteurs sur la France (certains sont français,
  d'autres travaillent ou ont travaillé en France mais une grande majorité n'est
  pas directement sur le terrain).  
- [Commentaires HN](https://news.ycombinator.com/item?id=17169314)

### [The Importance of Deep Work and the 30-Hour Method for Learning a New Skill](https://azeria-labs.com/the-importance-of-deep-work-the-30-hour-method-for-learning-a-new-skill/)
L'article est sur méthode de productivité présentée par
[Cal Newport](https://en.wikipedia.org/wiki/Cal_Newport) dans son livre
[Deep Work](https://www.amazon.fr/Deep-work-retrouver-concentration-distractions/dp/B06XXVRZJC). L'auteur se base sur cette méthode dans le domaine d'apprentissage de nouvelles
compétences en informatique.
- [Commentaires HN](https://news.ycombinator.com/item?id=17163251)

<!--
### [Reality Driven Development: Fixing Project Management in Software](http://www.brightball.com/articles/reality-driven-development-fixing-project-management-in-software)
- [Commentaires HN](https://news.ycombinator.com/item?id=17154355)
-->
