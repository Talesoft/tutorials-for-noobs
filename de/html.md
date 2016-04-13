HTML für Noobs
=============


# Was ist HTML?
HTML steht für Hypertext Markup Language. Sinngemäß bedeutet dies, es ist eine Sprache, die aus normalem Text besteht, ihn aber aufwertet.



# Was ist Hypertext?
Ihr könnt euch das in etwa wie den Unterschied zwischen Notepad.exe und Wordpad.exe vorstellen (Windows).

Notepad.exe erzeugt beim speichern eine Text-Datei. Wir können keine Bilder, Links, Farben oder sonstige Angaben angeben. Öffnet man diese Text-Datei wieder in Notepad, erhält man wieder den normalen, lesbaren Text.

Speichern wir eine Datei in WordPad, wird nicht etwa eine .txt-Datei erzeugt, sondern eine .rtf-Datei. Hier können wir Bilder hinzufügen, Text fett und kursiv machen und Text-Farben sowie Schriftarten und Schriftgrößen ändern. RTF steht für Rich Text Format. Rich Text ist schon fast etwas wie Hypertext bzw. HTML.

Öffnet man nun eine derartige .rtf-Datei nicht etwa in WordPad, sondern in Notepad, sieht man etwas spannendes:
```rtf
{\rtf1\ansi\ansicpg1252\deff0\deflang1031{\fonttbl{\f0\fnil\fcharset0 Calibri;}}
{\colortbl ;\red255\green0\blue0;}
{\*\generator Msftedit 5.41.21.2510;}\viewkind4\uc1\pard\sa200\sl276\slmult1\cf1\lang7\f0\fs36 Torben is quite awesome!\cf0\fs22\par
}
```

Das sieht schon anders aus, als das, was uns in WordPad angezeigt wird.

Diese ganzen komischen Zeichen und Zahlen definieren nach und nach, wie der Text gestalten wird. Ich habe hier z.B. den Text "Torben is quite awesome!" in rot mit der Schriftart Calibri in der Größe 36.

Schaut genau hin und ihr könnt diese Werte erkennen, da hätten wir z.B. `colortbl ;\red255\green0\blue0` (Color Table, Rot 255, Grün 0, Blau 0) was dann wohl die Farbe für meinen roten Text ist. Weiter oben haben wir `fonttbl...fcharset0 Calibri` (Font Table, Font-Charset), was wohl meine Schriftart definiert. Unten kurz vor dem Text lösen wir `cf1` (Color Foreground 1) aus, um die erste Farbe in unserer `colortbl` zu verwenden: Rot. Dann lösen wir noch `f0` (Font 0) für unsere Schriftart aus sowie `fs36` (Font Size 36) für unsere Schrift-Größe.


Notepad kann damit nicht viel anfangen, denn Notepad kennt keine Formate, Notepad stellt alles im sogenannten "Plain Text" dar, also einfacher Text, der wahre Inhalt einer jeden Datei.

WordPad allerdings kennt das RTF-Format und bevor es eine RTF-Datei öffnet, verarbeitet es diese ganzen komischen Zeichen und Zahlen oben und sorgt dafür, dass uns am Ende einfach nur ein roter, großer Text angezeigt wird.

#### Warum erzähle ich euch das?
Als Analogie. HTML ist wie RTF, nur einfacher zu lesen und einfacher mit der Hand zu modifizieren.

Man hätte nämlich durchaus auch die Entscheidung treffen können, RTF als Hypertext-Format zu nutzen. Aber hättet ihr Lust, diese ganzen komischen Begriffe und Zeichen oben zu kennen und euch zu merken?

Deshalb hat sich jemand hingesetzt und HTML entwickelt. Nicht nur irgendjemand, es war der CERN, nämlich zur Übertragung von strukturierten, meist wissenschaftlichen Informationen (und niedlichen Katzenbildchen!).

Ganz ohne komische Zeichen kommt auch HTML nicht aus, aber diese Zeichen lassen sich leicht merken und leicht lesen.




#### Ein (doch) gewaltiger Unterschied
Es gibt eine Sache, die HTML (mittlerweile) anders macht als RTF. Denn heutzutage ist es ein No-Go, Stilinformationen im HTML zu hinterlegen (z.B. Farben, Schriftarten, Schriftgrößen).

Dies hat den einfachen Grund, dass HTML grundsätzlich als Struktur-Sprache gedacht ist, nicht als Layout-Sprache.

Dies bedeutet, dass HTML lediglich die Struktur der Daten vorgibt, quasi dem Browser mitteilt, wo sich welche Art von Daten befinden.

Den Style selbst übernimmt am Ende das CSS (Cascading Stylesheets). Dazu könnt ihr euch gerne am Ende noch CSS für Noobs durchlesen. Der Vorteil dabei ist, dass man später nur das CSS anpassen muss und man kann mit demselben HTML eine völlig neu gestaltete Seite realisieren. Man schreibt sein HTML quasi nur ein mal, die Daten sollten sich ja im Grunde nicht ändern.

Das war nicht immer so. Noch mit HTML4 war es Gang und Gebe, seine Seitenstruktur in große Tabellen zu verschachteln und Dinge wie die Hintergrundfarbe oder Schriftfarben direkt ins HTML zu schreiben. Macht das nicht. Jedes mal, wenn ihr es tut, tötet ein Ninja ein kleines Katzenbaby und lacht dabei.


# Die Aufgabe
Nehmen wir einfach mal einen Text und versuchen diesen, durch HTML schön zu strukturieren.

Erstellt doch am besten einfach jetzt auf dem Desktop eine Datei und benennt sie irgendwie. Wichtig ist, dass diese Datei am Ende die Endung `.html` enthält (Bitte seht von der Endung `.htm` ab, es ist eher eine Altlast als ein "Shortcut" und stammt FAT-Zeiten, in denen man maximal 3 Zeichen für die Endung und 8 Zeichen für den Dateinamen hatte)

Diese Datei öffnet ihr in einem Text-Editor eurer Wahl. Ihr könnt Notepade.exe nehmen, empfehlen tu ich euch Sublime Text 3 oder Notepad++

Nehmt den folgenden Text und haut ihn dort rein.


```
Die wichtigsten HTTP-Status Codes

Hier findet ihr eine Auflistung aller wichtigen HTTP Status-Codes

Code 	Status Text 	Bedeutung
200		OK				Alles gut.
404		Not Found 		Die Seite wurde nicht gefunden.
403 	Unauthorized	Du bist nicht authorisiert.
```

Unser Ziele sind folgende:
- "Die wichtigsten HTTP-Status Codes" sollte als große Überschrift dargestellt werden.
- Das "HTTP Status-Codes" sollte fett geschrieben sein, um beim überlesen des Textes schnell darauf aufmerksam zu machen, worum es sich handelt.
- Die Tabelle unten sollte sauber als Tabelle dargestellt werden. Dies ist bei Tabs immer relativ schwierig, vor allem bei dynamischen Daten.




# Das Element
In HTML dreht sich alles um sogenannte **Elemente**. Merkt euch den Begriff, ihr werdet ihn oft hören. Das Element, dass dafür sorgen würde, dass wir eine richtige Überschrift oben erhalten, sieht folgendermaßen aus:

`<h1>Die wichtigsten HTTP-Status Codes</h1>`

Es wird immer ein Element geöffnet (`<h1>`), darin landet Text oder noch weitere Elemente und am Ende wird es wieder geschlossen `</h1>`.

Das `h1` ist der Name des Elementes, im HTML nennt man diese Namen **Tags**. In diesem Fall ist `<h1></h1>` das Element, `h1` ist der Tag.

`h1` steht für "Header 1" oder auch "Überschrift erster Ordnung". Es gibt ingesamt 6 dieser `h*` Elemente, nämlich `h1`, `h2`, `h3`, `h4`, `h5`, `h6`.

Jede Zahl steht eine tiefere Rangordnung da, heißt, `h1` ist die größte, `h6` die kleinste.

```html
<h1>Die wichtigsten HTTP-Status Codes</h1>

Hier findet ihr eine Auflistung aller wichtigen HTTP Status-Codes

Code 	Status Text 	Bedeutung
200		OK				Alles gut.
404		Not Found 		Die Seite wurde nicht gefunden.
403 	Unauthorized	Du bist nicht authorisiert.
```

Dies sorgt also schonmal dafür, dass unsere Überschrift groß als Überschrift angezeigt wird. Ändert es in eurer Datei so ab und doppelklickt die Datei auf dem Desktop, sie sollte sich in eurem Standardbrowser öffnen und die Überschrift sollte vom Browser einen standardmässigen, fetten, großen Textstil erhalten.

Wohlgemerkt, im HTML sind die Anzahl der Leerzeichen, die ihr setzt, völlig egal.
Ihr könnt auch zwischen einzelne Wörter komplette Zeilenumbrüche machen, diese werden in HTML ignoriert (Mitgrund, warum auch unsere Tabelle unten nicht korrekt angezeigt würde, Tabs werden eben so ignoriert).

Lediglich die Leerzeichen zwischen Worten werden von HTML beibehalten.

`h1-h6` sind sogenannte **Block**-Elemente. Sie nehmen die gesamte Weite des Dokuments ein und erzeugen automatisch einen Zeilenumbruch. Dazu später mehr.



# HTML im Text
Mit dem `strong`-Tag können wir Text hervorheben. In der Regel bedeutet dies: Fett geschriebener Text.

Hier greift nämlich der Punkt, den ich oben versucht habe zu erklären: Einem Entwickler steht es frei, aus dem `strong`-Tag ein kursives Element oder vielleicht ein rot-geschriebenes zu machen. `strong` zu nutzen heißt nicht zwangsläufig, dass der Text fett wird, aber es ist die Standardeinstellung des Browsers und die meisten Entwickler einigen sich darauf, dass es "Fett geschriebener Text" bedeutet. `strong` sagt dem HTML nicht "Mach den Text fett geschrieben" sondern es sagt dem HTML "dieses Element ist hervorgehoben". Nichts anderes. Wie man am Ende hervorhebt, ist Sache des Designers und gehört ins CSS.

Ein **Inline**-Element wie `strong` können wir mitten im Text platzieren, wir müssen nicht die gesamte Zeile hervorheben.

```html
Hier findet ihr eine Auflistung aller wichtigen <strong>HTTP Status Codes</strong>
```



# Verschachtelung
Dies ist für viele das schwierigste Element im HTML: Elemente können Elemente enthalten.

Dies greift z.B. einerlei bei Vorraussetzungen wie: "Ich möchte einen Text fett _und_ kursiv machen".

Um dies zu realisieren, baut man einfach 2 Elemente um den Text herum.

Ich nutze hier das Element `em`. Dies steht für `emphasize` und lässig sich am besten in "betonen" übersetzen. Ein Element, dass Text-teile betont also. Äußern tut sich dies in der Regel in kursivem, also schräg-gestelltem Text.

```html
<strong><em>Hier</em></strong> findet ihr eine Auflistung aller wichtigen <strong>HTTP Status Codes</strong>
```

Das `em`-Element landet _in_ unserem `strong` element und in dem `em` Element dann wiederrum unser Text.

Ein öft begangener Fehler ist hier das Vertauschen der End-Tags.
```html
<strong><em>Hier</strong></em>
``` 

wird zwar von vielen Browsern halbwegs korrekt interpretiert, ist aber ein semantischer Fehler und das HTML wird dadurch invalide.



Viel interessanter wird Verschachtelung allerdings, wenn wir unsere Tabelle realisieren wollen.

Am einfachsten wäre euch nun wahrscheinlich eine Lösung, die so aussieht:
```html
<table>
Code 	Status Text 	Bedeutung
200		OK				Alles gut.
404		Not Found 		Die Seite wurde nicht gefunden.
403 	Unauthorized	Du bist nicht authorisiert.
</table>
```

Das `table` Element gibt es tatsächlich und ist genau jenes, welches wir benötigen.

Dies funktioniert allerdings aus folgendem Grund nicht: HTML verarbeitet nicht. HTML _macht_ nichts, es _definiert_ nur. Deshalb ist es HTML auch nicht möglich, unsere Daten dort anhand des Tabs aufzuteilen und auf Spalten zu verteilen. Was wir tun müssen, ist dem HTML mitteilen: "Dies hier ist eine Tabellen-Zeile", "Dies hier sind Tabellen-Daten, die du in Spalten anzuordnen hast"

Und genau das tun wir.

Dafür gibt es 2 Elemente:
- `tr` steht für Table Row und stellt eine Zeile in der Tabelle dar
- `td` steht für Table Data und stellt sowohl eine Spalte als auch eine Zelle dar.

Weiterhin gibt es ein Element, was wir anstelle von `td` verwenden können, aber (fast) dieselbe Funktion hat: `th` steht für Table Header und stellt eine Kopf-Zelle dar. Diese Zellen werden von Browsern standardmässig etwas fetter dargestellt und der Text wird zentriert. Testet es einfach gleich selbst und schaut es euch an.

Hier beginnt der Punkt, an dem HTML Verschachtelung komplex werden kann. Wenn euch nach dem folgenden Text die Augen tränen, seid ihr hier falsch!

```html
<table>
	<tr>
		<th>Code</th>
		<th>Status Text</th>
		<th>Bedeutung</th>
	</tr>
	<tr>
		<td>200</td>
		<td>OK</td>
		<td>Alles gut.</td>
	</tr>
	<tr>
		<td>404</td>
		<td>Not Found</td>
		<td>Die Seite wurde nicht gefunden.</td>
	</tr>
	<tr>
		<td>403</td>
		<td>Unauthorized</td>
		<td>Du bist nicht authorisiert.</td>
	</tr>
</table>
```

Wenn ihr diese Verschachtelung auf Anhieb verstanden habt: Freut euch nicht zu früh! Aber dazu später.

Was wir hier gemacht haben ist folgendes:
- Innerhalb unseres `table` Elements definieren wir insg. 4 Tabellen-Zeilen durch `tr`
- Innerhalb jeder `tr` definieren wir jeweils 3 Tabellen-Zellen und legen damit auch automatisch die Spalten fest (`td`)
- Das erste `tr`-Element enthält statt `td`-Elementen nur `th`-Elemente, um darauf hinzuweisen, dass es sich hier nicht um Daten, sondern um Spaltenüberschriften handelt.

Ich halte euch an diesem Punkt an, euch direkt eine Sache anzugewöhnen: **Achtet auf die Einrückung!**

Rückt eure Elemente sauber ein, jedes Kind-Element gehört ein Level weiter nach rechts. Rückt nicht mit Tabs ein, sondern stellt euren Editor darauf ein, Leerzeichen zu verwenden, denn diese werden auf jedem System gleich dargestellt, Tabs nicht. Leute, die mit euch zusammen an euren Projekten arbeiten, werden euch dafür auf ewig dankbar sein.

Es ist klar, dass _ihr_ euren Code meistens versteht, aber das heißt nicht, dass _jeder_ dort auf Anhieb durchsteigt, selbst erfahrene Personen müssen schlecht geschriebenes HTML erst mal auseinanderzupfen. Haltet euch an bekannte Vorgehensweisen und Standards und ihr werdet auf ewig ein glückliches Developer-Leben führen. Versprochen.

Haben wir das soweit verinnerlicht, schauen wir uns mal unser gesamtes HTML an:

```html
<h1>Die wichtigsten HTTP-Status Codes</h1>

<strong><em>Hier</em></strong> findet ihr eine Auflistung aller wichtigen <strong>HTTP Status Codes</strong>

<table>
	<tr>
		<th>Code</th>
		<th>Status Text</th>
		<th>Bedeutung</th>
	</tr>
	<tr>
		<td>200</td>
		<td>OK</td>
		<td>Alles gut.</td>
	</tr>
	<tr>
		<td>404</td>
		<td>Not Found</td>
		<td>Die Seite wurde nicht gefunden.</td>
	</tr>
	<tr>
		<td>403</td>
		<td>Unauthorized</td>
		<td>Du bist nicht authorisiert.</td>
	</tr>
</table>
```

Diesen Inhalt müsstet ihr nun in eurer Datei auf dem Desktop haben. Öffnet ihr ihn in einem Browser, seht ihr die Tabelle, sauber strukturiert.

Bastelt etwas daran rum, googelt euch Elemente zusammen und schmeißt sie einfach rein. Kaputt machen kann man mit HTML nichts. Es sieht maximal am Ende scheiße aus.

Wir schauen uns auf jeden Fall noch ein paar weitere Eigenschaften von HTML und ein paar weitere Elemente an.

Im folgenden bitte ich euch darum, die Elemente einfach mal in eure HTML-datei zu schreiben, vielleicht auch in die einzelnen Tabellen-Zellen, um ein Gefühl dafür zu kriegen, was sie machen.


# Attribute
Es gibt einige Elemente, die doppeldeutig sind.

Nehmen wir als beispiel das `input`-Element. Input steht für Eingabe und erstellt in seiner Standardform ein Texteingabefeld.

`input` ist weiterhin eines der wenigen Elemente, die nicht explizit geschlossen werden müssen, heißt, ihr braucht kein `</input>`, um das Element zu schließen. Dies ist der Fall für die Elemente `input`, `br`, `img`, `link`, `area`, `base`, `col`, `command`, `embed`, `hr`, `keygen`, `meta`, `param`, `source`, `track` und `wbr`, einfach für die Vollständigkeit. Ihr müsst euch diese nicht merken und erst mal auch nicht unbedingt wissen, was diese tun.

Schreibt nun ein Input-Element in eure Datei
```html
<input>
```

und führt diese aus.

Ihr seht ein Input-Element.


Was aber, wenn wir dieses coole Passwort-Feld haben wollen, wo die Zeichen nur als * dargestellt werden?

Dafür modifizieren wir das Element mit einem **Attribut**. Das sieht so aus:

```html
<input type="password">
```

Das `type` definiert hier den Namen des Attributs, das `=` teilt HTML mit, dass dieses Attribut einen Wert hat (Es kann bei manchen Attributen auch einfach nur der Name dort stehen) und der Wert des Attributs (Hier `password`) wird immer in doppelte Anführungsstriche gesetzt.

Es gibt eine ganze Reihe von Input-Typen und es gibt auch eine ganze Reihe an Attributen für jedes Element.

z.B. können wir Formular-Elementen wie `input` auch noch einen Namen geben, damit die übergebenen Daten beim Versenden des Formulars identifizierbar bleiben.

Als Beispiel könnten wir zwei Input-Felder für einen Login definieren

```html
<input type="text" name="username">
<input type="password" name="password">
```

Schicken wir diese Daten mit einem Formular ab, erhält die Verarbeitungsinstanz am Ende die Daten `username` und `password` mit den in die Textfelder geschriebenen Inhalten.


# Verlinkungen
Ihr wollt natürlich nicht eure gesamte Website in eine, einzige HTML-Datei quetschen. Üblicherweise hat eine Website mehrere Seiten und durch sogenannte **Links** oder auch **Anker** betritt man sie.

Klickt man einen solchen Link an, wird eine neue Abfrage gestartet und ein anderes Dokument wird ausgegeben.

Um so einen Link zu realisieren, nutzt man nicht etwa das `link`-Element, wie man annehmen könnte, sondern das `a`-Element (`a` steht in dem Fall für `anchor` und deshalb oben auch **Anker**). Warum ist etwas umfangreich zu erklären, aber die initiale Funktion das `a`-Elementes war es, innerhalb von Seiten zu navigieren, also auf einer Seite von Punkt A nach B zu springen (quasi automatisch runter scrollen, bis zu einem gewissen Punkt).

Diese Funktion ist auch heute noch realisierbar, decke ich hier nun aber nicht ab.

Wir wollen auf andere Seiten verlinken, mit eigenem Inhalt, mit richtig neu laden und neu rendern. In 100Mbit/s-Zeiten kann man sich das leisten!

Ein Link zu einer anderen Seite könnte z.B. so aussehen

```html
<a href="ueber-mich.html">Über mich</a>
```

`href` steht für `Hypertext Reference` und gibt das Ziel unseres Links an.

Schreibt es in eure Datei, erstellt daneben eine weitere Datei namens `ueber-mich.html`, schmeißt zufälligen Content dort rein und dann ruft eure Seite auf und klickt auf den Link.

Es besteht die Möglichkeit, dass euer Browser das Charset falsch erkennt und euch das `Ü` in `Über uns` als Kauderwelsch angezeigt wird. Das ist sehr gut! Denn so seid ihr bestens auf das vorbereitet, was weiter unten noch auf euch wartet.



# Das war alles?
Fast. Ihr wisst jetzt (im besten Falle) wie HTML allgemein funktioniert und was es für euch tun kann.

Wie aber sorgt ihr nun dafür, dass ihr eure HTML-Datei über eure eigene Website abrufen könnt?

Und wie sorgt man dann dafür, dass der Tab nach der eigenen Website benannt ist und nicht nach dem Dateinamen?

Wie kann man diese kleinen Icons im Tab laden?

Und wo läd man CSS und JavaScripts?


Bevor ich euch entlasse, müssen wir diese Fragen beantworten.


# Die index.html
Der Einstiegspunkt ist standardmässig **index.html**. Ruft man im Browser einen Ordner auf einem Webserver auf und dieser Ordner beinhält eine Datei namens `index.html`, wird diese automatisch als erstes ausgegeben. Wäre dies nicht so, müsstet ihr `google.de/index.html` eingeben, jedes mal, wenn ihr Google aufrufen möchtet.

Ruft ihr `google.de` auf, findet er in dem dahinterliegenden Ordner automatisch die `index.html` und gibt euch diese wieder (Sinnbildlich, Google verwendet natürlich keine HTML-Dateien sondern dynamische Prä-Prozessoren und eigene Technologien. Die Ausgabe ist aber dennoch HTML!)

Es ist also generell - und das ist das, was ich euch damit sagen möchte - am besten, wenn ihr eure erste Seite, eure Startseite, euren Einstiegspunkt, immer `index.html` nennt. Schreibt ihr PHP, nennt ihr sie `index.php`, es ist dasselbe Prinzip. Verwendet nicht die Endung `.htm`. Es reicht, dass zwei anerkannte Erweiterungen existieren, wir müssen sie nicht auch noch nach Spaß und Laune streuen. `.html` ist der Standard.


# Das Grundgerüst
Eine HTML-Datei sollte niemals einfach nur loses HTML wie oben geschrieben enthalten. Der Browser kann immer etwas damit anfangen, aber nicht jeder fängt das richtige damit an. Deshalb brauchen wir eine Möglichkeit, um dem Browser noch ein paar Informationen übergeben zu können, bevor unser Seiteninhalt kommt. Wenn ihr in der Link-Übung weiter oben Kauderwelsch beim `Ü` angezeigt bekommen habt, werdet ihr auch gleich sehen, wie ihr dies lösen könnt bzw. gar nicht erst reinlauft.

Würden wir diese Informationen nun einfach in unsere HTML-Datei schreiben, würde diese als Text angezeigt werden. Aber das wollen wir gar nicht, wir wollen dem HTML, also dem Browser, Informationen über unsere Seite geben.

Deshalb schachtelt man jedes HTML-Dokument in das sogenannte Grundgerüst.

Das Basis-Grundgerüst einer HTML-Datei sieht folgendermaßen aus:
```html
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Meine Geile Website!</title>

	</head>
	<body>

	</body>
</html>
```

Nehmen wir das ganze mal auseinander.

Da unser Browser nicht nur HTML, sondern auch XML, SVG und ähnliche Markup-Sprachen darstellen kann, müssen wir ihm mitteilen, dass es sich um HTML handelt. Das tun wir zwar schon mit einem Mime-Type, aber dieser ist derselbe für z.B. HTML4, XHTML1 und HTML5.

Früher musste man als Doctype ewig lange Strings und Namespaces angeben, heute reicht ein einfaches `<!DOCTYPE html>` (Laut Standard MUSS das `DOCTYPE` groß geschrieben werden. Dazu könnt ihr euch gerne über XML Entities und Doctypes anlesen, falls es euch interessiert, denn diese sind hier am Werk)

Als nächstes haben wir ein alles umgebendes `<html></html>` Element. Dieses sollte immer das äußerste Element bleiben. Das `html`-Element kriegt ein Attribut namens `lang` (Language) und dieses setzen wir hier auf `de` für Deutsch. Baut ihr eine englischsprachige Seite, schreibt dort `en` rein, für französisch `fr`, spanisch `es`, polnisch `pl` usw. Dies hilft z.B. Tools wie dem Google Übersetzer, die Ausgangssprache eurer Website direkt ausfindig zu machen.


Innerhalb des `html`-Elements haben wir zwei wirklich wichtige und essenzielle Elemente: `head` und `body`.

Das `head`-Element ist für sogenannte Meta-Informationen da, heißt es sind Informationen, die nicht angezeigt werden, das `head`-Element ist absolut unsichtbar. Die darin enthaltenen Elemente sind primär dazu da um den Browser ein paar wichtige Informationen mit auf den Weg zu geben.

Da wäre z.B. ein `meta`-Tag, der explizit eine Meta-Information darstellt. Vereinfachterweise hat es ein Attribut, dass wir setzen, nämlich das `charset` und zwar (in den meisten Fällen) auf `utf-8`. Dies wird dafür sorgen, dass unser Kauderwelsch-`Ü` weiter oben korrekt angezeigt wird, denn der Browser ist nun darüber informiert, wir wir unsere Zeichen kodiert haben (Mehr dazu könnt ihr euch unter Charsets und Encoding anlesen, ist ein sehr interessantes Thema). Gehe ich hier aber dazu jetzt ins Detail, sprenge ich dieses Tutorial.

Als nächstes haben wir im `head` das `title`-Element. Mit dem `title`-Element vergeben wir unserem HTML-Dokument einen Titel, der im Browser üblicherweise im Tab oben dargestellt wird. Ändert ihn und ruft es auf, dann seht ihr es.


Das `body` Element ist von nun an der Container für unseren gesamten Seiteninhalt, also alles, was wir weiter oben besprochen haben.

Jeder Text, jedes Element, jeder Link, jede Tabelle, einfach alles, was ihr auf der Seite darstellen wollt, sollte innerhalb des `body`-Elements stehen.



Verknüpfen wir also nun mal unser HTML oben mit unserem HTML Grundgerüst
```html
<!DOCTYPE html>
<html lang="de">
	<head>
		<meta charset="utf-8">
		<title>Meine Geile Website!</title>

	</head>
	<body>

		<h1>Die wichtigsten HTTP-Status Codes</h1>

		<strong><em>Hier</em></strong> findet ihr eine Auflistung aller wichtigen <strong>HTTP Status Codes</strong>

		<table>
			<tr>
				<th>Code</th>
				<th>Status Text</th>
				<th>Bedeutung</th>
			</tr>
			<tr>
				<td>200</td>
				<td>OK</td>
				<td>Alles gut.</td>
			</tr>
			<tr>
				<td>404</td>
				<td>Not Found</td>
				<td>Die Seite wurde nicht gefunden.</td>
			</tr>
			<tr>
				<td>403</td>
				<td>Unauthorized</td>
				<td>Du bist nicht authorisiert.</td>
			</tr>
		</table>

	</body>
</html>
```

Dies ist ein vollständiges, valides HTML-Dokument. So hat eine HTML-Datei auszusehen und nicht anders.


Es gibt natürlich noch eine ganze Menge weiterer Elemente, die wir hier nun erklären könnten, aber man scrollt sich jetzt schon zu Tode, also spar ich mir das für ein weiteres Tutorial auf.

Wenn ihr Lesestoff zu HTML haben wollt, bemüht Google:
- HTML Content Flow (Es wird ein Content Flow für Noobs geben)
- Inline vs. Block
- WAI-ARIA (Es wird ein WAI-ARIA für Noobs geben)
- Semantic Web (Es wird Semantic Web für Noobs geben)


Ansonsten [hier eine Liste von W3Schools](http://www.w3schools.com/tags/ref_byfunc.asp), die soweit die meisten Elemente beinhält.

Spielt einfach mal mit den Elementen rum, benutzt sie, ändert die Attribute, probiert rum, schrottet und zerstört, Learning by Doing ist der einzige Weg, ein HTML-Profi zu werden!


Good night, good fight!

~Torben