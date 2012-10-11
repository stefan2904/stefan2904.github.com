---
layout: 	post
tags: 		[intern]
published: 	true
---

## What is this?

My new Blog. Hosted on [GitHub](http://github.com)! \o/

## GitHub Pages

Ermöglich wird das durch [GitHub Pages](http://pages.github.com/) welche aus einem [einfachen Repository](https://github.com/stefan2904/stefan2904.github.com), diese statischen Seiten hier bauen. Damit das nicht ganz so statisch ist, kommt auf den GitHub Servern der "Static Site Generator" [Jekyll](http://jekyllrb.com/) zum Einsatz. Ich muss also nichts weiter tun, als die (Text-)Dateien (Layout, CSS, Blog-Posts) in einer vordefinierten [Ordner-Struktur](https://github.com/mojombo/jekyll/wiki/Usage) und mit einer kurzen [Konfigurations-Datei](https://github.com/mojombo/jekyll/wiki/Configuration) in das Repository zu [pushen](http://de.gitready.com/beginner/2009/01/21/pushing-and-pulling.html). Jekyll erledigt den Rest. Voilà!

Damit ich mit der Konfiguration und der Stuktur nicht ganz von null anfangen musste, hab' ich auf [Jekyll-Bootstrap](http://jekyllbootstrap.com/) zurückgegriffen, welches sogar das [Twitter-Bootstrap](http://twitter.github.com/bootstrap/) mitbringt. Aus dessen GitHub Repository ausgecheckt, in meines gepusht, und online war die Seite. 

## Code & Design

Wie es derzeit ja modern ist, kann man die Artikel nicht nur in HTML, sondern auch in [Markdown](http://daringfireball.net/projects/markdown) verfassen; was insbesondere bei Links und inline-Formatierungen ein Vorteil ist, da es den Schreibfluss nicht so sehr stört. Außerdem werden Sonderzeichen richtig in ihre HTML-Codes umgesetzt. <3
(Dank [Pygments](http://pygments.org/) gibt's so nebenbei auch Syntax-Highlighting.)

Quasi das 'Tüpfelchen auf dem i' ist die Template-Sprache [Liquid](http://liquidmarkup.org/), besonders durch die [Jekyll-eigenen Filter und Erweiterungen](https://github.com/mojombo/jekyll/wiki/Liquid-Extensions) dafür. Dadurch wird der Generierungsprozess erst richtig dynamisch und ermöglicht klassiches Templating. Das beinhaltet natürlich Variablen, Schleifen und Bedingungen, was das Layout sehr übersichtlich macht. 

Durch die Kombination dieser Technologien wird außerdem der Inhalt vom Design/Layout getrennt, wie es sich gehört.

## Schrift-Art

Die Schriftgröße ist aus [bestimmten Gründen](http://twitter.com/stefan2904/status/249245742647087106) etwas größer geworden. Auf Empfehlung von [Heinz](http://wittenbrink.net/lostandfound/2012/09/schriften-fuer-meinen-blog-relaunch/) hab' ich mich für [Merriweather](http://code.google.com/webfonts/specimen/Merriweather) als Schriftart entschieden - mein Blog sieht in dieser Hinsicht seinem also nicht zufällig ein wenig ähnlich. Positiv überrascht war ich übrigens ob der Einfachheit der [Google Web Fonts](http://www.google.com/webfonts) - ein für mich neues Feld.

## Diskussion bitte!

Da der Output von Jekyll natürlich statische HTML-Seiten sind, gibt's keine Möglichkeit, direkt eine Kommentar-Funktion einzubauen. Hier kommen "Blog-Kommentar Services" in's Spiel: Zuerst hab' ich [Disqus](http://disqus.com/) installiert. Das blieb aber nicht lange, da es mir nicht gelang, das Kommentieren für nicht-registrierte User zu aktivieren. Deshalb findet sich jetzt unter jedem Post ein Kommentar-Bereich, zur Verfügung gestellt von [IntenseDebate](http://intensedebate.com/). Mal schau'n, wie sich das bewährt.

## Versionierung

Grund für den Umstieg von Google's Blogger war, neben der Unabhängigkeit, hauptsächlich die Möglichkeit, meine Artikel zu versionieren. Da mein "Perfektionismus" mit Grund dafür war, dass ich seit Längerem nichts mehr gebloggt - oder zumindest veröffentlicht - habe, gibt's hier jetzt eine "alles immer in Arbeit Policy". Um das auch technisch zu realisieren - schließlich soll man die Änderungen ja nachvollziehen können - dachte ich zuerst an ein Wiki-artiges System. Da das aber alles schnell viel zu kompliziert wurde, und weil ich sowieso mal was abseits von Softwareentwicklung mit Git machen wollte, kamen mir die oben genannten GitHub Features gerade recht. Und so findet sich unter jedem Artikel nun ein Link zur "Artikel-Geschichte" - zumindest zur [Commit History](http://git-scm.com/book/en/Git-Basics-Viewing-the-Commit-History) davon.

Feedback willkommen! ;-)