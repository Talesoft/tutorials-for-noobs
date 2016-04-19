PHP Datentypen für Noobs
=============


# Voraussetzungen
Dieses Tutorial baut auf dem Tutorial [PHP für Noobs](https://github.com/Talesoft/tutorials-for-noobs/blob/master/de/php.md) auf. Könnt ihr noch kein PHP, solltet ihr euch erst selbiges zu Gemüte führen.

Hier geht es um Datentypen und wie sie verarbeitet werden. Dies ist kein einfaches "Ja also, es gibt String, Integer, Float und Array"-Tutorial, sondern hier lernt ihr **knallharte, graue Theorie**!

Spart euch das Informatik-Studium, ihr wollt sowieso programmieren und nicht als Consultant enden.


---


# Datentypen
PHP arbeitet mit unterschiedlichen Datentypen, die dem Interpreter dahinter mitteilen, wie er sich bei bestimmten Werten zu verhalten hat.

Das Typen-System in PHP ist sehr lose. Eine Variable muss nicht vorher mit einem Typen deklariert werden und es kann zu jedem Zeitpunkt jeder Werte-Typ in eine Variable geschmissen werden.

Drei der Datentypen in PHP haben wir bereits im vorigen Tutorial kennengelernt: **String**, **Integer** und **Float**
```php
$theString  = 'Dies ist ein String';    //'string' Datentyp
$theInteger = 1423;                     //'int' Datentyp
$theFloat   = 23.64;                    //'float' Datentyp
```

Der Unterschied ergibt sich in der Art und Weise, wie diese Daten im Arbeitsspeicher gelagert werden und ein sinnvoller Umgang mit den Datentypen erleichtert es, performante Applikationen zu schreiben, die nicht unnötig viel Arbeitsspeicher belasten.

Wir schauen uns die Art und Weise des Speicherns einmal im Detail an, um es zu verstehen.


---


# Binär, Bytes, Bits, WTF?
Ich werde hier nicht all zu detailliert auf das Binärsystem eingehen, aber es ist notwendig, dass ihr versteht, _warum_ Datentypen überhaupt existieren und was sie ausmacht. Überspringt diesen Schritt, wenn es euch zu viel ist, aber jammert mich dann am Ende nicht voll, wenn ihr Wissenslücken habt.

**Ein Byte sind 8 Bit**. Das wissen die meisten, selbst außenstehende Menschen. **Aber was bedeutet das?**

Ein Bit ist ein Zustand. Ein Schalter. Er kann entweder **An** (1) oder **Aus** (0) sein. Der Arbeitsspeicher (und auch viele andere Entitäten im Computer) speichern ihre Daten als **Bits**, also als eine Reihe von Schaltern, die entweder auf **1** oder auf **0** stehen (Im Computer: Entweder eine **hohe Spannung** oder eine **niedrige** haben)

Das Binärsystem erkläre ich in [Binärsystem für Noobs](https://github.com/Talesoft/tutorials-for-noobs/blob/master/de/binary-system.md) detailliert, falls es euch interessiert.

Da ein Byte 8 Bit sind und ein Bit ein Schalter, der entweder auf 1 oder auf 0 steht: **Was können wir mit 8 ollen Schaltern darstellen?**

Eine ganze, verdammte Menge, wie ihr gleich seht. Ihr lernt nun die Grundlage der gesamten Informationstechnologie, das Alpha und Omega, der Grund, warum ich dies schreiben kann und ihr es lesen könnt. Freut euch drauf.

Nutzen wir die vollen 8 Bit und nehmen uns die Möglichkeit für ein Vorzeichen weg, können wir mit 8 Bit, also 8 dummen Schaltern, die entweder auf `1` oder auf `0` stehen, eine Zahl zwischen 0 und 255 darstellen.

**Wie?**
```
|--------------------------------------------------|
| Stellenwert | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|--------------------------------------------------|
|        Wert |   1 |  0 |  1 |  0 | 0 | 1 | 0 | 1 |
|--------------------------------------------------|
```

Steht der Schalter auf 1, wird der Stellenwert addiert, tut er es nicht, wird er ignoriert.

Addiert erhalten wir hier
`128 + 32 + 4 + 1` und damit die Zahl `165`.

Die höchste Zahl, die wir darstellen können, ist die `255`, nämlich mit `1111 1111` (`128 + 64 + 32 + 16 + 8 + 4 + 2 + 1`)

Die niedrigste Zahl, die wir darstellen können, ist die `0`, nämlich mit `0000 0000`.

Wir können somit genau `256` Zahlen (inklusive der 0 eben) darstellen. Die Zahl kommt euch womöglich bekannt vor.

Dies ist das sogenannte **Unsigned Byte**, ein Byte ohne Vorzeichen (Sign = Vorzeichen, Unsigned = Kein Vorzeichen, Signed = Mit Vorzeichen)

Ihr könnt in diesem System _sämtliche_ Zahlen zwischen 0 und 255 darstellen, probiert es ruhig aus. Beachtet, dass wir keine negativen Zahlen darstellen können.

Wenn wir dies möchten, dann müssen wir ein Bit in unserem Byte für das Vorzeichen opfern. In dem Moment bedeutet `0` auf dem Bit, dass es sich um eine negative Zahl handelt, während `1` bedeutet, dass es eine positive Zahl ist. Es kann auch umgekehrt sein, das ist abhängig von der Computerarchitektur.

Beispiel:
```
|---------------------------------------------------------|
| Stellenwert | Vorzeichen | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---------------------------------------------------------|
|        Wert |          1 |  0 |  1 |  0 | 0 | 1 | 0 | 1 |
|---------------------------------------------------------|
```

Dies wäre hier der Wert `37` (`32 + 4 + 1` und das Vorzeichen ist `1`, also _positiv_)

Wollen wir dieselbe Zahl negativ darstellen, setzen wir das erste Bit (Vorzeichen) auf `0`. `0010 0101` würde demnach `-37` darstellen.

Wir können damit eine andere Zahlenreihe darstellen, nämlich `-127` (`0111 1111`) bis `127` (`1111 1111`).

Ein Bit, nämlich das mit dem höchsten Stellenwert, mussten wir opfern (Die 1 wäre fataler gewesen, denn dann könnten wir diverse Zahlen einfach nicht mehr darstellen).

Ein interessanter Fakt: Dieses System (und so ist es tatsächlich) erlaubt sowohl die `0` (`1000 0000`) als auch die `-0` (`0000 0000`), was natürlich an sich Unsinn ist, aber hier und da tatsächlich Gebrauch findet. Manche Systeme bieten statt der `-0` lieber eine `-128` an und rücken demnach einfach einen Wert auf, sollte das Byte `0000 0000` (`-0`) sein.

Das Ganze nennt man das **Signed Byte**, also ein Byte mit Vorzeichen.

Wir können also primär Zahlen mit Bits und Bytes darstellen und im Arbeitsspeicher oder auf der Festplatte speichern. Verschiedenste Zahlen. Je nachdem, wie viele Bits und Bytes wir verwenden.

Ich belasse es erst mal dabei, etwas graue Theorie zu diesem Thema wird noch folgen.

Ihr werdet gleich noch sehen, wie wir auch Buchstaben, höhere und niedrigere Zahlen sowie Gleitkommazahlen darstellen können.


---


#### Der String
Der String ist eine Sammlung aus Zeichen. Jedes Zeichen (`D`, `i`, `e`, `s`, ` `, `i`, `s`, `t`, ` `, `e`, `i`, `n`, ` `, `S`, `t`, `r`, `i`, `n`, `g`, `!`), in der Regel als **Character** oder einfach nur **Char** bezeichnet, wird im Arbeitsspeicher als 1 **Unsigned Byte** dargestellt. Wisst ihr nicht, was das ist, lest bitte noch mal von vorne.

**Der String ist wohl der komplexeste Datentyp, die folgenden werden einfacher. Wenn euch diese Theorie etwas erdrückt, überspringt es ruhig, ich kann euch aber versichern, dass es hilfreiches Wissen für die Zukunft ist!**

Ein String mit dem Inhalt `Dies ist ein String!` würde demnach 20 Bytes benötigen (Er hat 20 Zeichen!), 1 Byte für jedes Zeichen. Dazu kommt noch ein sogenannter Null-Terminator (`0000 0000`), der dem Computer _Hier endet deine Zeichenkette!_ sagt, denn eine Zeichenkette kann beliebig lang sein. Sagen wir also `$theString = 'Dies ist ein String!';` werden in diesem Moment genau 21 Bytes im Arbeitsspeicher für diesen Wert beansprucht und dieser wird dort abgelegt.

Nun, **wie stellt man Buchstaben als Zahlen dar?**

Dies ist ein wichtiger Punkt und von ein paar Begriffen gleich habt ihr sicherlich schon einmal gehört: Eigentlich sind es Zahlen!

Die Buchstaben, die wir visuell vor uns haben, werden im Arbeitsspeicher eigentlich als Zahl hinterlegt. Um dies zu realisieren, wird ein sogenanntes **Charset** verwendet, eine Tabelle, die beschreibt, welche Zahl für welches Zeichen steht.

Eines der großen Standard-Charsets, die ihr oft unbewusst verwendet, ist z.B. **[ASCII](http://www.asciitable.com/)** (American Standard Code for Information Interchange).

Arbeiten wir mit dem Charset **ASCII**, legen wir automatisch ein paar Mappings fest, wie z.B.
- Die Zahl `65` ist ein `A`
- Die Zahl `89` ist ein `Y`
- Die Zahl `97` ist ein `a`
- Die Zahl `37` ist ein `%`
- Die Zahl `9` ist ein `TAB` (Die Taste links neben dem `Q`)
- Die Zahl `10` ist ein `LF` (Line Feed, Zeilenumbruch)

Wenn der String nun gespeichert werden soll, werden alle Buchstaben in Zeichen übersetzt.

Der normale ASCII-Zeichensatz nimmt sogar nur die ersten 128 Möglichkeiten ein, nämlich die wichtigsten (amerikanischen) Zeichen, die man so braucht. Dazu kommt Extended ASCII, dass 128 weitere Zeichen bringt, die man eher selten benötigt. Denkt dran, 1 Byte pro Zeichen, also maximal 256 (0 - 255) mögliche Zeichen im ASCII-Zeichensatz pro Zeichen in unserem String.

Nutzen wir also das ASCII-Charset (Tun wir nicht immer!), dann würde unser String wie folgt im Arbeitsspeicher gespeichert werden (Jede Zelle ist ein Byte, also 8 Bit, also eine Zahl zwischen 0 und 255!):


```
|---------------------------------------------------------------------------------------------------------------------------------------------|
|      Position |  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  |  10 |  11 |  12 |  13 |  14 |  15 |  16 |  17 |  18 |  19 |  20 | 
|---------------------------------------------------------------------------------------------------------------------------------------------|
|  Dezimal-Wert |  68 | 105 | 101 | 115 |  32 | 105 | 115 | 116 |  32 | 101 | 105 | 110 |  32 |  83 | 116 | 114 | 105 | 110 | 103 |  33 |   0 |
|---------------------------------------------------------------------------------------------------------------------------------------------|
| ASCII-Zeichen |   D |  i  |  e  |  s  |     |  i  |  s  |  t  |     |  e  |  i  |  n  |     |  S  |  t  |  r  |  i  |  n  |  g  |  !  | END |
|---------------------------------------------------------------------------------------------------------------------------------------------|
```

Die Variable `$theString` speichert quasi nur die `0` als Position des Strings im Arbeitsspeicher. Wird der Wert abgerufen, greift PHP auf diese Position zu und liest den Arbeitsspeicher so lange aus, bis der Null-Terminator (`END`) erscheint. Danach wird der Zeichensatz drübergebügelt und ihr habt euren String.

Nun wisst ihr also, wie Strings im Arbeitsspeicher gespeichert werden. **Aber was bringt euch das Ganze?**

#### Zeichensätze (Charsets)
Unabhängig von interessantem Wissen folgende Frage an euch: **Wie stelle ich ein `Ü` dar?**

Hier beginnen nämlich die Probleme dieses ganzen Systems!

Der normale **ASCII**-Zeichensatz _besitzt kein Ü_! Und auch kein Ä, Ö, ü, ä, ö oder ß. Also wie stellen wir unsere schöne, deutsche Sprache dar?

Auf manchen Websites: Gar nicht. Diese enden entweder darin, HTML Entities nutzen zu müssen (`&Uuml;`, `&szlig;`) oder ihr erhaltet Kauderwelsch, weil der Computer keine korrekten Zeichen zur Übersetzung findet.

Für alle, die sich mit diesem Thema beschäftigt haben: **[ISO-8859-1](https://de.wikipedia.org/wiki/ISO_8859)**!

Natürlich, bei den Amis ist es einfach **ASCII** und wir müssen uns bescheuerte Zahlenkombinationen merken? Exakt. Europäer sind da penibler. Das `8859` ist nicht schwieriger zu merken als der Jugendschutzpin der Skybox eurer Eltern und merkt euch ansonsten einfach die `1` (Wir sind die 1!) für **Westeuropa**.

Der Westeuropäische Zeichensatz für das lateinische Alphabet, inklusive unserem, lautet **ISO-8859-1**. 

Seid ihr Amerikaner, könnt ihr auch einfach europäische Zeichensätze nutzen, denn die ersten 128 Zeichen sind dieselben wie im ASCII-Zeichensatz, unser normales Alphabet.

Nun, ISO-8859-1 macht dafür aus den letzten 128 Zeichen keine tollen Steuer- und Konsolenzeichen, sondern unser vermisstes `Ü` und zwar auf der `220`.

Nutzen wir also als Charset in unserer Datenbank und in der Browserausgabe das **ISO-8859-1** Charset, können wir alle Zeichen unserer Sprache nach belieben nutzen.

Schön, dass wir Deutschen dann mit dem System soweit auch glücklich sind.

Eine weitere Frage an euch: **Was machen Japaner, Chinesen, Griechen und Russen?**
Einige dieser Alphabete lassen sich durchaus in ein Charset einfassen, so haben die meisten Länder oder zumindest Regionen ihre eigenen ISO-*-Charsets.

Nun etwas Allgemeinwissen: Es gibt geschätzt über 50,000 verschiedene [Kanji](https://de.wikipedia.org/wiki/Kanji) auf der Welt. Das sind diese chinesischen und japanischen Zeichen, die nicht etwa wie Katakana oder Hiragana für Silben stehen, sondern für ganze Wörter bzw. Objekte. 

Normale Schulkinder in China lernen im Durchschnitt alleine ca. 1,000 Kanji. Normale Leser kennen im Durchschnitt gut 2,000 Kanjis.

Wir haben also 50,000 Kanji, die wir in ein Charset unterbringen möchten, dass 255 Zeichen fasst. Ööööhm.....ja.

Selbst bei einem Schulkind-Charset für Chinesen müssten wir also mindestens 4 Charsets anlegen, die man permanent wechseln müsste.

Diese Probleme gibt es mit vielen Sprachen, so haben z.B. auch die arabischen Sprachen diverse Unterschiede, die das Charset-System obsolet machen.

#### UTF-8 zur Rettung!
[UTF-8](https://de.wikipedia.org/wiki/UTF-8) habt ihr sicher schon einmal gehört.

UTF-8 ist eine andere Art von Kodierungssystem, dass abwärtskompatibel mit amerikanischen und europäischen Charsets ist. UTF-8 ist auch kein Charset, sondern eben eine Kodierung (Encoding). Charsets sind auch eine Kodierung.

Mit UTF-8 wird die Begrenzung aufgehoben, dass ein Character in einem String genau ein Byte einnimmt. Nun kann ein Character bis zu 4 Bytes einnehmen (Muss es aber nicht! Ein `A` z.B. lässt sich mit einem Byte darstellen).

Die ersten 128 Zeichen des UTF-8 Encodings entsprechen dem ASCII-Zeichensatz. Allerdings wird dem ersten Byte auch ein Bit gemopst, damit wir eine Angabe darüber treffen können, ob weitere Bytes folgen.

Steht das erste Bit auf `1`, kommt ein weiteres Byte und ein weiterer Bit im ersten Byte wird gemopst. Steht dieses auch auf `1`, gibt es ein drittes Byte und es wird ein weiteres Bit gemopst. Ist auch dieses `1`, haben wir genau 4 Bytes, die wir kombinieren können. Dadurch, dass uns hier und da ein paar Bit gemopst werden, um die Funktion selbst zu realisieren (Wie oben beim Signing bereits), können wir leider nicht die ganzen 32 Bit nutzen. Das ist aber völlig okay, UTF-8 ist zurzeit auf ein Limit von **1.114.112 Möglichkeiten** beschränkt.

Wir können also mit UTF-8 statt 255 verschiedenen Zeichen auf einmal 1.114.112 verschiedene Zeichen darstellen. Toll, oder nicht?

Für unsere chinesischen Schulkinder ist damit gesorgt!

#### Ende der Strings
Wir haben also gesehen, wie sich so ein String verhält, wie er gespeichert wird und wie ein Computer ihn handhabt.

In PHP braucht ihr euch natürlich (um das meiste davon!) nicht zu scheren. Ihr könnt aber im Endeffekt im Kopf ausrechnen, wie viel Speicher euer Programm verbrauchen wird, wenn ihr spezifische Strings nutzt, wenn ihr möchtet!

Weiterhin werdet ihr viele Probleme mit Zeichenkodierungen vermeiden, wenn ihr versteht, wie es funktioniert und einfach überall und immer UTF-8 nutzt.


---


# Der Integer
Graue Theorie für eure Hirnzellen. Wenn ihr Einsen und Nullen nicht sehen könnt....ach was erzähle ich, dann seid ihr sowieso falsch. Viel Spaß!

**Warum gibt es den Integer?** Na ganz einfach: **Weil wir Zahlen speichern wollen, die höher als 255 und niedriger als -127 sind!**

Der Integer stellt immer eine Ganzzahl dar. Zwischen Ganzzahlen und Gleitkommazahlen wird in der IT stark unterschieden. In den meisten Fällen benötigt man allerdings auch eben nur einen Integer.

Der Integer nimmt immer **4 Byte/32 Bit** im Arbeitspeicher ein (Bis auf eine gewisse Ausnahme, die meist zutrifft, siehe dann weiter unten)

Ein **Signed Integer** fasst die Werte `−2.147.483.648` bis `2.147.483.647`. (`-0` wird für die `-2.147.483.648` verwendet) Wir haben also schon ziemlich hohe Zahlen, mit denen wir rechnen können.

Aber wie können wir denn aus 4 Bytes, also 4 Zahlen zwischen 0 und 255, eine große Zahl machen?

Verwendet wird dazu das sogenannte **Bitshifting**. Ihr müsst heute nicht verstehen, was das ist und wie es funktioniert, aber im Endeffekt werden alle 4 Byte einfach vom Stellenwert her um 8 Bit verschoben. Ich gehe auch nicht auf **Little Endian** oder **Big Endian** ein, googelt diese Begriffe gerne, wenn es euch interessiert. Wir machen hier **Little Endian**, einfach nur zur Veranschaulichung.

Unsere 4 Bytes z.B. könnten so aussehen:
```
1.
|--------------------------------------------------|
| Stellenwert | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|--------------------------------------------------|
|        Wert |   0 |  0 |  0 |  0 | 1 | 0 | 0 | 1 |
|--------------------------------------------------|

2.
|--------------------------------------------------|
| Stellenwert | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|--------------------------------------------------|
|        Wert |   0 |  0 |  1 |  0 | 1 | 0 | 0 | 0 |
|--------------------------------------------------|

3.
|--------------------------------------------------|
| Stellenwert | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|--------------------------------------------------|
|        Wert |   0 |  0 |  0 |  1 | 0 | 1 | 0 | 1 |
|--------------------------------------------------|

4.
|---------------------------------------------------------|
| Stellenwert | Vorzeichen | 64 | 32 | 16 | 8 | 4 | 2 | 1 |
|---------------------------------------------------------|
|        Wert |          1 |  1 |  0 |  0 | 0 | 1 | 0 | 0 |
|---------------------------------------------------------|
```

Das letzte Byte muss ein Bit für unser Vorzeichen opfern.

Wir haben also die Bytes `0000 1001`, `0010 1000`, `0001 0101` und `1100 0100` (Ohne Vorzeichen `0100 0100`)

Dezimal wären das `9`, `40`, `21` und `68`.

So werden sie auch im Arbeitsspeicher gespeichert, als einzelne Bytes.
- Das letzte Byte (4.) bleibt, wo es ist, also `1100 0100`. Merkt euch, dass hier das erste Bit für unser Vorzeichen steht.
- Das vorletzte Byte (3.) wird um 8 Bits nach rechts _geshiftet_, also verschoben. Es würde also `0000 0000 0001 0101` entstehen
- Das zweite Byte (2.) wird um 16 Bits nach rechts _geshiftet_, also `0000 0000 0000 0000 0010 1000`
- Das erste Byte (3.) wird um 24 Bits nach rechts geshiftet, also `0000 0000 0000 0000 0000 0000 1001`

Diese 4 Bit-Blöcke werden mit einer Bitweisen OR (`|`)-Operation verknüpft. d.h. sie werden untereinander gelegt
```
0000 0000 0000 0000 0000 0000 0000 1001
0000 0000 0000 0000 0010 1000
0000 0000 0001 0101
1100 0100
```
und jedes so kombiniert, dass alle Bits auf `1` stehen, die in _irgend einer_ der 4 Zeilen an derselben Stelle eine `1` haben.

Das Ergebnis wäre
```
1100 0100 0001 0101 0010 1000 0000 1001
```

Die Wertetabelle für diesen Binärwert ist etwas groß, deshalb stelle ich diese nun nicht dar.
- Das erste Bit vorne ist das Vorzeichen (`+`)
- Das höchste Bit ist das zweite Bit mit dem Stellenwert 2^30 (1.073.741.824)
- Das letzte Bit ist unser Ende mit der 2^0 (1)

Diese Zahl würde nun `1.142.237.193` darstellen. Wir haben also aus den Zahlen `9`, `40`, `21` und `68` die Zahl `1.142.237.193` erreichnet. Verdammte Mathematik! Damit lässt sich schonmal einiges anfangen.

Die nächst-höhere Stelle wäre die 2^31 mit einem Stellenwert von 2.147.483.647. Das ist interessant, denn würden wir unser erstes Bit vorne nicht für das Vorzeichen verschwenden, könnten wir doppelt so hohe Zahlen speichern (4.294.967.295). Ein **32 Bit Unsigned Integer** würde somit die Werte `0` bis `4.294.967.295` fassen.

#### Fun-Fact für zwischendurch:
4.294.967.295 ist auf die größte Arbeitsspeicheradresse, die eine 32Bit CPU mit einem Unsigned Integer ansprechen kann. Jede Adresse speichert einen Byte.

Folglich ist eine 32Bit CPU in der Lage, 4.294.967.296 (0 ist auch ein valides Offset) Byte an Daten zu speichern. Das sind genau 4.194.304 Kilobyte, 4096 Megabyte und 4 Gigabyte und entspricht eben genau der Menge an Arbeitsspeicher, die sich in einem 32Bit System verwenden lassen. 

Wenn ihr euch bisher gefragt habt, warum 64Bit CPUs notwendig waren und sind: **Deshalb!!**

#### Long Integers
In Zeiten der 64Bit Systeme ist es unsinnig, diese nicht auch in PHP zu erlauben. Deshalb stellt PHP sich auf 64 Bit Systemen um und aus dem 4 Byte/32 Bit Integer wird ein **8 Byte/64 Bit Long Integer**. Dies funktioniert tatsächlich bis PHP7 nicht unter Windows, sitzt ihr als gerade an einem Windows, werdet ihr von den gleich kommenden Zahlen nur träumen können (oder ihr installiert PHP7!)

Nun ist es ja so: Jede weitere Stelle in unserem Zahlensystem, also jedes weitere Bit, dass wir speichern können, _verdoppelt_ die Anzahl unserer möglichen Zahlen.

Demnach heißt `64 Bit` nun nicht, dass es das doppelte eines `32 Bit` Integers speichern kann, sondern das **2^32-fache**.

Ich brauche euch nur die Zahlen zeigen und ihr versteht, wie viel mehr das ist.

- Die kleinste Zahl, die der 64 Bit Integer speichern kann ist `−9.223.372.036.854.775.808`.
- Die größte Zahl, die der 64 Bit Integer speichern kann ist `9.223.372.036.854.775.807`

Hier haben wir nun endlich einen Zahlenbereich, mit dem wir wahrscheinlich noch viele Jahrzehnte leben können. Das Prinzip ist dasselbe wie beim 32 Bit Integer, es werden einfach nur mehr Bytes verwendet und dadurch können wir die maximale Stelle um 4x8, also 32 Bits weiter nach rechts schieben. Die letzte Stelle, die wir damit erreichen, ist somit 2^63 und beträgt `4.611.686.018.427.387.904`. Binär dargestellt wäre das `0100 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000 0000`. Na wenn da nicht etwas kompensiert wird!

#### Die Fakten

- Ein PHP Integer fasst auf einem 32 Bit System minimal `−2.147.483.648` und auf einem 64 Bit System minimal `−9.223.372.036.854.775.808`
- Ein PHP Integer fasst auf einem 32 Bit System maximal `2.147.483.647` und auf einem 64 Bit System maximal `9.223.372.036.854.775.807`

Dies sind die Zahlenbereiche, die ihr mit einem Integer bereitstellen könnt und nun wisst ihr auch, warum.

Wenn ihr die Zahlenbereiche innerhalb von PHP automatisch ermittelt wollt, könnt ihr die Konstanten `PHP_INT_MIN` und `PHP_INT_MAX` verwenden. Überschreitet eine Zahl diese Grenze, wird sie automatisch als `float` gehandhabt und ihr erhaltet eine zufällige, aus euren Int-Bytes bestehende, Kommazahl. Verhindert also mit aller Gewalt, dass jemand euch größere Zahlen als `PHP_INT_MAX` oder kleinere Zahlen als `PHP_INT_MIN` unterjubeln kann.

Das Ganze nimmt aber für euch leider heute noch kein Ende, denn während Ganzzahlen ja cool und schick sind, wären Gleitkommazahlen doch eine feine Sache, oder nicht?
Schließlich wollen wir unser Divisionsergebnis nicht grundsätzlich gerundet erhalten.


---

# Der Float
Dieser Punkt ist in PHP leider etwas verschwommen. 

Normalerweise besteht ein `float`-Wert aus 32 Bit. Es gibt einen präziseren Typen, nämlich `double`, welcher eine _längere_ Kommazahl mit insgesamt 64 Bit darstellen kann.

In PHP sind Floats immer 64 Bit groß, sofern 64 Bit möglich sind. Auf 32 Bit Systemen sind sie demnach immer 32 Bit groß.

Das liegt daran, dass PHP den Datentyp `double` nicht kennt. In PHP sind alle `float`s automatisch `double`s.

Die Art und Weise wie Gleitkommazahlen gespeichert werden, ist von System zu System und Implementierung zu Implementierung sehr unterschiedlich, deshalb werde ich hier nun keine Allgemeinlösung präsentieren. Wen das detailliert interessiert, der kann sich gerne den unheimlich aufschlussreichen [Wikipedia-Artikel](https://de.wikipedia.org/wiki/Gleitkommazahl#Darstellung) zu dem Thema durchlesen.

Computer haben vergleichsweise unheimliche Schwierigkeiten mit Kommazahlen, denn viele errechneten Kommazahlen sind für uns nahezu unendlich. Würden wir jede Kommazahl vollständig speichern, ohne sie in irgend einer Form zu runden, würde es keine 2 Sekunden dauern und der Arbeitsspeicher wäre voll. Voll mit Stellen hinter dem Komma.

Um dies zu verhindern, werden Kommazahlen eben mit begrenzter Präzision gespeichert. Sie weichen quasi eigentlich _immer_ ab, in bestimmten Architekturen nur mal mehr und mal weniger. Die meisten CPUs haben einen eigenen Bereich, der ausschließlich für die Berechnung von Gleitkommazahlen zuständig ist.

Gerade in der 3D-Entwicklung sind Kommazahlen ein großes Thema, denn der gesamte 3D-Raum wird zwischen 1 und 0 auf allen 3 Achsen berechnet. Um nun einen Pixel auf einem 4K-Monitor gezielt richtig darzustellen und zu positionieren, müssen ziemlich genaue Präzisionen wirken.

Wir wollen hier demnach heute nicht erklären, wie Kommazahlen funktionieren, sondern eher, auf welche Probleme ihr stoßen werdet, denn sie richten überall Probleme an!

Maximal- und Minimalwerte für Floats in PHP gibt es so nicht. In der Regel werden sie aber auch nicht für Werte verwendet, die in irgend einer Form sehr niedrig oder sehr hoch limitiert werden müssten.


Probleme sind eher Dinge wie [folgender Aufbau](http://php.net/manual/de/language.types.float.php#113703) (Danke, catalin!):
```php
$x = 8 - 6.4;
$y = 1.6;

var_dump($x == $y);
```

Wir errechnen hier 2 Kommazahlen und vergleichen diese.

Normalerweise dürften beide Zahlen exakt `1.6` darstellen. Der Vergleich müsste demnach in jedem Fall `true` Ergeben, die Zahlen stimmen ein.

Nun ist es leider so, dass es dies eben nicht tu. Der Vergleich schlägt (in der Regel!) fehl und es gibt `false` als Ausgabe.

**Warum?**

Nun, wie schon erwähnt, mit der Präzision bei Float-Zahlen haben die Systeme es nicht so. Da ist `8 - 6.4` eventuell mal eben nicht `1.6`, sondern eher `1.5999999999999999999999999999999999999234235325...`. `var_dump` würde für `$x` eventuell sogar `1.6` ausgeben, intern ist der Wert allerdings ein anderer. Damit schlägt der Vergleich fehl. 

Dies ist kein PHP-typisches Problem, viele Sprachen, wie z.B. JavaScript, haben ebenfalls große Probleme mit Float-Werten.

Umgehen könnt ihr es auf 2 Wege:

#### Runden
Ihr könnt ganz normal, wie in der Mathematik, runden.

In PHP gibt es drei Möglichkeiten zum runden:
- `ceil($x)` (`ceil` wie in `ceiling`, also `Decke`) rundet immer _auf_, und zwar auf den nächstgrößten, ganzzahligen Wert. Das Ergebnis wäre der Integer `2`.
- `floor($x)` (`floor` bedeutet `Boden`) rundet immer _ab_, auf das nächstkleineren nächstgrößten, ganzzahligen Wert. Das Ergebnis wäre der Integer `1`.
- `round($x)` rundet mathematisch, heißt: Alles über `.5` wird aufgerundet, alles darunter wird abgerundet. Das Ergebnis ist immer ein Integer.

und nun die für uns relevanteste Methode, denn eigentlich wollen wir aus unserer `1.5999999999...` weder `1`, noch `2` machen, sondern `1.6`
- `round($x, $precision)`. Mit `$precision` ist hier die Anzahl der Stellen hinter dem Komma gemeint.

Mit folgendem Code könnten wir also dafür sorgen, dass unser Vergleich hinhaut:
```php
$x = round(8 - 6.4, 1);
$y = 1.6;

var_dump($x == $y);
```

Wir nutzen `round(8 - 6.4, 1)` um das Ergebnis auf **eine** Stelle hinter dem Komma zu runden. Da wir wissen, dass irgendwas annähernd `1.6` als Ergebnis kommt, also so was wie `1.59999....`, wissen wir ebenfalls, dass aufgerundet wird.

Ihr könnt beide Vergleiche testen. Wie gesagt, es unterscheidet sich von System zu System und von Architektur zu Architektur, so ist es durchaus möglich, dass der erste Vergleich bei euch `true` ergibt. Hier bei mir ist er definitiv `false`, der zweite gibt mir `true` zurück.


#### Annäherung/Toleranz (Epsilon)
Ein weiterer Weg, das Problem zu umgehen, allerdings ein etwas aufwendigerer: Toleranzen.

Wir können eine Toleranz (Mathematisch in der Regel als `Epsilon` bezeichnet) definieren und diese zulassen. 

Die Funktion `abs($x)`, die wir gleich nutzen, entfernt einfach nur das Vorzeichen einer Zahl. d.h. aus `-1.7` wird `1.7`, aus `1.7` wird ebenfalls `1.7`. Das Ergebnis ist immer dieselbe Zahl, nur positiv.

```php
$a = 1.23456789;
$b = 1.23456780;
$epsilon = 0.00001;

if (abs($a - $b) < $epsilon) {

    echo 'Die Werte sind _fast_ identisch!';
}
```

Wir haben hier nun eine Toleranz von `0.00001` definiert. Wir subtrahieren die beiden Werte gegeneinander und machen durch `abs()` die Frage überflüssig, welcher von beiden der höhere war.

Dann prüfen wir, ob die Differenz unter unserer Toleranz liegt. Tut sie es, lassen wir den Wert zu.


Nun haben wir zumindest einen kleinen Einblick in die Welt der Floats erhalten. Eine spannende, nervenauftreibende, teilweise jemanden zur Weißglut treibende Geschichte von Menschen, die versuchen, sich gegen Naturgesetze durchzusetzen.


---


# Das Ende

Ursprünglich war dieser Artikel hier den normalen PHP Datentypen gewidmet und eigentlich sollten hier jetzt noch weitere Datentypen erscheinen. Die Tatsache, dass ich diese Datei im Laufe des Schreibens von `data-types` zu `data-types-detailed` umbenannt hab, sollte euch klar machen, mit welchem Level an komplexem Wissen ihr nun ausgestattet wurdet und warum ich eben jene anderen Datentypen nicht erwähne, sondern dafür eine neue `data-types.md` verfassen werde.

Ich werde diesen Artikel womöglich noch um das `boolean` ergänzen, nur heute nicht mehr.


---


# Who won, who's next?

Wenn euch dieses Tutorial gefallen hat: Mein Beileid!

Ich bedanke mich für die Aufmerksamkeit und hoffe, dass euch Datentypen in etwa genau so viel Kopfschmerzen bereitet haben, wie mir damals. Sorry, sonst wäre das einfach nicht fair!

Möchtet ihr mehr Tutorials sehen, habt ihr Fragen, Kritik und/oder Anregungen, habt ihr einen Fehler gefunden oder seid ihr auf der Suche nach der großen Liebe, [spendiert mir einen Kaffee](https://www.paypal.me/TorbenKoehn) und/oder [schreibt mir eine E-Mail](mailto:tk@talesoft.io).




Good night, good fight.

~Torben Köhn