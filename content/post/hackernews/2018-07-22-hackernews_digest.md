---
categories:
- hackernews
date: 2018-07-22T12:00:00Z
tags:
- hackernews
title: Hacker News Digest (14-07-2018 au 20-07-2018)
---

{% include toc %}

Ma sélection personnelle des sujets de la semaine sur
[Hacker News](https://news.ycombinator.com/)


# [C++ Coroutine Types](https://abseil.io/blog/20180713-coroutine-types)
Un article qui parle du design des coroutines dans la prochaine norme C++20.
Cette fonctionnalité permettra d'écrire des fonctions qui peuvent être
suspendues puis redémarrées, le but étant de pouvoir écrire plus facilement
du code asynchrone.

Le type permettant d'écrire des coroutines n'est pas encore défini mais les spécifications s'orientent vers un type dans la STL qui s'appelera
`std::task<T>`.

- [Commentaires HN](https://news.ycombinator.com/item?id=17527618)

# [Reflections on Three Years of Reading Knuth](http://commandlinefanatic.com/cgi-bin/showarticle.cgi?article=art070)

L'auteur a passé trois ans à lire les trois tomes de "The Art of Programming" de
*Donald Knuth* et résume ses impressions sur l'utilité de cet ouvrage considéré
comme beaucoup comme une référence mais que très peu de personnes ont lu
effectivement. L'auteur admet la difficulté de l'ouvrage et cite certaines
parties qui sont inutiles maintenant (par exemple la partie sur la gestion de
la mémoire sur bandes magnétique). L'avis de l'auteur peut se résumer ainsi :
- l'ouvrage demande beaucoup de temps, si vous en manquez, dirigez vous plutôt
vers des ouvrages plus orientés "entreprise"
- l'assembleur n'est pas un obstacle pour la compréhension car il ne représente
qu'une petite partie du code. Le reste est fait en pseudocode facile à
comprendre.

- [Commentaires HN](https://news.ycombinator.com/item?id=17546734)

# [The Data Transfer Project](https://datatransferproject.dev/)

Un projet qui a pour objectif de fournir un service de transfert de données
entre différents fournisseurs. Pour cela, le projet s'intéresse à
l'interopérabilité des services et à la portabilité des données. Parmi les
exemples d'utilisation possible :
- changement du fournisseur de services (photos, drive, etc.)
- utilisation du service d'un autre fournisseur que celui sur lequel sont
stockées les données
- transfert des données à cause de la faillite du fournisseur de service
- ...

Le projet est actuellement en phase de développement. Le code se trouve
[ici](https://github.com/google/data-transfer-project). Les instructions
d'utilisation sont [ici](https://github.com/google/data-transfer-project/blob/master/Documentation/RunningLocally.md)
pour l'image Docker. A noter qu'il faut une clé développeur pour chaque
fournisseur de service à utiliser. Parmi les fournisseurs impliqués dans ce
projet, on trouve Google, Twitter, Microsoft, et Instagram.

- [Commentaires HN](https://news.ycombinator.com/item?id=17574707)

# [Farewell, Google Maps](https://www.inderapotheke.de/blog/farewell-google-maps)

Cette startup allemande a eu la mauvaise surprise de recevoir au mois de Juin
un mail de Google leur annonçant un changement de la politique tarifaire de ce
dernier pour l'utilisation de son service Google Maps. Après avoir contacté
le service client de Google, elle a eu les détails du changement :
- l'usage gratuit passe de 750K requêtes à 28k requêtes (divisé par plus de 30).
- le prix de l'utilisation commerciale de chaque 1000 requêtes passe de 0.5$ à
7$ (multiplé par 14)

Et la conséquence du changement est telle que le coût mensuel d'utilisation du service
pour cette startup est passé de 0 à 5000$. Après avoir étudier les alternatives,
la startup a décidé de partir vers les concurrents de Google, en utilisant la
librairie JavaScript open-source [Leaflet](https://leafletjs.com/) qui permet
de choisir facilement le fournisseur de cartes. Le problème du
prix mis de côté, Google a la politique de prix la plus transparente, car les
autres facturent en fonction du nombre de fragments et non en fonction du
nombre de cartes. Mais en testant les deux concurrents *Mapbox* et *MapTiler*,
le coût quotidien d'utilisation est passé de 80$ (Google) à 9$ (*Mapbox* ou
  *MapTiler*).

L'article soulève à la fin un point très important. Ce changement brusque des
tarifs de Google va réduire la confiance des entreprises pour dépendre des
autres services de Google. L'utilisation d'outils comme *Leaflet* peut s'avérer très utile pour éviter la dépendance à un seul fournisseur.

- [Commentaires HN](https://news.ycombinator.com/item?id=17570029)

# [Show HN: How to make your Python code more idiomatic – 25 tips and tricks](https://github.com/jerry-git/learn-python3#idiomatic-python)

Un projet *Github* qui propose un ensemble de recommandation pour améliorer son
code *Python*.

- [Commentaires HN](https://news.ycombinator.com/item?id=17529326)

# [“Real developers don't use UIs”: The value of web UIs for CLI-oriented users](https://medium.com/design-ibm/real-developers-dont-use-uis-daea7404fb4e)
Un article assez long mais divertissant sur interfaces utilisateurs en ligne
de commande (CLI) versus les interfaces graphiques (GUI) dans le domaine du web
en particulier. L'auteur détaille les avantages et les particularités de
chacune des deux types d'interface. Il conclut sur le fait que les deux
interfaces doivent être complémentaires et non redondantes.

- [Commentaires HN](https://news.ycombinator.com/item?id=17559973)





<!--

The Effect of Sleep on Happiness

https://www.trackinghappiness.com/effect-sleep-happiness/

https://news.ycombinator.com/item?id=17558542

---

How to Design your Resume

https://uxdesign.cc/how-to-design-your-resumes-3b86ff7d9f76

https://news.ycombinator.com/item?id=17539825

---

Ask HN: Why do you keep a personal knowledge base?

https://news.ycombinator.com/item?id=17530498

https://news.ycombinator.com/item?id=17530498

-->

<!--

Ask HN: How to Seriously Start with Machine Learning and AI

https://news.ycombinator.com/item?id=16167620

https://news.ycombinator.com/item?id=16167620

---
What is going on in tech industry today?

https://news.ycombinator.com/item?id=17530580

https://news.ycombinator.com/item?id=17530580
-->

<!--
Ask HN: What was your best passive income in 2017?
https://news.ycombinator.com/item?id=16815842
https://news.ycombinator.com/item?id=16815842

Ask HN: How much passive income do you generate, and from what?
https://news.ycombinator.com/item?id=17566891
https://news.ycombinator.com/item?id=17566891


A new Darpa program to develop insect-scale robots
https://spectrum.ieee.org/automaton/robotics/robotics-hardware/darpa-wants-your-insect-scale-robots-for-a-micro-olympics
https://news.ycombinator.com/item?id=17575319

P1108R0: web_view for the C++ standard library
http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1108r0.html
https://news.ycombinator.com/item?id=17560942

Ask HN: Software eng, but not a web dev. Learn new frameworks to build MVP?
https://news.ycombinator.com/item?id=17563170
https://news.ycombinator.com/item?id=17563170



Resume Examples from people who got hired by Google, Apple, NASA and others
https://www.kickresume.com/help-center/resume-samples/
https://news.ycombinator.com/item?id=17565478

Work less, get more: New Zealand firm's four-day week an 'unmitigated success'
https://www.theguardian.com/world/2018/jul/19/work-less-get-more-new-zealand-firms-four-day-week-an-unmitigated-success
https://news.ycombinator.com/item?id=17569391

JavaScript fundamentals before learning React
https://www.robinwieruch.de/javascript-fundamentals-react-requirements/
https://news.ycombinator.com/item?id=17569848

Project Fuchsia: Google Is Quietly Working on a Successor to Android
https://www.bloomberg.com/news/articles/2018-07-19/google-team-is-said-to-plot-android-successor-draw-skepticism
https://news.ycombinator.com/item?id=17566138

Ask HN: Were you happy moving your API from REST to GraphQL?
https://news.ycombinator.com/item?id=17565508
https://news.ycombinator.com/item?id=17565508

Best Buy Should Be Dead, but It’s Thriving in the Age of Amazon
https://www.bloomberg.com/news/features/2018-07-19/best-buy-should-be-dead-but-it-s-thriving-in-the-age-of-amazon
https://news.ycombinator.com/item?id=17566164

Blue Origin successfully lands both booster and crew capsule after test launch
https://techcrunch.com/2018/07/18/blue-origin-successfully-lands-both-booster-and-crew-capsule-after-test-launch/
https://news.ycombinator.com/item?id=17559675

The code that took America to the moon was just published to GitHub
https://qz.com/726338/the-code-that-took-america-to-the-moon-was-just-published-to-github-and-its-like-a-1960s-time-capsule/
https://news.ycombinator.com/item?id=17555878

Jupiter has 10 more moons we didn't know about
https://www.nature.com/articles/d41586-018-05725-6
https://news.ycombinator.com/item?id=17557002

Ask HN: What front end tools do you find yourself most productive with?
https://news.ycombinator.com/item?id=17562305
https://news.ycombinator.com/item?id=17562305

Python exercises to practice skills
https://github.com/srigalibe/pynotes/tree/master/Exercises-2
https://news.ycombinator.com/item?id=17560112

Show HN: Pinpointer, a Firefox extension to share links to page elements
https://addons.mozilla.org/en-US/firefox/addon/pinpointer/
https://news.ycombinator.com/item?id=17556805

Google to Be Fined $5B by EU in Android Antitrust Case
https://www.wsj.com/articles/google-to-be-fined-5-billion-by-eu-in-android-case-1531903470
https://news.ycombinator.com/item?id=17556497

In-Place Construction for std::any, std::variant and std::optional, C++17
https://www.bfilipek.com/2018/07/in-place-cpp17.html
https://news.ycombinator.com/item?id=17549826

Performance implications of default struct equality in C#
https://blogs.msdn.microsoft.com/seteplia/2018/07/17/performance-implications-of-default-struct-equality-in-c/
https://news.ycombinator.com/item?id=17547352

When You Watch Sports, Your Brain Thinks You’re Playing
http://nautil.us/issue/39/sport/the-unique-neurology-of-the-sports-fans-brain
https://news.ycombinator.com/item?id=17535995

Parcel: Fast, zero configuration web application bundler
https://github.com/parcel-bundler/parcel
https://news.ycombinator.com/item?id=17547433

Modern C++ for C Programmers: Part 4
https://ds9a.nl/articles/posts/cpp-4/
https://news.ycombinator.com/item?id=17544207

Show HN: Ramd.js JavaScript library for making TODO-like applications
https://github.com/vladocar/ramd.js
https://news.ycombinator.com/item?id=17540119

Show HN: I ran sentiment analysis on Show HN comments and got the meanest ones
https://hn.walzr.com
https://news.ycombinator.com/item?id=17540393

100+ Effective tactics to promote your blog posts
https://www.indiehackers.com/@indieorbust/100-effective-tactics-to-promote-your-blog-posts-d8905f76d3
https://news.ycombinator.com/item?id=17542563

Twitch streamers who spend years broadcasting to no one
https://www.theverge.com/2018/7/16/17569520/twitch-streamers-zero-viewers-motivation-community
https://news.ycombinator.com/item?id=17541600

The Power of Positive People
https://www.nytimes.com/2018/07/10/well/the-power-of-positive-people.html
https://news.ycombinator.com/item?id=17544300

Keeping a plaintext “did” file
http://theptrk.com/2018/07/11/did-txt-file/
https://news.ycombinator.com/item?id=17538697

Bullet journal: A simple productivity system that just uses pen and paper
http://qz.com/701309/people-are-falling-in-love-with-a-simple-productivity-system-that-just-uses-pen-and-paper/
https://news.ycombinator.com/item?id=11856987

How to Bullet Journal
https://www.youtube.com/watch?v=fm15cmYU0IM
https://news.ycombinator.com/item?id=13471590

How to Beat Digital Overload with a Bullet Journal
https://medium.com/@cloudapp/how-to-beat-digital-overwhelm-with-a-bullet-journal-217668be2235?utm_content=hackernews_bulletjournals&utm_medium=hackernews&utm_source=hackernews_medium_bulletjournals
https://news.ycombinator.com/item?id=15031865

BuJoPro: Thoughts on Adapting Bullet Journal to a Hyper-Connected World
http://calnewport.com/blog/2017/12/15/bujopro-thoughts-on-adapting-bullet-journal-to-a-hyper-connected-world
https://news.ycombinator.com/item?id=15938942

Ask HN: Is it a good time to switch to Ubuntu 18.04 desktop?
https://news.ycombinator.com/item?id=17538091
https://news.ycombinator.com/item?id=17538091

Ask HN: How do you keep checklists?
https://news.ycombinator.com/item?id=17537675
https://news.ycombinator.com/item?id=17537675

My Startup Failed, I Lost Everything. Here’s What I Learned:
https://medium.com/@StartupJourney/my-startup-failed-i-lost-everything-heres-what-i-learned-44658a116464
https://news.ycombinator.com/item?id=17538349

Open-Source Release Practices (2013)
http://en.tldp.org/HOWTO/Software-Release-Practice-HOWTO/
https://news.ycombinator.com/item?id=17534633

Ask HN: Reasons to stay in Software Engineering
https://news.ycombinator.com/item?id=17534845
https://news.ycombinator.com/item?id=17534845

Show HN: All Side Projects – side projects and apps for sale
https://www.allsideprojects.com
https://news.ycombinator.com/item?id=17534379

Why Use OpenStreetMap Instead of Google Maps?
https://www.openstreetmap.org/user/jbelien/diary/44356
https://news.ycombinator.com/item?id=17531713

Show HN: Start actually reading what you saved in your bookmarks – Meet Mailist
http://mailist.app
https://news.ycombinator.com/item?id=17526599

Ask HN: Favorite note-taking software?
https://news.ycombinator.com/item?id=17532094
https://news.ycombinator.com/item?id=17532094

Compile Time C++ Snake Game
https://github.com/mattbierner/STT-C-Compile-Time-Snake
https://news.ycombinator.com/item?id=17533636

The inconvenient truth about cancer and mobile phones
https://www.theguardian.com/technology/2018/jul/14/mobile-phones-cancer-inconvenient-truths
https://news.ycombinator.com/item?id=17530688

Show HN: Guppy, a GUI desktop app that replaces the terminal for React dev
https://github.com/joshwcomeau/guppy
https://news.ycombinator.com/item?id=17530818

My experience teaching my kids some programming [Racket]
http://emmanueltouzery.github.io/blog/posts/2016-10-13-teaching-racket.html
https://news.ycombinator.com/item?id=17530192

Open Sourced Logo Icons
http://logodust.com/?ref=mailchimp083582
https://news.ycombinator.com/item?id=17529849
-->
