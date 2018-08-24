---
categories:
- hackernews
date: 2018-06-11T16:00:00Z
tags:
- hackernews
title: Hacker News Digest (02-06-2018 au 08-06-2018)
---

{% include toc %}

Ma sélection personnelle des sujets de la semaine sur
[Hacker News](https://news.ycombinator.com/). La semaine qui vient de s'écouler
a vu la plupart des sujets tourner autour de l'acquisition de Github par
Microsoft. Cette nouvelle a généré une myriades de sujets où les anti
et les pro Microsoft ont échangé leurs arguments. Je n'ai pas retenu ces sujets car il y en avait tellement. J'ai gardé juste un sur les alternatives à Github.

### [Why Development Teams Struggle to Deliver on Time, on Budget, or at All](https://www.7pace.com/blog/software-development-planning-fallacy)
Dans cet article, l'auteur traite du sujet du planning et de l'estimation des coûts d'un projet de développement en informatique. L'auteur qui note que selon certaines études ces retards coûtent entre 50 et 80 milliards de dollars part d'un phénomène psychologique appelé *[The Planning Fallacy](https://en.wikipedia.org/wiki/Planning_fallacy)*. Ce phénomène conduit les humains à être optimiste et à sous estimer le temps nécessaire pour une tâche. C'est ce que *Daniel Kahneman* décrit dans son livre *Thinking Fast and Slow* avec les deux modes de pensées rapides et lentes; avec une tendance des humains à préférer la méthode rapide car ils sont plutôt paresseux, et le mode lent demande plus d'efforts. Dit autrement, si on nous demande d'estimer le temps pour faire quelque chose, on préfère utiliser la méthode de pensée rapide au lieu d'étudier le sujet plus longuement.

L'auteur décrit quelques points pour remédier à ce problème. Les points décrits sont les suivants :
- Consacrer du temps aux planning car il est important pour le succès d'un projet. L'auteur admet que les équipes n'aiment pas les réunions autour des plannings car elles ne sont pas très utiles et qu'il faut les améliorer. Par contre, il ne précise pas les pistes pour améliorer ces réunions et pour faire adhérer les équipes autour de leur importance.
- Estimer en se basant sur des données et non sur des intuitions.
- Ajouter une marge d'erreur pour pallier aux imprévus car avec le meilleur planning, il peut y avoir toujours des imprévus. L'auteur note que beaucoup d'équipe utilisent ce point pour contrer le phénomène de *The Planning Fallacy* mais qu'en faite elles ne s'attaquent pas à l'origine du problème.

Le sujet du retard dans les projets de développement logiciel est un sujet qui a fait couler beaucoup d'encre, générer une multitude de méthodologies et de systèmes et il n'est pas prêt d'être résolu dans un avenir proche. L'auteur étudie ce problème du point de vue de la sous-estimation du temps, mais il y a d'autres facteurs qui sont la cause de ce problèmes. J'en citerai les suivants :
- L'estimation ne peut être précise car il y a toujours des inconnus dans un projet informatique et estimer l'inconnu est impossible. On peut ajouter une marge d'erreur (point 3), mais cette estimation se basera forcémment sur le *Planning Fallacy*, l'intuition ou la surestimation.
- L'estimation des coûts est la plupart du temps effectuée par des managers qui ont d'autres contraintes : diminuer les coûts, éviter le gaspillage, délivrer plus vite, obtenir un retour sur investissement. Ces facteurs ne permettent pas d'effectuer une estimation précise car le pouvoir de décision n'est pas dans les équipes de développement.
- Un projet informatique n'est jamais fini, il y a toujours des améliorations et des modifications à apporter peu importe l'état du projet à la fin de son temps de développement.  

- [Commentaires HN](https://news.ycombinator.com/item?id=17237468)

### [Want More Time? Get Rid of the Easiest Way to Spend It](https://www.raptitude.com/2017/06/want-more-time-get-rid-of-the-easiest-way-to-spend-it/)
L'auteur parle de l'utilisation qu'il fait depuis Mai dernier des réseaux
sociaux (*Facebook*, *Twitter* et *Reddit*) et comment il a gagné du temps
pour faire d'autres activités. L'auteur n'a pas complètement abandonné ces services, mais il est revenu à leur usage d'il y a une dizaine d'années
quand ils n'étaient que de simples sites webs. Au lieu de les consulter constamment
sur son téléphone, il les utilise depuis son ordinateur de bureau. En plus du
temps gagné à ne pas les consulter, il fait remarquer qu'il s'est débarassé de
toutes ces micro-interruptions causées par les notifications.

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
s'enregistrer et les données semblent couvrir les marchés européens en plus des marchés américains. Je n'ai
pas pu trouver comment obtenir la liste des symboles, mais les actions
françaises (au moins celles que j'ai testées) sont présentes :
```
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=SGO.PA&apikey=<Key>
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=AF.PA&apikey=XD6HTE47G8ZZIDRB
https://www.alphavantage.co/query?function=TIME_SERIES_DAILY&symbol=AF.PA&apikey=XD6HTE47G8ZZIDRB
```
![Benchrmark - Premier test]({{ site.url }}{{ site.baseurl }}/assets/images/alphavantage-screenshot.png )

- [Commentaires HN](https://news.ycombinator.com/item?id=17268715)

### [GitHub Alternatives](https://tutswiki.com/github-alternatives/)
Après l'acquisition de Github par Microsoft, une bonne partie de la communauté s'intérroge sur la question de rester ou de migrer vers un concurrent. Ces derniers se sont empressés d'attirer les projets à eux en présentants les méthodes de migration. Cet article présente rapidement les différentes solutions pour héberger son projet (open source ou pas). Trois catégories d'hébergement sont présentés :
- Gratuites : [Gitlab](https://about.gitlab.com/), [Bitbucket](https://bitbucket.org/), [Gitea](https://gitea.io/en-US/), [Sourceforge](https://sourceforge.net/) et [Launchpad](https://launchpad.net/)
- Payantes : [Cloud Source Repositories](https://cloud.google.com/source-repositories/), [AWS CodeCommit](https://aws.amazon.com/codecommit/)
- Auto-hébergées : [Phabricator](https://phacility.com/phabricator/), [Gitbucket](https://gitbucket.github.io/), [Gogs](https://gogs.io/), [Gitprep](http://gitprep.yukikimoto.com/) et [Allura](https://allura.apache.org/)


- [Commentaires HN](https://news.ycombinator.com/item?id=17241487)

### [For more and more people, work appears to serve no purpose](https://www.newyorker.com/books/under-review/the-bullshit-job-boom)
Cet article parle du dernier livre de l'anthropologue américan [David Graeber](https://en.wikipedia.org/wiki/David_GraeberDavid Graeber), *[Bullshit Jobs: A Theory](https://www.amazon.fr/Bullshit-Jobs-Theory-David-Graeber/dp/150114331X/)*. Ce livre qui parle de l'utilité de certains emplois, s'appuie sur des études et des sondages menés par *YouGov* sur l'avis des employées sur l'utilité de leurs postes. Ces études ont montré qu'une grande partie des sondés trouvent leur emploi inutiles. Graeber montre que ces emplois sont des *Bullshit Jobs* mais ne sont pas des *Shit jobs* car très souvent ils sont très bien rémunérés. La communauté de Hackernews a largement réagi à l'article dans les commentaires, et on sens qu'une grande majorité des intervenants est d'accord avec l'auteur du livre sur l'inutilité de certains métiers (le Powerpoint n'est pas très populaire dans la communauté HN). Par contre les intervenants ont souvent oublié que parmi les catégories visées par ce livre, il y a celle des *duct tapers* ou ceux qui réparent les problèmes qui ne devraient pas exister, et cette catégorie inclut les développeurs informatiques qui corrigent les bugs des systèmes existants. Je termine avec ce commentaire sur le domaine de la finance.
> 'I'm now convinced that the entire finance world is the biggest scam of all time'


- [Commentaires HN](https://news.ycombinator.com/item?id=17260911)
