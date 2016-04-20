Binärsystem für Noobs
=============


# Vorwort
Zugegeben, ich bin auch kein großes Mathematik-Genie. Aber das, was ihr hier lernt, wird ausreichen, um die Vorgänge und Berechnungen innerhalb von binären Systemen zu verstehen und anzuwenden.

Dieses Tutorial ist allgemein gehalten und allgemein gültig. Ihr könnt es immer gebrauchen, wenn ihr etwas mit Computern zu tun habt oder haben wollt und etwas tiefer in die Materie einsteigen möchtet.

Es geht hier explizit um Zahlensysteme. Das Grundproblem, und der Grund für dieses Tutorial, ist die Tatsache, dass viele Leute Zahlen einfach ganz anders betrachten als jene, die Zahlensysteme aufgenommen und verstanden haben.

---

# Über das Binärsystem
Fangen wir damit an, die Frage zu klären, **was das Binärsystem überhaupt ist**.

Das _Binär_ im Binärsystem kommt aus dem lateinischen und steht für _bini_ (_"je zwei"_) oder _bina_ (_"doppelt/paarweise"_). Im Deutschen nennt man es oft und gerne auch das **Dualsystem**. Wenn ihr nun noch dazu beachtet, dass das _Dezi_ im Dezimalsystem (also unserem, normalen Zahlensystem) für _"zehn"_ bzw. _"zehnfach"_ steht, erkennt ihr schnell, warum das Binärsystem so heißt.

Es nennt sich so, weil es, anders als in unserem Dezimalsystem, nicht **zehn** (_"decem"_) Ziffern gibt (`0123456789`), sondern nur **zwei** (_"bini"_) (`0` und `1`).

Dies ist gerade in der Computerwelt relevant, denn in Stromkreisen hat man leider in der Regel keine **zehn** Zustände, sondern maximal **zwei**:
- Strom liegt an (`1`)
- Strom liegt nicht an (`0`)

Es ist im Computer selbst noch etwas anders, darauf gehen wir aber später ein. Wichtig ist, dass ihr versteht, dass ein Computer nur zwei Zustände kennt: `1` und `0`. `An` und `Aus`. `Wahr` und `Falsch`.

Nun verrate ich euch vorab, dass wir mit diesen zwei Ziffern, also `0` und `1`, genau so effiziente Mathematik betreiben können und jeden erdenklichen Wert darstellen können, den wir möchten, wie mit unserem Dezimalsystem. Nicht einmal schwieriger, nur für euch umständlicher, weil ihr an das Dezimalsystem gewöhnt seid.


---


# Ziffern und Werte: Zahlensysteme
Bevor wir nun anfangen, mit Einsen und Nullen um uns zu werfen, benötigen wir einen kleinen Exkurs in Zahlensysteme. Beherrscht ihr diese perfekt, überspringt diesen Part. 

Eure Lehrer haben in der Schule versucht, euch diese zu erklären, wenn man allerdings (wie ich) Lehrer hatte, die sie selbst nicht richtig verstehen, wird es schwierig, daraus eine lehrreiche Lektion für die Zukunft zu gestalten. Ich habe mir diesen Mist selbst angelesen und es tut mir gut, zu versuchen, es so simpel wie möglich zu erklären, um euch denselben Mist zu ersparen und das zu tun, was eigentlich Aufgabe unserer Lehrer hätte sein müssen.


Ein kleiner Fakt: **Die Ziffer 2 und die Zahl 2 können grundlegend unterschiedliche Dinge bedeuten!**

Das klingt vielleicht etwas vewirrend, aber wir decken diese Aussage nun nach und nach auf.

Grundsätzlich gilt es zu verstehen, dass man in Zahlensystemen zwischen drei grundlegenden Dingen unterscheidet: **Ziffer**, **Wert** und **Stellenwert**

### Ziffern
**Ziffern** sind im Grunde einfach nur Zeichen. Symbole. Irgendjemand hatte 3 Äpfel in der Hand und dachte sich _"Ey, für die Anzahl an Äpfeln definiere ich eine Ziffer!"_, hat danach auf ein Blatt Papier zwei umgedrehte, gestapelte `c`s gekritzelt und tada: Die `3` war geboren. Als Beschreibung für den **Wert** 3 (`|||`). Natürlich ging es _etwas_ professioneller zu, aber so in der Art kann man sich das vorstellen.

Alle wichtigen Werte, mit denen wir arbeiten, wurden also Symbole, Ziffern zugewiesen. Nun hat man aber wohl das Problem, dass einem irgendwann die Symbole ausgehen. In einigen Zahlensystemen hat die `10` z.B. ihr eigenes Symbol (Römisches Zahlensystem, `X`). In unserem nicht.

Im Dezimalsystem hat man sich gesagt: _"Bei 10 Ziffern ist Schluss!"_. Und das ist auch gut so, sonst wäre unsere Mathematik um die Anzahl der weiteren Ziffern komplexer.

Ihr könnt euch das so vorstellen, dass im Endeffekt irgendwann jemand dagesessen hat, seine Finger abgezählt und jeder Anzahl von Fingern ein Symbol, eine Ziffer zugewiesen hat. Bei einem Finger hat er eine `1` daneben gemalt, bei zwei Fingern eine `2`, bei drei Fingern eine `3` usw. und hat damit unser heutiges Zahlensystem definiert: **Das Dezimalsystem**.

Warum genau 10 Ziffern? Warum nicht 13? oder 28? oder 4? **Na weil wir 10 Finger haben!**. Das Dezimalsystem arbeitet mit 10 Ziffern, weil wir 10 Finger haben, mit denen wir jede Ziffer darstellen können. Dies erleichtert uns das erlernen des Systems und das Kopfrechnen. Ihr glaubt es nicht? Lest es nach. Genau das ist der Grund.

Im Dezimalsystem gibt es da eine ganz einfache Zuordnung, die euch nicht schwer fallen wird, weil ihr es genau so gelernt habt:
- `0` hat den Wert `Nichts`, keine Sache
- `1` hat den Wert `|`, also eine Sache
- `2` hat den Wert `||`, also zwei Sachen
- `3` hat den Wert `|||`, also drei Sachen.
- `4` hat den Wert `||||`, also vier Sachen
- `5` hat den Wert `|||||`, also fünf Sachen
- `9` hat den Wert `|||||||||`, also neun Sachen

Lernt also, zwischen Symbol/Ziffer und Wert zu trennen. Eine `2` ist eine `2`, weil irgendwer irgendwann gesagt hat, dass `||` Sachen als `2` dargestellt werden. Wäre ja auch anstrengend, wenn wir für 300 Sachen `||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||....` schreiben müssten. Das wird nun wichtig.

Wir schreiben nun schon so oft die `10`, **aber was genau ist die `10` eigentlich?**

Die Zehn ist grundsätzlich erst einmal die Kombination aus den Ziffern `1` und `0`. Wir haben kein Zeichen für eine `10`. Also was genau macht die `10` zu der Zahl, die genau einen Wert höher als die `9` ist?

### Stellenwerte
In den meisten Zahlensystemen sitzt ganz links der höchste Stellenwert, ganz rechts der niedrigste. Wir multiplizeren immer den **Wert** unserer **Ziffer** mit dem **Stellenwert** der Stelle der Ziffer, an der sie positioniert ist und addieren anschließend alle Werte. Haben wir alle unsere Ziffern für einen Stellenwert aufgebraucht, müssen wir einen höheren Stellenwert verwenden.

In jedem Zahlensystem hat eine normale Ziffer, die einfach nur so da steht, immer den Stellenwert `1`.

Haben wir also nun eine `5` einfach so da stehen und wir wissen: Eine alleinstehende Zahl hat immer den Stellenwert `1`, können wir den **Wert** der **Ziffer** (`|||||`) mit unserem **Stellenwert** (`1`) multiplizieren und erhalten damit den Wert unserer finalen **Zahl**: `5`.

Erst wenn unsere **Ziffern** durch unsere **Stellenwerte** gebügelt wurden, sind es **Zahlen**, erst dann stellen sie ihren tatsächlichen **Wert** dar. Das ist eine Kopfsache, das ist das wirklich schwierige dabei. Ihr müsst im Kopf verstehen, dass eine `10` erst durch ihren Stellenwert zum Wert `||||||||||` wird. Nicht, weil irgendjemand gesagt hat _"Ja, `||||||||||` stellen wir einfach als `10` dar!"_

Im Falle unserer Zehn haben wir **zwei** Stellen. Da wir mit einer Stelle exakt die Werte `0` bis `9` darstellen können, muss uns unser nächster Stellenwert die Möglichkeit geben, den nächsthöheren Wert, also `||||||||||` (`10`) auszudrücken. Deshalb ist der Stellenwert der zweiten Stelle `10`, nämlich `||||||||||`. Der nächsthöhere Wert, den wir benötigen.

In einer kleinen Tabelle mit Stellenwert dargestellt, sieht das folgendermaßen aus:
```
|-----------------------|
| Stellenwert | 10 |  1 |\
|-----------------------|  Stellenwert x Ziffer-Wert für jede Stelle/Spalte
| Ziffer-Wert |  1 |  0 |/
|-----------------------|-------------|
|        Wert | 10 |  0 | 10 + 0 | 10 |
------------------------|-------------|
```

Wir haben also die Zahl `10` auseinander genommen. An der ersten Stelle (bei zwei Stellen mit dem Stellenwert **10**) haben wir die `1` als Ziffer stehen. Ihr **Wert** (nämlich `1` oder `|`) wird mit unserem Stellenwert (Also **10**) multipliziert. Dasselbe tun wir auch für die zweite Stelle mit dem Stellenert **1**. `1 x 0` sind immer `0`. Am Ende addieren wir die beiden Ergebniswerte, also `10` und `0` und erhalten damit den gesamten Wert unserer Zahl.

Wir sind also in der Lage, mit der Zahl `1` und der Zahl `0` den **Wert** `||||||||||` darzustellen. Durch **Stellenwerte**. Ihr macht das völlig unterbewusst, seit Jahrzehnten.

Die letzte Zahl, die wir mit zwei Stellen darstellen können, ist die `99`, denn das sind die beiden Ziffern mit den höchsten Werten, die wir besitzen.
```
|-----------------------|
| Stellenwert | 10 |  1 |\
|-----------------------|  Stellenwert x Ziffer-Wert für jede Stelle/Spalte
| Ziffer-Wert |  9 |  9 |/
|-----------------------|-------------|
|        Wert | 90 |  9 | 90 + 9 | 99 |
------------------------|-------------|
```

Durch Stellenwerte sind wir also in der Lage, aus den beiden Zahlen `9` und `9` einen Wert darzustellen, der `|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||` darstellt, neunundneunzig Sachen.

Wollen wir nun die nächst höhere Zahl darstellen, brauchen wir eine weitere Stelle. Wie schon bei der `10`, muss diese Stelle in der Lage sein, exakt die Zahl darzustellen, die nach dem Wert von `99` kommt. **Die `100`**.


Stellen wir die Zahl `379` im Stellenwertssystem dar.
```
|-------------------------------|
| Stellenwert | 100 |  10 |   1 |\
|-------------------------------|  Stellenwert x Ziffer-Wert für jede Stelle/Spalte
| Ziffer-Wert |   3 |   7 |   9 |/
|-------------------------------|--------------------|
|        Wert | 300 |  70 |   9 | 300 + 70 + 9 | 379 |
--------------------------------|--------------------|
```

Mit 3 Stellen ist die höchste Zahl, die wir darstellen können, die `999`, nämlich wenn alle Stellen ihren höchstmöglichen Ziffern-Wert im Dezimalsystem erhalten. Folglich ist der nächste Stellenwert **`1000`**.

Hier lässt sich ein Schema erkennen, denn jeder höhere Stellenwert ist immer der vorige Stellenwert multiplizert mit `10`. Warum mit `10`? Na weil wir `10` Ziffern zur Verfügung haben!

Die erste Stelle ist, wie schön erwähnt, immer `1`. Dies lässt sich auch mathematisch darstellen und es wird euch erklären, warum das so ist. Der zweite Stellenwert ist `10 x 1`, also der vorige Stellenwert `1` multipliziert mit `10`, der Anzahl unserer Ziffern. Der nächste Stellenwert wäre `10 x 10`, also `100`. Dasselbe Schema. Als nächstes kommt `10 x 100`, also `1000`. Danach, logischerweise, `10 x 1000`, `10.000`. So reisen die Stellen immer höher und geben uns die Möglichkeit, damit sämtliche Werte darzustellen, die wir uns vorstellen können.

### Potenzen
Wie können wir eine Zahl darstellen, die sich selbst immer höher mit einer anderen multipliziert? **Mit Potenzen!**

Nochmal für diejenigen, die es nicht kennen: Die Aussage `10 * 10 * 10 * 10 * 10` lässt sich auch als `10^5` darstellen. Es wird _Zehn hoch vier_ ausgedrückt. Dies ist die übliche Schreibweise in normalen Computertexten, normalerweise wird die hintere Zahl, also die `4`, hochgestellt. Die `10` nennt man in diesem Fall **Basis**. Die `5` ist der sogenannte **Exponent**. Sinngemäß wird hier die Aussage getroffen, dass **10 insgesamt 5-mal mit sich selbst multipliziert wird**.

Eine weitere, wichtige Regel für Potenzen ist folgende: **Jede Potenz mit dem Exponenten `0` ergibt `1`**. `10^0` ist `1`, `5^0` ist `1`, `2^0` ist `1` und auch `16^0` ist `1`. Wenn ihr euch fragt, warum das so ist, kann ich euch es nicht genau sagen. Die Antwort darauf ist komplex. Es lässt sich aber mathematisch beweisen, nämlich so: `x^0 = x^(-1+1) = x^(-1) * x^1 = 1/x * x = 1`.  

Für unsere Zahlensysteme ist dies auch nur vorteilhaft, denn wir können unsere Stellenwerte prima in Potenzen darstellen. Das funktioniert auch tatsächlich für jedes Zahlensystem.

Wir fangen von rechts bei `0` an zu zählen, damit unsere Potenzen hinhauen.

Schreiben wir also gleich `10^6`, reden wir von `10 x 10 x 10 x 10 x 10 x 10` und damit von `1000000`. Die Zehnerpotenzen lassen sich dank unseres Dezimalsystems wunderschön im Kopf errechnen, so bedeutet eine `10^18` im Endeffekt nichts weiter als **Eine Eins mit 18 Nullen**. Der Exponent stellt gleichzeitig die Anzahl der Nullen dar.

Schreiben wir einfach mal die Zahl `3.146.785`, also **dreimillioneneinhundertsechsundvierzigtausendsiebenhundertfünfundachtzig**, in eine Stellenwerts-Tabelle wie oben und nutzen statt der Zahlenwerte für unsere Stellen die entsprechenden Potenzen.
```
|--------------------------------------------------------------------------------------------------------------------|
| Stellenwert | 10^6 (1.000.000) | 10^5 (100.000) | 10^4 (10.000) | 10^3 (1.000) | 10^2 (100) | 10^1 (10) | 10^0 (1) |\
|--------------------------------------------------------------------------------------------------------------------|  Stellenwert x Ziffer-Wert für jede Stelle/Spalte
| Ziffer-Wert |                3 |              1 |             4 |            6 |          7 |         8 |        5 |/
|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
|        Wert |        3.000.000 |        100.000 |        40.000 |        6.000 |        700 |        80 |        5 | 3.000.000 + 100.000 + 40.000 + 6.000 + 700 + 80 + 5 | 3.146.785 |
---------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------|
```

Das ist im Grunde echt cool, denn das gesamte Dezimalsystem lässt sich so mit einer Formel beschreiben: `10^n`.

Das ist im Grunde noch cooler, denn **alle** Zahlensysteme lassen sich so beschreiben!

# Das Binärsystem


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