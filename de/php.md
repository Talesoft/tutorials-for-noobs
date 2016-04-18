PHP für Noobs
=============


# Was ist PHP?
PHP ist eine Programmiersprache. Knapp 80% aller Websites im Internet basieren auf PHP, so z.B. auch große CMS wie WordPress, Joomla!, Drupal und Typo3.

Die Sprache ist allerdings nicht nur Web-fähig, es lassen sich in PHP auch allgemeine Konsolenprogramme schreiben (CLI, Command Line Interface) und mit der PHP-GTK kann man sogar normale Desktop-Programme in PHP schreiben (Was nicht empfohlen ist, dafür gibt es sinnvollere Technologien)

PHP ist ein Backronym für "PHP Hypertext Preprocessor", es bedeutet sinngemäß also, dass PHP dafür da ist, Hypertext vor der Ausgabe zu be- und verarbeiten.


# Vorwort
Bevor ihr dies lest: Könnt ihr noch kein HTML, wird euch das alles hier nicht helfen. Lernt HTML. Dafür gibt es HTML für Noobs eine Datei weiter.

Dieser Guide ist sehr fixiert auf Windows-Systeme. Wenn euch das stört: Schade. Vielleicht kommt später noch mal ein Linux-Zusatz.

**Keine Angst vor Sonderzeichen!**

Wirklich, ihr gewöhnt euch mit etwas Übung blitzschnell an die diversen Sonderzeichen, die in der Programmierung verwendet werden und nach und nach werdet ihr auch erkennen, warum es diese alle gibt und welchen Sinn sie haben.


# Warum PHP?
Zugegeben, es gibt bei weitem schönere Web-Programmiersprachen als PHP. Nach vielen Problemen in den ersten größeren Versionen von PHP was die gesamte Sprachstruktur betrifft, konnten sich Sprachen wie ASP.NET (C#, Visual Basic), Ruby, Perl, Python und heute sogar JavaScript stark durchsetzen und werden rege genutzt.

Der Vorteil, den PHP hat, ist die Tatsache, dass eigentlich so gut wie jeder Webspace, den man sich mietet, bereits mit PHP ausgestattet ist. Man schmeißt eine PHP-Datei drauf, ruft sie im Browser auf und sie ackert los.

Dazu kommt, dass die Lernkurve in PHP zwar exponential ist, der Einstieg aber verdammt simpel.

Ein weiterer wichtiger Grund für PHP Entwickler ist die Tatsache, dass sie ziemlich gut verdienen. Die Einstiegsgehälter in Deutschland für halbwegs fähige PHP Entwickler liegen (wenn man auch sonst ein halbwegs kompetenter Allgemeinmensch ist) bei 40.000€/p.a., ein Experte mit ca. 10 Jahren Erfahrung geht für ca. 72.000€/p.a. über den Tisch, nur damit ihr mal ein paar Richtlinien habt.

Wenn ihr also bisher Bäcker/Amazon-Packer/KFZ-Mechaniker/Kassierer oder sonst irgend einen der Jobs gemacht habt, die in spätestens 10 Jahren durch Leute wie mich wegautomatisiert wurden, dann seid ihr hier genau richtig.

Bei Entwicklern ignoriert man eben oft und gerne das fehlende Studium oder Abitur, weil sie händerringend gesucht werden und es nur eine handvoll kompetenter Entwickler auf dem Markt gibt.


Starten wir doch einfach mal.


# Objektorientiert, Prozedural, WTF?
Ich zeige euch hier reine, prozedurale PHP Programmierung. Die objektorientierte Programmierung in PHP ist ein Thema für sich und wird deshalb hier nicht behandelt, nicht mal im Ansatz.

Auf Basis dieses Tutorials allerdings wird es euch bei weitem leichter fallen, die objektorientierte Programmierung in PHP zu verstehen.

Dazu könnt ihr euch dann gerne OOP für Noobs durchlesen.

Bitte lasst euch im Laufe dieses Tutorials nicht von der OOP verleiten. Auch wenn ihr sie eventuell bereits kennt und einige Dinge hier sich definitiv besser darin abbilden lassen, wir fangen mit den Basics an und ihr solltet den Kopf dafür frei haben.


# Terminologie
Damit ihr gleich nicht verwirrt seid, wenn ihr einige Begriffe noch nicht kennt.

Als **Server** (Auslieferer, Dienstausführer) wird hier gleich meist der Rechner bezeichnet, auf dem euer eigenes PHP Projekt liegt. Dies kann ein 1€ Webspace bei Strato oder 1und1 sein, dies kann euer lokaler PC mit einer Installation von Xampp oder Apache2 und PHP5 sein.

Als **Client** (Anforderer, Kunde) wird hier in der Regel der User bezeichnet, der eure Website besucht. Damit ist nicht ein bestimmte User gemeint, sondern allgemein jeder User ist ein **Client** für euren **Server**.

Mit **Webserver** meine ich einen **Server**, auf dem eine bestimmte Software läuft, nämlich ein **Webserver**. Der _servt_ eben das _Web_. Dafür gibt es z.B. Apache2 und nginx in der Linux-Welt und Microsoft's IIS in der Windows-Welt. Jeder dieser Webserver kann mit PHP arbeiten.

Mit **Webspace** meine ich den Ordner auf eurem **Webserver**, in dem ihr eure Dateien ablegt. In unserem Beispiel mit Xampp gleich unten wird unser Webspace erst mal `C:\xampp\htdocs` sein.

Mit **URL** (Unified Resource Locator) rede ich von einer Adresse (z.B. `http://google.de/search?q=such+was`), unter der ihr einen bestimmten Web-Dienst erreichen könnt. Dazu gerne noch mal HTTP for Noobs anschauen, dort wird es etwas verdeutlicht.

# Der Webserver
Bei HTML war es noch so, dass wir eine HTML-Datei auf dem Desktop erstellen können. Dies ist jetzt nicht mehr so.

**Warum?**

PHP wird nicht vom Browser interpretiert, wie z.B. HTML. Der Browser selbst interpretiert nur HTML, CSS und JavaScript.

Wäre ja auch etwas fatal, wenn ihr eine Datenbankverbindung aufbauen wollt und die Zugangsdaten für selbige erst mal an den Client übertragen werden müssen.

PHP wird bereits vor der Ausgabe auf dem Server ausgeführt, kann dann _auf dem Server_ z.B. Daten aus einer Datenbank holen, daraus HTML generieren und lediglich das generierte HTML wird zum Client übertragen.

Nur Ausgaben, die ihr in PHP tätigt, werden jemals zum Client übertragen, kein Code den ihr ausführt und keine Funktionen, die ihr irgendwo definiert.


Wir benötigen also einen Webserver zum betreiben von PHP.

Damit dies für uns nun einfach gehalten wird, installieren wir uns diesen lokal, damit wir auf unserem eigenen Computer PHP entwickeln können.


#### Xampp
Installiert Xampp (Googelt danach, apachefriends.org ist die korrekte Seite). Dies ist die beste Möglichkeit für euch, schnell einen Einstieg in PHP zu erlangen.


Damit ihr nicht lange verwirrt seid, was wofür ist:

1. Installiert Xampp im Standard-Verzeichnis `C:\xampp`
2. Löscht alle Dateien im `C:\xampp\htdocs` Verzeichnis
3. Erstellt euch einen Ordner im `htdocs`-Verzeichnis, nennt ihn z.B. `learning-php`

Nun startet euer Xampp Control Panel und startet den "Apache"-Dienst

Im besten Falle sollte das "Apache" grün hinterlegt werden und bei "Port(s)" sollten die Zahlen `80` und `443` erscheinen.
Tut es das nicht, achtet darauf, dass keine anderen Programme den Port 80 oder 443 blockieren, ansonsten schließt diese.

Skype und TeamViewer benötigen z.B. standardmässig den Port 80, können sich aber auch umsiedeln, ist dieser erst einmal belegt. Also notfalls Skype schließen, Apache starten, Skype wieder starten.


#### Port 80 und 443
Wenn euch Port 80 noch kein Begriff ist, bitte ich euch darum, erst HTTP für Noobs zu lesen.

`80` ist der Standardport für HTTP. `443` ist der Standardport für HTTPS, also HTTP-Secure, also verschlüsseltes HTTP, also etwas, was uns _jetzt in diesem Moment_ gerade noch nicht interessiert.

Wichtig ist, dass der Webserver auf Port `80` hört.


#### localhost
Öffnet nun einen Browser und gebt die Adresse `http://localhost` ein.

Es sollte sich ein sogenanntes Directory Listing öffnen, eine Art Dateibrowser für euren Webspace.

Die Standardeinstellung des Xampp-Apaches ist, den Ordner C:\xampp\htdocs im Web zu spiegeln. Folglicherweise müsstet ihr einen Ordner namens `learning-php` sehen, sofern ihr diesen oben wie besprochen erstellt habt. Habt ihr es nicht, tut es.

Rufen wir die URL `http://localhost/learning-php` auf (denkt dran, wir spiegeln den Ordner `C:\xampp\htdocs` unter `http://localhost`), solltet ihr den Inhalt des Ordners `learning-php` sehen. Ihr könnt eine Textdatei in dem Ordner erstellen und solltet diese im Browser sehen können.

**Was ist dieses `localhost`?**
Diesen Part könnt ihr überspringen, wenn ihr nicht all zu wissbegierig seid.

Euer Computer besitzt mindestens 2 Netzwerk-Schnittstellen. 

- Jene, die in euer Heimnetzwerk und ins Internet führt, ins sogenannte `Ethernet`.
- Weiterhin die sogenannte `Loopback` Schnittstelle, die sämtlichen Traffic, der hineingeht...auf dem selben Endpunkt wieder ausgibt. Ihr schickt Netzwerktraffic an euch selbst.

Das Loopback-Interface hört standardmässig auf die IP Adresse `127.0.0.1` (und das wird sich auch nie ändern).

`localhost` ist ein Name, der im System verankert automatisch auf `127.0.0.1` auflöst und damit quasi "das Gerät, auf dem ich mich befinde" anspricht.

Gebt `http://127.0.0.1` im Browser ein und ihr seht, dass es genau dassselbe ist, wie `http://localhost`, nur umständlicher zu schreiben (weshalb es `localhost` überhaupt gibt)


# Die IDE
Was ist eigentlich eine IDE?

IDE steht für `Integrated Development Environment` und bedeutet sinngemäß `Integrierte Entwicklungsumgebung`. Das `Integriert` lässt sich dabei breit fächern, aber es geht meist auf die Integration in Tools zur Fehlersuche (Debugger) und Code-Analyse (Profiler) zurück.

Um PHP entspannt entwickeln zu können, benötigt ihr 2 Programme. **Eine IDE und einen Editor**.

Die IDE ist das große, mächtige Geschütz, dass ihr auffahrt, wenn ihr eine komplette Website oder eine Applikation mit PHP umsetzt. Die Vorzüge sind eine richtige Projekt-Verwaltung, das automatische Umbenennen von Funktionen und eine automatische Code-Analyse, die offensichtliche Fehler sofort hervorheben.

Dafür habt ihr zur Auswahl:
- PHPStorm (Kostenpflichtig, mit Testversion, aber _sehr_ zu empfehlen)
- Netbeans (Kostenlos, absolut ausreichend für die meisten Tasks)
- Zend Studio (Kostenpflichtig, mit Testversion, Eclipse mit ein paar Plugins als _eigene, tolle, neue IDE_ verkauft)
- Eclipse mit Plugins (Kostenlos, umständlich in der Konfiguration, steht einmal konfiguriert einem Netbeans in nichts nach)
- Adobe Dreamweaver (Kostenpflichtig, primär dazu da, um schlecht zusammengewürfeltes HTML aus einem zweitklassigen WYSIWYG-Editor zu erhalten)

Ich kann euch für den Anfang Netbeans empfehlen und wenn ihr richtig in PHP einsteigt, gönnt euch eine PHPStorm Lizenz. Es lohnt sich!



Der Editor ist für den klassischen Doppelklick, man hat sich eine ZIP runtergeladen, da drin liegen ein paar PHP-Dateien, die man sich angucken will, aber nicht gleich das ganze Projekt. 

Der Windows-Editor würde grundsätzlich ausreichen, aber dieser kann keine Linux-Zeilenumbrüche (kommt später) und er markiert, gerade was Code betrifft, einfach völlig hirnverbrannt.

Als Editor kann ich euch folgende beiden ans Herz legen:
- Sublime Text 3 (Stammt aus der OSX Welt und wurde nach Windows portiert, Python-basiert, erweiterbar hat auch eine kleine Projektverwaltung, sehr schnell)
- Notepad++ (Quasi das Windows-Pendant zu Sublime Text, nicht-python basiert, kommt etwas flacher und hässliger, ist aber ebenso erweiterbar)

Hier empfehle ich ganz klar Sublime Text 3, einfach weil es von Hause aus mehr hilfreiche Features mitbringt, so kann man z.B. einen Ordner öffnen und sieht dann links eine Art Projektstruktur.



Ich habe selbst eine Weile lang ausschließlich mit Sublime Text 3 entwickelt und für kleinere Geschichten reicht es völlig aus.

Bevor ihr hier weiter lest, installiert euch eine IDE und einen Editor und stellt den Editor als Standardprogramm für `.php`-Dateien ein.



# Hello World!
Zu jeder Einführung in einer Programmiersprache gehört das sogenannte "Hello World!".

Wer es nicht kennt, "Hello World!" ist ein klassisches Mittel um darzustellen, wie eine einfache, normale Ausgabe in einem Programm erzeugt wird.

Erstellt in eurem `learning-php` Ordner eine Datei namens `hello-world.php`. In diese tragt ihr folgenden Inhalt ein:

```php
<?php

echo 'Hello World!';

```


Danach ruft ihr diese Datei im Browser auf, nämlich unter `http://localhost/learning-php/hello-world.php`.

Erscheinen sollte einfach nur ein Text, nämlich `Hello World!`.

Was wir gerade getan haben ist eine Ausgabe in PHP. 

Schauen wir uns die Datei einmal genau an:

- Mit `<?php` markieren wir den Beginn eines PHP-Code-Blocks. Mit `?>` schließen wir diesen wieder, können ihn allerdings auch weglassen, wenn die Datei ausschließlich PHP beinhält bzw. anschließend kein HTML mehr folgt.
- Mit `echo` erzeugen wir eine Ausgabe. Dies kann z.B. am Ende einer Verarbeitung von Daten erfolgen. Diese Ausgabe wird so, wie sie übergeben wird, direkt an den Client übermittelt.
- Die `'`-Zeichen markieren einen sogenannten `String`. Ein String ist ein Text. Eine Sammlung aus Zeichen. Die Datentypen lernen wir später noch kennen. Ein String muss immer vollständig von Anführungszeichen (oder auch `Quotes`) umgeben sein.
- In unserem String steht der Text `Hello World!`, der ausgegeben werden soll. Die Anführungszeichen werden natürlich nicht mit ausgegeben.
- Das `;` ist notwendig und beendet unsere Anweisung (oder auch `Statement`).

Ich nenne bewusst die englischen Begriffe dazu, damit ihr euch später beim Googeln leichter zurecht findet.


# Ausgabe mit HTML
Die Ausgabe muss nicht unbedingt reines PHP sein.

PHP ist (ursprünglich) dafür gestaltet worden, mit HTML zusammen verwendet zu werden.

```php
<h1>
	<?php

	echo 'Mein Titel!'; 

	?>
</h1>
```

Da hier am Ende noch ein `</h1>` nach unserem PHP folgt, müssen wir den PHP-Anweisungs-Block (Im folgenden nur noch `PHP-Tags` genannt) schließen.

Öffnet diesen Code im Browser und ihr werdet den Text `Mein Titel!`, nur ziemlich groß und fett sehen.


Damit dies nicht ganz so wuchtig wirkt, können wir die Anweisung natürlich auch auf einer Zeile halten

```php
<h1><?php echo 'Mein Titel!'; ?></h1>
```

Die Ausgabe ist dieselbe.


PHP hat noch eine weitere Schreibweise, von der wir im weiteren Verlauf intensiven Gebrauch machen werden, die sogenannte `Short-Syntax`.

```php
<h1><?='Mein Titel'?></h1>
```

Hier sparen wir uns das `echo` vollständig, anstelle des `php` schreiben wir ein Gleich-Zeichen (`=`), was dem PHP Interpreter mitteilt, dass hier direkt eine Ausgabe zu tätigen ist.


Aber das ist natürlich nicht alles, was wir mit PHP machen können, oder?

Natürlich nicht.

# Variablen
Bleibt ruhig in eurer `hello-world.php` oder erstellt euch ein paar neue Dateien, es ist Sinn der Sache, dass ihr rumspielt und damit warm werdet.

In PHP gibt es, wie in so ziemlich jeder anderen Programmiersprache, die sogenannte **Variable**.

Wer jetzt an `f(x)=y` denken muss, wird womöglich kotzen: Genau darum geht es hier.

Zugegeben, ich kann sehr gut mit Variablen hantieren, bin aber eine Niete in Mathe, macht euch also nicht gleich ins Hemd.



#### Was ist eine Variable?
Fangen wir doch damit an. Was stellt so eine Variable eigentlich dar? Wozu ist sie gut?

Variablen sind ein Faulheitskonstrukt (Wenn man so anfängt, könnte man die gesamte Programmierung als Faulheitskonstrukt bezeichnen, aber naja...).

Damit man einen Wert nicht immer wieder schreiben muss, nimmt man eine Schachtel, klebt einen Zettel mit einem Namen drauf, schmeißt den Wert hinein und legt quasi überall nur noch den Namen der Schachtel als Zettel mit der Notiz "Hol's dir doch selbst!" hin.

So in der Art.

Im Grunde ist eine Variable eben einfach nur eine Schachtel mit einem Namen und einem Deckel. Der Deckel kann zwar geöffnet werden, aber solange man es nicht tut, weiß man eben nicht, welcher Wert in der Schachtel steckt. Man geht aber davon aus, dass man damit arbeiten kann.

Sie nennt sich Variable, weil der Wert eben variabel ist. Er kann `5` sein, `14`, `42.42` oder eben `'Hallo Welt!'`. Und sogar noch ein paar andere Dinge, aber das lernen wir weiter unten.

#### Definition
Eine Variable in PHP definiert sich wie folgt:

```php
<?php

$variablenName = 'Variablenwert';
```

Das Dollar (`$`)-Zeichen wurde in PHP als Einleitung für eine Variable verwendet. Seht ihr ein Dollarzeichen (`$`), handelt es sich um eine Variable.
Als Name darf alles verwendet werden, was nicht mit einer Zahl anfängt (Danach dürfen gerne Zahlen enthalten sein) und ansonsten nur die Zeichen A-Z, a-z, 0-9 und _ enthalten.

In der Regel schreibt man seine Variablen im sogenannten `Camel Case` mit dem ersten Buchstaben klein. Belasst es auch dabei, denn es hilft anderen Entwicklern, mit euch zusammen zu arbeiten.


Unsere Schachtel heißt hier also `variablenName` und als Wert hat sie den String `Variablenwert`.

Diesen könnten wir nun ausgeben, nämlich, wie oben schon, mit `echo`.

```php
echo $variablenName;
```

Ruft es im Browser auf, als Ausgabe dürfte `Variablenwert` erscheinen.

In der Kurzform lässt sich natürlich auch eine Variable nutzen.

```php
<h1><?=$variablenName?></h1>
```


Variablen können auch Zahlen als Werte haben. Für Zahlen sind keine Anführungszeichen notwendig.
Es gibt zwei Arten von Zahlen in PHP
- Den **Integer** (merken!!), kurz auch gerne **int** genannt und bedeutet **Ganzzahl**. Und genau das ist sie auch. 1, 2, 3, 56, 2456, 35267357, alles Ganzzahlen.
- Die **Floats** (!merken!!), kurz auch gerne **float** genannt und bedeutet **Fließzahl, Gleitkommazahl**. Und genau das sind sie! Diese werden allerdings anders als im Deutschen in der englischen Schreibweise notiert und mit einem `.` (Punkt) statt einem `,` (Komma) getrennt. Fängt die Zahl mit `0.` an, kann die `0` weggelassen werden. Dies könnt ihr tun, müsst ihr aber nicht.

So sieht das ganze dann aus:
```php

$someInteger = 45;

$someFloat = 45.314;

$someOtherFloat = .5; //Dasselbe wie 0.5
```


Natürlich machen Variablen an diesem Punkt noch wenig Sinn, aber ich zeige euch vorab ein Beispiel, an dem sie sehr wohl Sinn machen:


Die Firma Buntdruck KG hat eine Website.

```php
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Homepage | Buntdruck KG</title>

	</head>
	<body>

		<h1>Willkommen bei der Buntdruck KG</h1>
		<p>
			Wir von der Buntdruck KG sind ein Unternehmen mit viel Bla Bla Bla
		</p>

	</body>
</html>
```

Nun hat der Geschäftsführer entschieden: Buntdruck zieht nicht. Wir nennen uns nun `VintagePrint`. Außerdem gab es ein paar Zukäuft und aus dem Unternehmen wird statt einer KG eine `SE`.

Ihr armen, nicht-variablen-nutzenden Menschen dürftet nun über ein HTML-Dokument gehen, dass natürlich mit der Größe meines hierüber absolut ins Lächerliche gezogen wird. Am meisten Schadenfreude empfinde ich dabei, wenn es ein System aus Hunderten, ja im besten Falle Tausenden HTML-Seiten ist und `Buntdruck` auch hier und da in der Schreibweise variiert (`Bunt Druck`, `BuntDruck`, `Butndruck` (Typos können mal passieren?)))


Basteln wir das ganze mal in richtigen Hacker-Kram um!

```php
<?php

$siteName = 'Buntdruck KG';

?>
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Homepage | <?=$siteName?></title>

	</head>
	<body>

		<h1>Willkommen bei der <?=$siteName?></h1>
		<p>
			Wir von der <?=$siteName?> sind ein Unternehmen mit viel Bla Bla Bla
		</p>

	</body>
</html>
```

Jetzt können wir den Geschäftsführer in Ruhe auslachen, ihm "Gib uns eine Woche!" sagen, den Wert der Variablen von `Buntdruck KG` auf `Vintage SE` ändern und den Rest der Woche zocken.


#### Benennung
Bennennt eure Variablen sinnvoll.

Üblicherweise haben eure IDEs sogenannte Auto-Completion (Auto-Vervollständigung), d.h. ihr gebt _so oder so_ nur 4-5 Buchstaben eurer Variable ein und drückt danach Enter. Völlig egal, ob die Variable nun 10 Zeichen oder 80 Zeichen lang ist.

Die Variable sollte den Inhalt sinnvoll beschreiben.

Ein Variablenname wie `$string` ist meist nicht sinnvoll, denn es sagt nicht was, was für eine Art von String. So was wie `$pageTitle`, `$databasePassword`, `$metaKeywords` oder im Notfall auch einfach mal `$stringThatNeedsToBeCutByComma`, solange es euch umfangreich beschreibt, worum es geht, ist es besser als Dinge wie `$str`, `$pt`, `$x` und `$i`. Letztere dürft ihr gerne als Zählervariablen verwenden, dazu später.

Vermeidet weiterhin, den Variablen ein Typ-Prefix zu verpassen. Variablennamen wie `$strPageTitle`, `$numPageVisits` oder `$intTimeInteral` wiedersprechen absolut der **bewussten** Typen-Freiheit von PHP und mit PHP7 gibt es richtige Typen, womit jeder, der diese Art von Variablen bisher genutzt hat, seinen gesamten Code neu schreiben darf.


# Kommentare
Wollt ihr in eurem Code etwas nicht ausführen, sondern nur einen Hinweis für andere Leute hinterlassen, könnt ihr einen Kommentar nutzen.

Kommentare in PHP werden grundsätzlich mit `//` für einen Kommentar auf einer Zeile und mit `/*` und `*/` für Kommentare auf mehreren Zeilen genutzt.

Ein Beispiel:
```php

echo $siteName; //Hier wird $siteName ausgegeben


/* Hier kann jetzt eine
ellenlange Beschreibung der Dinge stehen
die darunter vor sich gehen. */
echo $somethingElse;
```


# Verknüpfung/Verkettung (Concatenation)
Unter Verknüpfung, oder auch Concatenation, versteht man das Zusammenführen zweier Strings oder auch eines Strings und einer Zahl.

Nehmen folgendes Beispiel: Ihr habt einen Zusammenschluss aus Address-Daten in Variablen und wollt daraus eine, zusammenhängende Addresse machen
```php

$street = 'Force Street';
$number = 45;
$postalCode = '23455';
$city = 'Demacia';
```

Der `.`, ein normaler Punkt, stellt das Zeichen zur Verkettung dar.
```php
$fullStreet = $street.' '.$number;  //'Force Street 45'
$location = $postalCode.' '.$city;  //'23455 Demacia'

$address = $fullStreet.', '.$location; //'Force Street 45, 23455 Demacia'
```

Wir können so viele Elemente aneinanderketten, wie wir möchten, aber ab einem gewissen Punkt wird es gerne unübersichtlich.

Um das zu umgehen, gibt es neben der Concatenation noch ein weiteres Konstrukt.

# Interpolation
Ich würde ja jetzt einen einfacheren, deutschen Begriff wählen, aber Interpolation ist deutsch.

Es klingt wie irgend etwas krasses, dass normalerweise nur Wissenschaftler tun, es ist im Endeffekt nichts weiteres als eine andere Form der Verkettung (Concatenation).


Strings in PHP lassen sich entweder mit einfachen Anführungszeichen (`'`) oder doppelten Anführungszeichen (`"`) verwenden.

Nutzt man doppelte Anführungszeichen, erhält man auf Kosten eines kleinen, weiteren Scans eine neue Funktion: Die Interpolation.

Diese sieht, mit unserem Beispiel oben, folgendermaßen aus.
```php
$fullStreet = "$street $number";  //'Force Street 45'
$location = "$postalCode $city";  //'23455 Demacia'

$address = "$fullStreet, $location"; //'Force Street 45, 23455 Demacia'
```

Das sieht etwas angenehmer aus, oder? Juhuu, ein komplexer Begriff für eine so einfache Funktion. So ist das generell in der Programmierung und deshalb haben viele Leute Angst davor.

Sobald die doppelten Anführungszeichen verwendet werden, könnt ihr eine Variable einfach so _in den String hinein_ schreiben und im Hintergrund wird automatisch _interpoliert_ und der Wert daraus gemacht.

Beide Stile, sowohl die Concatenation als auch die Interpolation, werden grundsätzlich beide rege genutzt. Viele meiden die Interpolation, gerade aufgrund von Performance-Gründen, ich sage euch: Nutzt sie.
Sie macht euren Code übersichtlicher und die Performance, die ihr gewinnt, wenn ihr es nicht tut sind vielleicht 1 Sekunde Zeit im Jahr, die euer Server sich mehr langweilt (Wenn überhaupt).


# Arithmetik
Die meisten PHP-Statements sind Ausdrücke (Expressions), die etwas berechnen und einen Ergebnis-Wert erhalten. Wir können an diesen Punkten normale, Arithmetik, also Grundschulrechnen, anwenden.

Wir nutzen hier nun `$x` als Variablennamen, um schön bei unserer Schulmathematik zu bleiben und euch etwas zu quälen. Ihr dürft alternativ gerne etwas anderes wählen.

Ein Beispiel:
```php
<?php

$x = 1 + 5;

echo $x;
```

Die Ausgabe dieses Programms wird `6` sein. Warum? Na 1 und 5 addiert sind 6.

Neben der Addition sind natürlich sämtliche Grundrechenarten möglich.

```php

$x = 4 - 2; //$x ist 2, Subtraktion

$x = 4 * 3; //$x ist 12, Multiplikation

$x = 6 / 2; //$x ist 3, Division
```

In der Programmierung zählt, wie in unserer Mathematik auch: Punkt geht vor Strichrechnung.

Um dies an manchen notwendigen Punkten zu unterbinden, können wir, wie in unserer Mathematik auch, Klammern nutzen.

```php

$x = 4 - 2 * 3;		//$x ist -2
$x = (4 - 2) * 3;	//$x ist 6
```

Dies lässt sich natürlich beliebig tief verschachteln

```php

$x = (((12 - 4) * 2) + 13) / 5;
```


Ihr könnt beliebig Variablen mit einbringen, um eure Rechenaufgaben zu erleichtern. Beim Anpassen der Variablen könnt ihr so völlig dynamische Ergebnisse erhalten.


```php

$x = 4;

$square = $x * $x; //$x ist 16
```

Ändern wir `$x` in diesem Code-Beispiel auf `5`, wird `$square` `25` enthalten. Denn 5 * 5 sind 25.


Natürlich wollen wir aber nicht jedes mal unseren Code anpassen, um eine andere Zahl zu erhalten.

Aber auch dafür gibt es eine Lösung.

# Funktionen
Variablen sind ja schon ein wunderschönes Konstrukt, aber so richtige Dynamik kriegt man damit halt doch noch nicht rein, man schreibt immer noch genau so viel HTML und Mathematik ist nicht der Grund, warum wir PHP lernen.

Nun folgt der `f(x)=y`-Part, die Sauerstoffmasken befinden sich über Ihren Sitzen.


Eine Funktion ist grob beschrieben eine Möglichkeit, ein-und-denselben Code immer wieder zu verwenden. Habt keine Angst, es ist halb so wild, wie ihr denkt. Aber was ihr werdet, ist danach eure Mathematik besser verstehen!

Nehmen wir mal unser `square`-Beispiel von oben und basteln eine Funktion, die uns das Quadrat aus einer Zahl bildet.

Eine Funktion definiert sich wie folgt:
```php
<?php

function square($x)
{

	return $x * $x;
}
```

Ob nun die geschweiften Klammern in die nächste Zeile sollen oder nicht, bleibt generell erst mal euch überlassen, macht euch aber auf Diskussionen und Kriege gefasst, denn es ist eins der heiligen Themen in der Entwickler-Welt. Wir entwickeln PHP, mit PHP folgendem wir PSR-2, dem Coding Guide für PHP und dieser setzt sie in die nächste Zeile. Ende der Geschichte. Ich musste mich auch mit ächzen und würgen dran gewöhnen, heute nehme ich es gar nicht mehr wahr.

Dann legen wir mal los:
- Das `function` sagt PHP "Hey, jetzt kommt eine Funktion!"
- Das `square` definiert den Namen der Funktion. Dieser ist frei wählbar, solange er nicht einer der Namen ist, die PHP bereits für ihre eigenen Funktionen verwendet. Gebt ihm den Namen, führt es aus, meckert er, wählt einen anderen.
- Die Klammern `()` sagen PHP "Ey, das hier sind die Parameter für die Funktion"
- Dahinter folgt eine Liste von `,`-getrennten Variablen, in unserem Fall nur `$x` (Wir definieren noch mehr, keine Sorge!)
- Die `{}` Klammern (Erreichbar unter ALT-GR+7 und ALT-GR+0, gewöhnt euch schonmal dran!) sagen PHP "Hey, das hier ist ein Code Block für die Funktion". Der Code-Block definiert hier die Anweisungen, die ausgeführt werden sollen, sobald die Funktion aufgerufen wird.
- Das `return` sagt PHP: "Wenn ich an diesen Punkt komme, beende den Funktionsaufruf und gebe was auch immer hinter mir steht zurück". In diesem Fall wäre das "was auch immer" das Ergebnis von `$x * $x`, also das Quadrat.


Führen wir diesen Code aus, passiert erst mal nichts. Wir haben die Funktion lediglich definiert, aber noch nicht aufgerufen.

Aufrufen können wir diese ab dem Zeitpunkt der Definition wie folgt:


```php

$result = square(5);

```

`$result` würde nun den Wert des `return`-Statements innerhalb der Funktion erhalten.

Schauen wir uns mal an, was genau passiert:
- `square(5)` ruft die Funktion `square` mit dem Parameter `5` auf. Der erste Parameter ist innerhalb der Funktion als `$x` deklariert.
- Da `5` der erste Parameter ist, wird `$x` innerhalb der Funktion auf `5` gesetzt.
- Das `return` der Funktion gibt das Quadrat aus `$x` wieder, also `5 * 5`
- `$result =` fängt den Wert der Funktion auf und erhält, was auch immer `return` deklariert hat, in diesem Fall `25`

Wir können dies natürlich auch mit `echo` oder mit unserer Short-Syntax verknüpfen

```php
<?php echo square(4); ?> //gibt 16 aus

<?=square(3)?> //gibt 9 aus
```

Wie man schon sehen kann, brauchen wir `$x * $x` also von nun an nie wieder schreiben, wir können einfach bestimmte Werte an unsere `$square`-Funktion übergeben.

```php

echo square(1); //1
echo square(2); //4
echo square(3); //9
echo square(4); //16
echo square(5); //25
//usw.
```

Natürlich könnten wir auch eine Variable übergeben, sofern wir diese besitzen

```php

$x = 7;

echo square($x); //49
```

Beachtet dabei, dass das `$x` außerhalb der Funktion und das `$x` innerhalb der Funktion sich nicht überschneiden. Eine Funktion hat in PHP ihren eigenen Variablen-Bereich, das sogenannte `Scope`. Auf Scopes werde ich im Laufe dieses Artikels glaube ich nicht mehr eingehen, aber ihr dürft es gerne googeln und euch anschauen.

Wollt ihr Variablen an eine Funktion übergeben, müsst ihr alle übergeben, die ihr innerhalb der Funktion benötigt.

Bauen wir als Beispiel eine Funktion, die unser Copyright unten im Footer ausgibt

```php

function print_copyright($year, $name)
{

	return "(c) $year - $name";
}
```

Diese Funktion hat 2 Parameter, nämlich `$year` und `$name`. Diese werden mit einem `,` (Komma) getrennt.

Um diese Funktion aufzurufen, müssen wir die Parameter in der korrekten Reihenfolge übergeben.


```php

<footer class="footer footer-main">
	<div class="copyright">

		<?=print_copyright(2016, 'Lux Lilliput')?>

	</div>
</footer>
```

Wer will, kann selbst die gesamte Ausgabe mit in die Funktion einfassen. Die PHP-Tags lassen sich einfach mittendrin beenden und wieder einführen.

```php

function print_footer($copyrightYear, $copyrightName)
{
	?>
	<footer class="footer footer-main">
		<div class="copyright">

			(c) <?=$copyrightYear?> - <?=$copyrightName?>

		</div>
	</footer>
	<?php
}
```

Aufrufen ließe sie sich wie folgt

```php

print_footer(2016, 'Diana Dillknödel');
```

Was hier interessant zu beobachten ist, ist dass wir kein `return`-Statement verwendet haben. Dieses ist nicht immer erforderlich, zum Beispiel wenn unsere Funktion lediglich eine Ausgabe tätigt, aber nichts für uns fassbares berechnet.

Aus demselben Grund fangen wir den Rückgabewert von `print_footer` auch nicht auf, wir rufen einfach die Funktion auf.

Das sollte als kleine Einführung in PHP-Funktionen genügen.


# PHP Funktionen
Ihr habt nun gelernt, wie ihr eigene Funktionen deklarieren und benutzen könnt.

Natürlich müsst ihr euch aber nicht eure gesamte Basis aus den Fingern saugen.

PHP bringt eine riesige Sammlung an Funktionen und Hilfsmitteln für den Alltag mit.

Auf einige, wenige werden wir hier eingehen. Alle anderen könnt ihr inklusive einer groben Übersicht auf folgender Seite finden: [http://de.php.net/manual/de/funcref.php](http://de.php.net/manual/de/funcref.php). Speichert euch diese Seite als Bookmark. Schreibt euch die URL auf einen Zettel und legt ihn euch unter das Kopfkissen, damit ihr immer wisst, wen ihr fragen müsst, wenn ihr Hilfe braucht.

Lest nicht nur die Code-Beispiele in der PHP-Dokumentation. Die Kommentare von Benutzern unten geben oft und gerne weiteren Aufschluss über die Funktionsweise einer Funktion oder teilen euch wichtige Fettnäpfchen mit, in die ihr definitiv laufen werdet.

Wir schauen uns jetzt noch ein paar wichtige Paradigmen an, die ihr euch merken solltet. Danach greifen wir ein paar PHP-Funktionen an und schauen, wir wir sie intelligent nutzen können.


# Directory Index
Damit ihr nicht jedes mal `http://localhost/learning-php/was-auch-immer.php` aufrufen müsst, ein kleiner Exkurs.

Jeder Webserver besitzt einen sogenannten `Directory Index`. Die Dateinamen, die in diesem Directory Index definiert sind, werden standardmässig gesucht, wenn ihr einen Ordner über euren Browser aufruft.

Ihr könnt also statt `http://localhost/learning-php` aufrufen und der Webserver sieht, dass es sich um einen Ordner handelt, sucht automatisch eine Datei mit einem Namen, die im Directory Index enthalten ist und führt diese aus, falls vorhanden. Ist sie nicht vorhanden, erscheint der Inhalt des Ordners als Übersicht oder einfach nur eine 404 - Not found Fehlermeldung.


Standardmässig gibt es einen Directory Index namens `index.php`

Merkt ihr, worauf dies hinausläuft? Ich sage es euch:

Eure erste Datei, euer Einstiegspunkt, der Kern eurer Applikation, sollte immer eine Datei namens `index.php` sein.

Dies ist die erste Seite, die auch aufgerufen wird, wenn ein Benutzer z.B. `http://deine-geile-domain.com` aufruft. Umgesetzt wird es automatisch in `http://deine-geile-domain.com/index.php`.

Das erspart euch nervige Dateinamens- und Erweiterungsorgien für eure Nutzer.


Nun aber auf zu dem geilen Stuff.


# Der PHP Include
Die Funktion, die wir uns als erstes angucken möchten, ist `include`. Include heißt, wer hätte es gedacht, inkludieren, einschließen, mitnehmen.

Die `include`-Funktion ist in der Lage, eine weitere PHP Datei an der Stelle zu laden, an der ihr sie aufruft. Dies gibt uns für euch bisher noch ungeahnte Möglichkeiten zur dynamischen Erstellung von Websites.

Ihr könnt sie euch etwas wie klassisches Copy-and-Paste vorstellen: An der Stelle, an der ihr `include` aufruft, öffnet PHP die angegebene Datei, drückt einmal STRG+A und STRG+C um den gesamten Inhalt zu kopieren und drückt dann direkt an der Stelle des Includes STRG+V, um den Inhalt dort hinein zu verfrachten. Der Vorteil dabei ist: _Ihr_ müsst nicht STRG+A, STRG+C und STRG+V drücken.

Als Beispiel müssen wir nun leider etwas größere Geschütze auffahren.

Wir plustern nun unsere Projektstruktur etwas auf. Dies ist auch der Punkt, an dem ihr euren Ordner in Sublime-Text als "Ordner" öffnen solltet oder gar PHPStorm/Netbeans/w/e startet und ein neues Projekt erstellt.


Als Basis nehmen wir jetzt den Ordner `C:\xampp\htdocs\my-website`, mappt das für euch im Kopf um, wenn ihr ihn anders genannt habt.

`C:\xampp\htdocs\my-website` sollte folgende Struktur besitzen (Alle Dateien sind noch leer, aber erstellt sie ruhig schon mal).

Die folgende Projektstruktur werden wir jetzt in den kommenden Parts und sogar Artikeln erweitern. Auch weitere PHP Tutorials werden an dieser Struktur ansetzen und euch nach und nach zeigen, wie ihr aus einem Anfänger-Script eine vollwertige Web-Applikation zaubert.

Worauf ihr euch schon freuen dürft:
- Datenbank-Verarbeitung (MySQL)
- Formularübermittlung und -verarbeitung
- Sicherheit im Web
- Und mehr, fällt mir gerade nicht ein.

Ich habe hier nun mit kleinen Texten neben den Ordnern und Dateien etwas erklärt, wofür diese da sind


```
/index.php 					//Der Haupteinstiegspunkt unserer Seite		
/about-us.php 				//Eine Unterseite unserer Seite				
/includes 					//Ein Ordner für Unter-Teile unserer Seite
	/top.php 				//Der obere Teil bis zum <body> unseres HTML-Grundgerüsts
	/header.php 			//Der Kopf unserer Seite
	/navigation.php 		//Das Hauptmenü der Seite
	/footer.php 			//Der Fuß mit Copyright
	/bottom.php 			//Scripts und das abschließende Grundgerüst
```

Wir halten es noch klein. Wenn es hier für euch unübersichtlich wird, schaut euch eine klassische PHP Applikation und fragt euch, ob ihr das wirklich wollt. Ich verspreche euch: Ihr werdet es nicht bereuen.

Nun unser Plan.

Unser Plan ist es, unsere beiden Hauptseiten, nämlich `index.php`, was unsere Startseite darstellt, sowie `about-us.php`, was unsere "About us"-Seite darstellt, so klein wie möglich zu halten und Inhalte auszulagern, die sich wiederholen.

Um dies zu verdeutlichen, ein klassischer Aufbau ohne PHP würde so aussehen:
```
/index.html
/about-us.html
```

Sieht einfacher aus, oder? Ja, tut es. Bis aus den 2 Seiten 8 wurden und euer Chef euch bittet, dass "About us" jetzt in "Firmenprofil" umbenannt werden soll. Ihr dürft also in alle 8 Dateien gehen, die Navigation modifizieren, die Texte auf der Seite modifizieren und müsst drauf achten, dass die Navigation z.B. dieselben Inhalte pro HTML Datei beibehält, damit die Seite nicht _ruckelt_, wenn man navigiert.

Noch lustiger wird es dann für euch, wenn die Halbwertszeit des Webs mal wieder rum ist und ein Re-Design ansteht (Im Durchschnitt so alle 2-3 Jahre).

Ich zeige euch, wie ihr pro Änderung nur noch genau eine, einzige Datei anfassen müsst.


Als erstes definieren wir einmal die gesamte Seite und dazu die einzelnen Teilbereiche, aus denen diese bestehen soll. Dazu denken wir uns eine fiktive Firma aus, in der ihr arbeitet: **Die Noobsoft GbR**.



Das Grundgerüst:
```html
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Noobsoft - Spaghetticode for your customers</title>

	</head>
	<body>

		<main>
			<header>
				<a href="index.php">
					<img src="images/logo.png">
				</a>


				<nav class="main-nav">
					<ul>
						<li><a href="index.php">Startseite</a></li>
						<li><a href="about-us.php">Über uns</a></li>
						<li><a href="impressum.php">Impressum</a></li>
					</ul>
				</nav>
			</header>

			<section class="content">

				<!-- Hier soll unser Seiteninhalt rein -->

			</section>

			<footer>
				<div class="copyright">
					© 2016 by Timo Trötenrotz
				</div>
			</footer>
		</main>

	</body>
</html>
```

Lasst es einen Moment auf euch wirken, ich erkläre euch die Struktur.

- Alles bis zum `<body>` hin runter sollte klar sein. Wenn nicht -> HTML für Noobs lesen. Jetzt.
- Als erstes haben wir ein alles-umgebendes `<main>`-element, dass uns zur (virtuellen) Positionierung hilft (Vollständigkeitshalber)
- Das `<main>` Element hat 3 Hauptkinder, einen `<header>`, der unseren Kopf darstellt, einen `<footer>`, der den Fuß darstellt sowie eine `<section>`, die unseren Haupt-Inhalt darstellt
- Das `<header>` Element hat 2 Kinder, nämlich einmal einen Anker mit Bild drin für unser Logo sowie `<nav>`, was unser Hauptmenü der Seite darstellt. Die Links darin verlinken auf unsere Hauptseiten.
- Das `<footer>` Element enthält unser Copyright für später.
- Das `<section>` Element enthält unseren Inhalt, der für die Seite relevant ist.


Wichtig ist, dass ihr euch nun einen Punkt verinnerlicht:

Wechselt man von `index.php` auf `about-us.php`, ist exakt dasselbe HTML benötigt (Die Seite soll ja gleich aussehen). Der einzige Teil, der sich ändern wird, ist der Teil zwischen `<section>` und `</section>`.

Wie also sorgen wir dafür, dass wir nur diesen Teil dynamisch laden müssen?

Wie teilen unser Dokument erst mal in kleinere Teile auf, die wir allein festhalten können. Manche davon ändern sich regelmässig, manche nicht. Wir bauen es von oben nach unten wieder zusammen.

Legen wir los.

Als erstes wäre da `top`.

**includes/top.php**
```html
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Noobsoft - Spaghetticode for your customers</title>

	</head>
	<body>
```

Dieses Element müssen wir relativ selten ändern. Es schließt grundsätzlich die HTML-Definition, das gesamten `<head>` Element sowie den Start unseres `<body>`-elements. Der `<head>` Tag wird unseren Stylesheet beinhalten. Den Titel werden wir später noch dynamisch machen. Ich habe bewusst den `<body>` Tag alleine mitgenommen, damit wir keine extra `body-open.php` und `body-close.php`-Dateien brauchen, das würde den Rahmen hier sprengen.


Der zweitere Teil wäre unser `header`.

**includes/header.php**
```html
		<main>
			<header>
				<a href="index.php">
					<img src="images/logo.png">
				</a>


				<!-- Navigation? -->
			</header>

			<section class="content">
```

Die Navigation wurde bewusst entfernt, diese wollen wir ebenfalls auslagern. Der Header ändert sich vergleichsweise oft, wird doch im Header oft noch eine Form von Werbung gefahren, wie z.B. ein klassischer Banner mit aktuellen Produkten. Ich habe das öffnende `<section>` Element mit eingeschlossen, damit wir es immer wieder schreiben müssen. Bedenkt, wir wollen nur den _Inhalt_ des `<section>`-elements auslagern, nicht das Element selbst.


Der dritte Teil wäre demnach unsere `navigation`.

**includes/navigation.php**
```html
				<nav class="main-nav">
					<ul>
						<li><a href="index.php">Startseite</a></li>
						<li><a href="about-us.php">Über uns</a></li>
						<li><a href="impressum.php">Impressum</a></li>
					</ul>
				</nav>
```

Dieser Teil wird sich ebenfalls relativ oft, völlig unabhängig ändern. Wir fügen Seiten hinzu, wir entfernen wieder welche, manchmal fahren wir besondere Aktionen mit Zusatzseiten.


Nun neigen wir uns wieder dem Ende zu. Der nächste Teil ist der `footer`.

**includes/footer.php**
```html

			</section>

			<footer>
				<div class="copyright">
					© 2016 by Timo Trötenrotz
				</div>
			</footer>
		</main>
```

Wie sich sehen lässt, kommt hier unser `<section>`-element wieder zu seinem Schluss. Unser Inhalt muss sich also immer zwischen `header` und `footer` abspielen. Auch das `<main>` Element findet hier wieder sein verlorenes Schluss-Element.


Als letzten Teil lagern wir das Ende des Dokuments `bottom` aus.

**includes/bottom.php**
```html


	</body>
</html>
```

Dies mag für euch unnütz erscheinen, allerdings schreibt man seine JavaScripts grundsätzlich vor das schließenden `</body>` Element um das Rendering nicht zu blocken. Glaubt mir an diesem Punkt einfach, dass ihr mir irgendwann dafür danken werdet.


Diese Einzel-Elemente könnt ihr nun allesamt in die dafür vorgesehenen Dateien in `C:\xampp\htdocs\my-website\includes` ablegen. Erweitert sie ruhig, bastelt sie etwas um, macht sie euch schick.


**Aber wie machen wir daraus nun wieder eine Seite?**

Und genau hier kommt unser Freund, der PHP Include, zum tragen.

Schreiben wir nun erst mal ein Beispiel unserer `index.php`-Datei, also unserer Startseite, und gucken uns das Ergebnis an.

**index.php**
```php
<?php
include 'includes/top.php';
include 'includes/header.php';
?>

<h1>Willkommen bei Noobsoft!</h1>
<p>
	Wir machen geile Sachen. Kauft uns.
</p>

<?php
include 'includes/footer.php';
include 'includes/bottom.php';
?>
```

Ruft das ganze im Browser einmal auf und schaut es euch an.

Das erste, was euch auffallen wird, ist dass die Navigation nicht da ist. Dazu später. Als zweites werdet ihr aber sehen, dass die Seite ansonsten zusammengefügt wurde (Sofern ihr die Inhalte in die korrekten Dateien geschrieben habt).

Wie genau der Befehl `include` arbeitet, habe ich euch ja oben schon erklärt, nur die Syntax nicht.

Es beginnt immer mit `include` und der Dateipfad, der danach folgt, ist der Pfad zu der Datei, die ihr an diesem Punkt einfügen möchtet.


Bringen wir nun dazu noch unser Menü rein. Dieses wird nicht in unseren Hauptseiten geladen, sondern in `includes/header.php`, denn die Navigation ist ein Unterelement des Headers.

Wir ändern `includes/header.php` also wie folgt ab:

**includes/header.php**
```php
		<main>
			<header>
				<a href="index.php">
					<img src="images/logo.png">
				</a>


				<?php include 'includes/navigation.php'; ?>
			</header>

			<section class="content">
```

#### Include Path
Ein Punkt sollte euch nun vielleicht oder vielleicht auch nicht auffallen: Obwohl die Datei `header.php` im `includes`-Ordner liegt, müssen wir `includes/navigation.php` und nicht einfach nur `navigation.php` laden. Wieso?

PHP besitzt zur Ausführungzeit eines Scripts einen sogenannten **Include Path**. Dies ist eine Sammlung von Pfaden, aus denen PHP Dateien läd. Ihr könnt euch diese Pfade mit `echo get_include_path();` ausgeben lassen.

Der Einstiegspunkt unserer Applikation ist nach wie vor die `index.php` und der Pfad selbiger ist derjenige, der im Include Path landet. Dies wird auch zur gesamten Ausführung des Scripts der Fall sein.

Um den Pfad zu fixieren und nicht auf unschöne Überraschungen zu treffen, solltet ihr die Konstante `__DIR__` nutzen, die in jeder PHP Datei verfügbar ist.

#### Konstanten
Konstanten sind nicht anders als Variablen, mit dem Unterschied, dass sie nicht variabel sind, sie sind konstant (Wer hätte das gedacht!). Bedeuten tut das, ihr definiert eine Konstante genau einmal und danach kann sie nie wieder geändert werden. Dies macht an vielen Punkten Sinn und diese Punkte werdet ihr auch noch entdecken, dazu später mehr.

In jeder PHP-Datei habt ihr Standardmässig folgende Konstanten zur Verfügung:
- `__DIR__` ist das Verzeichnis, in dem sich die aktuelle PHP Datei befindet (Die, in der ihr in dem Moment schreibt, in dem ihr `__DIR__` oder sonstige `__*__`-Konstanten nutzt!)
- `__FILE__` ist der Pfad zur aktuellen PHP Datei
- `__FUNCTION__` ist der Name der Funktion, in der ihr euch befindet

Es gibt noch weitere, aber auf diese möchte ich an diesem Punkt einfach nicht eingehen. Das machen wir später dann in OOP for Noobs.

Verwenden können wir also einen Pfad, der von der aktuellen PHP Datei ausgeht. Dies würde in der `includes/header.php` folgendermaßen aussehen:

**includes/header.php**
```php
		<main>
			<header>
				<a href="index.php">
					<img src="images/logo.png">
				</a>


				<?php include __DIR__.'/navigation.php'; ?>
			</header>

			<section class="content">
```

Hier verknüpfen wir einfach den Wert der Konstanten `__DIR__` (Wird in diesem Fall definitiv `C:\xampp\htdocs\my-website\includes` sein, denn es geht um den Ordner, in dem sich `header.php`, also die Datei, in der das `__DIR__` steht, befindet)


#### Der Vorteil

Warum wir das Ganze gemacht haben zeige ich euch jetzt.

Wir sollen nun also eine weitere Seite, die "About us"-Seite einpflegen. Wir kopieren also den Inhalt unserer `index.php` und ändern lediglich den Content ab.

**about-us.php**
```php
<?php
include 'includes/top.php';
include 'includes/header.php';
?>

<h1>Wir über Noobsoft</h1>
<p>
	Noobsoft wurde im Jahre 2016 von unserem Herrscher Köhn dem Erhabenen gegründet um uns armen, unwissenden in eine Welt einzuführen, die wir vorher nicht kannten!
</p>

<?php
include 'includes/footer.php';
include 'includes/bottom.php';
?>
```


**Fertig.**

Jede deutsche Website muss laut Recht über ein Impressum verfügen, also wer sind wir, dass wir uns dem Gesetz verweigern? Wir haben dieses sogar oben in der Navigation schon hinterlegt.

Wir erstellen also eine neue Datei `impressum.php`

**impressum.php**
```php
<?php
include 'includes/top.php';
include 'includes/header.php';
?>

<h1>Noobsoft Impressum</h1>
<p>
	Ein riesiger, unendlich langer Blob von Anwaltsgebrabbel dass sich kein Schwein durchliest, aber trotzdem da sein muss.
</p>

<?php
include 'includes/footer.php';
include 'includes/bottom.php';
?>
```

**Bam.**


Klar, wir könnten natürlich auch noch den Include von `top` in den `header` verlagern und den von `footer` in den `bottom`, aber dies habe ich bewusst nicht gemacht.

Diese 4 Elemente sind die, die unter einzelnen Seiten am wahrscheinlichsten wechseln können.


So könnten wir jetzt ohne weiteres auf der Startseite einen fetten, interaktiven Banner einbringen, während die anderen Seiten so verbleiben, wie sie sind, ohne großen Aufwand:
```php
<?php
include 'includes/top.php';
include 'includes/header-with-awesome-banner.php';
?>

<h1>Willkommen bei Noobsoft!</h1>
<p>
	Wir machen geile Sachen. Kauft uns. Achja, wir haben einen geilen Banner!
</p>

<?php
include 'includes/footer.php';
include 'includes/bottom.php';
?>
```

Nun könnten wir eine `includes/header-with-awesome-banner.php` anlegen und die anderen Seiten bleiben genau so, wie sie waren.

Dies funktioniert an diesem Punkt mit dem Header, dem Footer, der Navigation, sämtlichen Stylesheets und Metatags sowie sämtlichen JavaScript.

Man, sind wir geil.


# Das Ende

Das reicht.

Wir sind bei 1082 Zeilen, ich kann alleine mit Basics wahrscheinlich noch 5000 weitere füllen, also belasse ich es dabei und lasse euch rumspielen.

Für alle anderen Themen gibt es spezifische * for Noobs-Tutorials, die ihr euch anschauen könnt und weitere werden auch folgen.



Good night, good fight.

~Torben