---
categories:
- hackernews
date: 2018-07-15T16:35:00Z
tags:
- hackernews
title: Hacker News Digest (07-07-2018 au 13-07-2018)
---

{% include toc %}

Ma sélection personnelle des sujets de la semaine sur
[Hacker News](https://news.ycombinator.com/)


### [Ask HN: 2018 Summer Reading List?](https://news.ycombinator.com/item?id=17513576)
Ce sujet est l'occasion de découvrir les choix de la communauté de
HackerNews en terme de lecture. Voici ma short liste de livres à tester :
- [12 Rules for Life](https://en.wikipedia.org/wiki/12_Rules_for_Life) de Jordan
Peterson
- [Why We Sleep](https://www.amazon.fr/Why-We-Sleep-Unlocking-Dreams/dp/1501144316) de Matthew Walker
- [The Millionaire Next Door](https://www.amazon.fr/Millionaire-Next-Door-Surprising-Americas/dp/1589795474)
de Thomas J. Stanley
- [Deep work](https://www.amazon.fr/Deep-work-retrouver-concentration-distractions/dp/B06XXVRZJC)
de Cal Newport

- [Commentaires HN](https://news.ycombinator.com/item?id=17513576)

### [Show HN: Markdown New Tab – A new tab replacement to jot down notes in Markdown](https://github.com/plibither8/markdown-new-tab)
Une extension chrome qui permet d'avoir une page de prise de note lors
de l'ouverture d'une nouvelle tab. Elle me sera bien utile pour garder
une trace des liens Hacker News et de mes notes pour cette série de posts (mais pas seulement). Le lien vers le plugin dans le store chrome est [ici](https://chrome.google.com/webstore/detail/markdown-new-tab/demppioeofcekpjcnlkmdjbabifjnokj). Il y a également un autre plugin,
[papier](https://chrome.google.com/webstore/detail/papier/hhjeaokafplhjoogdemakihhdhffacia),
 qui propose la même fonctionnalité.

 Dans les commentaires, j'ai pu aussi trouver cette astuce : bookmarker ce
 code (ou le taper dans la bare d'adresse directement pour essayer) :
```
 data:text/html, <body contenteditable style="font: 2rem/1.5 monospace;max-width:60rem;margin:0 auto;padding:4rem;">
 ```

La même chose mais avec un fond blanc :
 ```
 data:text/html, <body contenteditable style="font: 2rem/1.5 monospace;max-width:60rem;margin:0 auto;padding:4rem;color:white;background-color:black;">
 ```

Avec le focus directement dans la zone d'édition :
 ```
 data:text/html, <html><body id='.' contenteditable style="font: 2rem/1.5 monospace;max-width:60rem;margin:0 auto;padding:4rem;color:white;background-color:black;"></body><script type="text/javascript">var div = document.getElementById('.');setTimeout(function() {div.focus();}, 0);</script></html>
```
- [Commentaires HN](https://news.ycombinator.com/item?id=17506753)

### [Learn how to design large-scale systems](https://github.com/donnemartin/system-design-primer)
Un projet Github intéressant qui décrit la conception de systèmes
distribués à large échelle. En plus de la description des différentes
composantes d'un système distribués, le projet contient une série de
*Flashcards Anki* pour retenir les différents concepts et s'exercer aux
algorithmes et à la programmation.
- [Commentaires HN](https://news.ycombinator.com/item?id=17522362)

### [Seedbank – Collection of Interactive Machine Learning Examples](http://tools.google.com/seedbank/)
Un ensemble d'exemples de programmes *Python* sur le
[*machine learning*](https://fr.wikipedia.org/wiki/Apprentissage_automatique).
Ce sujet m'a permis de découvrir l'outil Google
[*colab*](https://colab.research.google.com/)
qui offre un environnement Python2/Python3 pour les tests sur le machine
learning. Cet outil s'exécute sur un navigateur et propose d'utiliser
des GPUs gratuitement (dans une certaine limite).
- [Commentaires HN](https://news.ycombinator.com/item?id=17516709)


### [I'm basically giving myself a permanent vacation from being BDFL](https://mail.python.org/pipermail/python-committers/2018-July/005664.html)
Le créateur du langage Python,
[Guido van Rossum](https://fr.wikipedia.org/wiki/Guido_van_Rossum),
quitte ses fonctions de BDFL (*Benevolent Dictator for Life*). Après plus de 27 ans depuis la création de son langage, il veut
s'éloigner du cercle de décision sur le projet. Pour la suite, il
laisse à la communauté le choix du mode de fonctionnement qu'elle veut mettre en
place.
- [Commentaires HN](https://news.ycombinator.com/item?id=17515492)

<!--

Web Architecture 101
https://engineering.videoblocks.com/web-architecture-101-a3224e126947/?ref=abhimanyu
https://news.ycombinator.com/item?id=17517155

George Hotz is on a hacker crusade against the ‘scam’ of self-driving cars
https://www.theverge.com/2018/7/13/17561484/george-hotz-comma-ai-self-driving-car-scam-diy-kit
https://news.ycombinator.com/item?id=17522766


Ask HN: Staring in 2010, each year what is your favorite startup?
https://news.ycombinator.com/item?id=17515664
https://news.ycombinator.com/item?id=17515664

Ask HN: Where do you get news on China VC and tech scene?
https://news.ycombinator.com/item?id=17513081
https://news.ycombinator.com/item?id=17513081

Microsoft Whiteboard is now generally available for Windows
https://techcommunity.microsoft.com/t5/Office-365-Blog/Microsoft-Whiteboard-is-now-generally-available-for-Windows/ba-p/214574
https://news.ycombinator.com/item?id=17521930

Should I Learn Java in 2018
https://www.e4developer.com/2018/06/09/should-i-learn-java-in-2018/
https://news.ycombinator.com/item?id=17522017

Google Cloud Platform – The Good, Bad, and Ugly
https://www.deps.co/blog/google-cloud-platform-good-bad-ugly/
https://news.ycombinator.com/item?id=17513758

Ask HN: 2018 Summer Reading List?
https://news.ycombinator.com/item?id=17513576
https://news.ycombinator.com/item?id=17513576

Why Kubernetes Is the New Application Server
https://developers.redhat.com/blog/2018/06/28/why-kubernetes-is-the-new-application-server/
https://news.ycombinator.com/item?id=17516706


The open-plan office is a terrible, horrible, no good, very bad idea
https://m.signalvnoise.com/the-open-plan-office-is-a-terrible-horrible-no-good-very-bad-idea-42bd9cd294e3
https://news.ycombinator.com/item?id=17513843

MacBook Pro with faster performance and new features for pros
https://www.apple.com/newsroom/2018/07/apple-updates-macbook-pro-with-faster-performance-and-new-features-for-pros/
https://news.ycombinator.com/item?id=17513828

People Aren’t Dumb, the World Is Hard
http://freakonomics.com/podcast/richard-thaler/
https://news.ycombinator.com/item?id=17513959

How GitHub Democratized Coding, Built a $2B Business, and Ended Up at Microsoft
https://producthabits.com/github/
https://news.ycombinator.com/item?id=17513688

Leaving no room for a lower-level language: A C++ Subset
http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1105r0.html
https://news.ycombinator.com/item?id=17513732

Scaling Microservices with Message Queues, Spring Boot and Kubernetes
https://learnk8s.io/blog/scaling-spring-boot-microservices
https://news.ycombinator.com/item?id=17509764

Top Continuous Integration Tools (2017)
https://stackify.com/top-continuous-integration-tools/
https://news.ycombinator.com/item?id=17509788

C++Now 2018: Matthew Butler “Secure Coding Best Practices”
https://www.youtube.com/watch?v=oW3rRfjWwUE
https://news.ycombinator.com/item?id=17509797

Show HN: Code::Stats – Free programming stats service
https://codestats.net/
https://news.ycombinator.com/item?id=17505940

Solar Just Hit a Record Low Price in the U.S
https://earther.com/solar-just-hit-a-record-low-price-in-the-u-s-1826830592
https://news.ycombinator.com/item?id=17508554

Ask HN: As a team lead how to handle project going off the rails?
https://news.ycombinator.com/item?id=17511850
https://news.ycombinator.com/item?id=17511850

Red Flags Signaling That a Rebuild Will Fail
http://www.pkc.io/blog/five-red-flags-signaling-your-rebuild-will-fail/
https://news.ycombinator.com/item?id=17510670

Ask HN: Which book have you re-read the most times? how many times?
https://news.ycombinator.com/item?id=17511800
https://news.ycombinator.com/item?id=17511800

A browser extension to make Medium more readable
https://makemediumreadable.com/
https://news.ycombinator.com/item?id=17511688

Unix system programming in OCaml (2014)
https://ocaml.github.io/ocamlunix/index.html
https://news.ycombinator.com/item?id=17510902

Show HN: Online challenge: Build a CPU from scratch
http://nandgame.com/
https://news.ycombinator.com/item?id=17508151

Unified access to the best community-driven cheat sheets repositories
https://github.com/chubin/cheat.sh
https://news.ycombinator.com/item?id=17504022

How to Learn React – Best Free Online Resources for Beginners
https://brainhub.eu/blog/how-to-learn-react-best-free-online-resources/
https://news.ycombinator.com/item?id=17507388

Djbsort: A new software library for sorting arrays of integers
https://sorting.cr.yp.to/
https://news.ycombinator.com/item?id=17505357

Bitwarden - Open Source Password Manager
https://bitwarden.com/
https://news.ycombinator.com/item?id=17503917

Firefox switching to clang-cl for Windows builds
https://groups.google.com/forum/m/#!topic/mozilla.dev.platform/wwO48xXFx0A
https://news.ycombinator.com/item?id=17504197

Menu Class – Example of Modern C++17 STL Features
https://www.bfilipek.com/2018/07/menu-cpp17-example.html
https://news.ycombinator.com/item?id=17490484

Simple Menu Class – Example of Modern C++17 STL Features
https://www.bfilipek.com/2018/07/menu-cpp17-example.html
https://news.ycombinator.com/item?id=17498188

Bartek's coding blog: How to Stay Sane with Modern C++ (2017)
https://www.bfilipek.com/2017/02/how-to-stay-sane-with-modern-c.html
https://news.ycombinator.com/item?id=17498952

Ask HN: What is your obscure personal blog or website?
https://news.ycombinator.com/item?id=17487750
https://news.ycombinator.com/item?id=17487750

Ask HN: Would you still do software engineering/dev if you could do it all over?
https://news.ycombinator.com/item?id=17498580
https://news.ycombinator.com/item?id=17498580

Sending and Receiving SMS on Linux (2015)
https://www.20papercups.net/programming/sending-receiving-sms-on-linux/
https://news.ycombinator.com/item?id=17496844

Nearly 1,000 Paintings and Drawings by Vincent van Gogh Digitized and Put Online
http://www.openculture.com/2018/07/nearly-1000-paintings-drawings-vincent-van-gogh-now-digitized-put-online-view-download-collection.html
https://news.ycombinator.com/item?id=17499152

Goodbye Microservices: From 100s of problem children to 1 superstar
https://segment.com/blog/goodbye-microservices/
https://news.ycombinator.com/item?id=17499137

How Fast Can You Learn React?
https://hackernoon.com/how-fast-can-you-learn-react-49c4bdabc0df
https://news.ycombinator.com/item?id=17497418

Let’s celebrate Hugo’s 5th birthday
https://gohugo.io/news/lets-celebrate-hugos-5th-birthday/
https://news.ycombinator.com/item?id=17497414

Scraping the Web at Scale: Lessons Learned Scraping 100B Product Pages
https://blog.scrapinghub.com/web-scraping-at-scale-lessons-learned-scraping-100-billion-products-pages
https://news.ycombinator.com/item?id=17497184

Being rational all the time isn't going to do you any favors
https://qz.com/1313944/being-rational-all-the-time-isnt-going-to-do-you-any-favors/
https://news.ycombinator.com/item?id=17493303

The case for copying business ideas
https://clearfounder.com/originality-is-overrated-the-case-for-copying-business-ideas/
https://news.ycombinator.com/item?id=17496766

Crafting Interpreters
http://craftinginterpreters.com/
https://news.ycombinator.com/item?id=17496238

Show HN: Browsh – A modern, text-based browser
https://www.brow.sh
https://news.ycombinator.com/item?id=17487552

Show HN: A prototype of a new visual web scraper project
https://scrapy.apki.io/
https://news.ycombinator.com/item?id=17489466

Show HN: Clothes shopping app UI built in React Native
https://github.com/ATF19/react-native-shop-ui
https://news.ycombinator.com/item?id=17489082

Making a low level Linux debugger, part 3: our first program
https://blog.asrpo.com/making_a_low_level_debugger_part_3
https://news.ycombinator.com/item?id=17489975

-->


<!--

C++ Coroutine Types
https://abseil.io/blog/20180713-coroutine-types
https://news.ycombinator.com/item?id=17527618

Socket.IO C++
http://socket.io/blog/socket-io-cpp/
https://news.ycombinator.com/item?id=9368426

C++ Core Guidelines
https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md
https://news.ycombinator.com/item?id=10239962

Visual C++ for Linux Development
https://blogs.msdn.microsoft.com/vcblog/2016/03/30/visual-c-for-linux-development/
https://news.ycombinator.com/item?id=11393641

Google's C++ Class
https://developers.google.com/edu/c++/
https://news.ycombinator.com/item?id=16525427

A repository of modern C++ code samples curated by the community
http://www.cppsamples.com/
https://news.ycombinator.com/item?id=9333193

C++ 17 is Done
https://herbsutter.com/2017/03/24/trip-report-winter-iso-c-standards-meeting-kona-c17-is-complete/
https://news.ycombinator.com/item?id=13954195

Single-file C/C++ public-domain/open source libraries with minimal dependencies
https://github.com/nothings/single_file_libs
https://news.ycombinator.com/item?id=13202114

Master C++ Programming with Open-Source Books
https://www.ossblog.org/master-c-programming-with-open-source-books/
https://news.ycombinator.com/item?id=13659159

Ask HN: Best way to learn modern C++?
https://news.ycombinator.com/item?id=16535886
https://news.ycombinator.com/item?id=16535886

The Fast Meme Transform: Convert Audio into Linux Commands
http://blog.robertelder.org/fast-meme-transform/
https://news.ycombinator.com/item?id=17521826

Show HN: Start actually reading what you saved in your bookmarks – Meet Mailist
http://mailist.app
https://news.ycombinator.com/item?id=17526599

Ask HN: What C++ parallelization framework do you use?
https://news.ycombinator.com/item?id=13600720
https://news.ycombinator.com/item?id=13600720

Featured Algorithm: The TBB Pipeline Class
http://www.ddj.com/212501296?cid=RSSfeed_DDJ_All
https://news.ycombinator.com/item?id=403223

Thrust is a parallel algorithms library like STL for CUDA, TBB, and OpenMP
http://thrust.github.io/
https://news.ycombinator.com/item?id=8606398

Introduction to high-level multithreading in C++ via Intel TBB library
http://blog.ruslans.com/2013/08/introduction-to-high-level.html
https://news.ycombinator.com/item?id=6223581

Multithreading: C# vs. Java
http://jj09.net/multithreading-csharp-vs-java
https://news.ycombinator.com/item?id=7494757

C++11 multithreading tutorial
http://solarianprogrammer.com/2011/12/16/cpp-11-thread-tutorial/
https://news.ycombinator.com/item?id=3360843

Common Multithreading Mistakes in C# – Unsafe Assumptions
http://benbowen.blog/post/cmmics_iii/
https://news.ycombinator.com/item?id=13704763

Multithreading in modern C++
http://www.modernescpp.com/index.php/multithreading-in-modern-c
https://news.ycombinator.com/item?id=11587661

C# 6.0: An Introduction
https://booker.codes/csharp-6-an-introduction/
https://news.ycombinator.com/item?id=10096754

Hidden features of C#
http://stackoverflow.com/questions/9033/hidden-features-of-c
https://news.ycombinator.com/item?id=3439756

A Preview of C# 8 [video]
https://channel9.msdn.com/Blogs/Seth-Juarez/A-Preview-of-C-8-with-Mads-Torgersen
https://news.ycombinator.com/item?id=15099019

Asynchrony in C# 5, Part One
http://blogs.msdn.com/b/ericlippert/archive/2010/10/28/asynchrony-in-c-5-part-one.aspx
https://news.ycombinator.com/item?id=1844578

New Features in C# 6 (2014)
http://blogs.msdn.com/b/csharpfaq/archive/2014/11/20/new-features-in-c-6.aspx
https://news.ycombinator.com/item?id=8870361

What's New in C# 6.0 [video]
http://channel9.msdn.com/Events/Visual-Studio/Connect-event-2014/116
https://news.ycombinator.com/item?id=8607648

C# 7 Work List of Features
https://github.com/dotnet/roslyn/issues/2136
https://news.ycombinator.com/item?id=9425867

Show HN: A new hobby OS from “scratch” in C#
https://github.com/amaneureka/AtomOS
https://news.ycombinator.com/item?id=13794879

New Features in C# 7.0
https://blogs.msdn.microsoft.com/dotnet/2017/03/09/new-features-in-c-7-0/
https://news.ycombinator.com/item?id=13834511

What’s New in C# 7.0
https://blogs.msdn.microsoft.com/dotnet/2016/08/24/whats-new-in-csharp-7-0/
https://news.ycombinator.com/item?id=12356259

C++Now 2018: Michael Caisse “Modern C++ in Embedded Systems”
https://www.youtube.com/watch?v=c9Xt6Me3mJ4
https://news.ycombinator.com/item?id=17518519

C++17 removed and deprecated features
https://mariusbancila.ro/blog/2018/07/05/c17-removed-and-deprecated-features/
https://news.ycombinator.com/item?id=17522026

[C++] the 2D Graphics TS – The story so far
https://hatcat.com/?p=63
https://news.ycombinator.com/item?id=17523214

-->
