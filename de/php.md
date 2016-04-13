PHP für Noobs
=============


# Was ist PHP?
PHP ist eine Programmiersprache. Gut 80% aller Websites im Internet basieren auf PHP, so z.B. auch große CMS wie WordPress, Joomla!, Drupal und Typo3.

Die Sprache ist allerdings nicht nur Web-fähig, es lassen sich in PHP auch allgemeine Konsolenprogramme schreiben (CLI, Command Line Interface) und mit der PHP-GTK kann man sogar normale Desktop-Programme in PHP schreiben (Was nicht empfohlen ist, dafür gibt es sinnvollere Technologien)

PHP ist ein Backronym für "PHP Hypertext Preprocessor", es bedeutet sinngemäß also, dass PHP dafür da ist, Hypertext vor der Ausgabe zu be- und verarbeiten.



# Warum PHP?
Zugegeben, es gibt bei weitem schönere Web-Programmiersprachen als PHP. Nach vielen Problemen in den ersten größeren Versionen von PHP was die gesamte Sprachstruktur betrifft, konnten sich Sprachen wie ASP.NET (C#, Visual Basic), Ruby, Perl, Python und heute sogar JavaScript stark durchsetzen und werden rege genutzt.

Der Vorteil, den PHP hat, ist die Tatsache, dass eigentlich so gut wie jeder Webspace, den man sich mietet, bereits mit PHP ausgestattet ist.

Dazu kommt, dass die Lernkurve in PHP zwar exponential ist, der Einstieg aber verdammt simpel.

Starten wir doch einfach mal.


# Objektorientiert, Prozedural, WTF?
Ich zeige euch hier reine, prozedurale PHP Programmierung. Die objektorientierte Programmierung in PHP ist ein Thema für sich und wird deshalb hier nicht behandelt, nicht mal im Ansatz.

Auf Basis dieses Tutorials allerdings wird es euch bei weitem leichter fallen, die objektorientierte Programmierung in PHP zu verstehen.

Dazu könnt ihr euch dann gerne OOP für Noobs durchlesen.



# Die Projektstruktur
Bevor man sich ran macht und eine PHP Applikation schreibt, sollte man sich erst einmal Gedanken darüber machen: Was will ich überhaupt erreichen? Wie soll meine Applikation am Ende funktionieren? Welche Möglichkeiten und Features soll sie bieten?

Fängt man z.B. an, Applikationen erweiterbar machen zu wollen, können sich schnell viele Dateien, Ordner und Funktionen bilden, die einen auch manchmal gerne erschlagen.

Eine gute Struktur ist das A und O für eine stabile und saubere Web-Applikation. Im besten Falle sorgt ihr dafür, dass ihr für eure weiteren Applikationen einfach eure vorhandene kopieren könnt und sie abändert. Damit spart ihr euch in Zukunft viel Arbeit.

Wir werden aus Tutorial-Gründen heute eine Portfolio-Seite für einen Designer bauen.

Unsere Menüstruktur wird folgende Punkte aufweisen:
- Startseite
- Über mich
- Portfolio
- Kontakt/Impressum


Die Startseite sowie die "Über mich"-Seite wird reinen HTML-Inhalt aufweisen.


Eine klassische, prozedurale PHP Applikation ist wie folgt strukturiert:
```
/index.php
/includes
	/config.php
	/common.php
	/database.php
/templates
	/index.php
	/portfolio.php