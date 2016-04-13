HTTP for Noobs
==============


# Was ist HTTP?
HTTP steht für Hypertext Transfer Protocol.

Es ist also ein Protokoll, dass Hypertext übertragen kann.



# Was ist ein Protokoll?
Wenn zwei Computer miteinander kommunzieren müssen, tun sie dies in einer Art Sprache.

Deutsch und Englisch lassen sich beispielsweise als 2 unterschiedliche Protokolle sehen.

Es gibt Menschen, die nur Deutsch können. Diese werden sich nicht mit Menschen verständigen können, die nur Englisch sprechen.

Sprechen zwei Einheiten dieselbe Sprache, können sie miteinander kommunizieren.


Im Internet gibt es diverse Protokolle, die unseren gesamten Datenfluss handhaben und dafür sorgen, dass unsere Facebook-Nachricht auch beim Empfänger ankommt.

**Beispiele bekannter Protokolle:**
- **IMAP** (Internet Message Access Protocol) wird z.B. zur Einsicht des E-Mail Postfachs benötigt
- **SMTP** (Simple Mail Transfer Protocol) wird benötigt, um eine E-Mail an einen anderen Rechner zu senden
- **FTP** (File Transfer Protocol) wird benötigt, um auf Dateien anderer Rechner zugreifen zu können


Damit die Rechner miteinander kommunizieren können, verbinden sie sich auf einen offenen Port des Rechners und stellen ihre Anfrage.
Wie das visuell aussehen kann, wird weiter unten als Beispiel erklärt.



# Was ist ein Port?
Die meisten Protokolle sind einem Port zugewiesen, auf dem sie standardmässig hören. Damit weiß man, wo sich gewisse Dienste befinden.

Das HTTP Protokoll beispielsweise hört standardmässig auf den Port 80.
Dies führt dazu, dass wir eben nicht **google.de:80** eingeben müssen, um Google aufzurufen. Der Browser weiß selbst: "Aha, HTTP, das liegt doch auf 80! Den nehm ich standardmässig".

Dies heißt allerdings nicht, dass z.B. auf dem Port 2456 kein Webserver laufen kann. Es gibt diverse Anwendungsfälle (z.B. Entwicklung, Proxy oder mehrere Webserver auf einem Server) in denen es Sinn macht, auch auf einem anderen Port HTTP zu sprechen.

Wollen wir diesen Port dann explizit nutzen, müssen wir ihn anhängen (Beispiel: **meine-dev-kiste.local:8080**)



# Was ist Hypertext?
Hypertext ist normaler Text, allerdings ist dieser Text speziell strukturiert, damit sich einige Elemente gesondert verarbeiten lassen. Diese Strukturierung ist optional, d.h. es kann auch einfach ganz normaler Text übertragen werden.

Ein Beispiel dafür ist z.B. eine Tabelle, eine Grafik, fett-geschriebene oder kursiver Text, Videos, Musik oder auch Links zu anderen Hypertext-Dokumenten.

Diese Strukturierung findet in verschiedenen Formen statt, die wichtigste allerdings ist die Definitionssprache HTML (Hypertext Markup Language, dazu mehr in HTML für Noobs).

In HTML lässt sich fettgeschriebener Text z.B. darstellen, indem man ihn mit `<strong>fetter text hier</strong>` umgibt.

Der Browser empfängt diese Elemente, sieht, dass man fetten Text haben möchte und macht daraus fetten Text.


Dies lässt sich so weit treiben, dass man mithilfe von Hypertext ganze Applikationen erstellen kann, die normalen Desktop-Programmen in nichts nachstehen.



# Wie sieht HTTP-Kommunikation aus?
Spielen wir doch einfach mal Browser. Der Browser ist quasi eine GUI (Graphical User Interface) für das HTTP Protokoll (und auch andere, dazu kommen wir später).

Wenn du **google.de** in die Adresszeile deines Browsers eingibst und Enter drückst, passiert folgendes:



### Verbindung
Der Browser sieht, dass du nicht explizit verschlüsseln willst und du keinen Port angegeben hast. Er ändert die angegebene Adresse auf **http://google.de:80** ab und weiß damit:
- Wir nutzen **HTTP** als Protokoll
- Der Server, den wir abrufen, hat den Namen **google.de**
- Der Port, auf den wir verbinden, lautet **80** 



### Request (Anfrage)
Der Browser verbindet sich auf den Endpunkt **google.de:80**. Auf diesen Port lauscht der Webserver, der die Google-Suchmaschine ausliefern soll. 
Nun sendet der Browser ein HTTP-Request an den Webserver. Dieses sieht z.B. folgendermaßen aus:

```
GET /search?q=meine+suche HTTP/1.1
Host: google.de
Connection: close
```

Dies ist wohl die einfachste Form eines HTTP Requests.

#### LF vs. CRLF
Ich weise an dieser Stelle darauf hin, dass es sich bei dem Zeilenumbruch nicht um ein klassisches LF (Line-Feed, `\n`) hält, sondern um das Windows-CRLF (Carriage-Return + Line-Feed, `\r\n`).
Soll heißen, der Zeilenumbruch wird nicht mit einem Zeichen dargestellt, sondern mit 2 Zeichen.
Diese Zeichen sind für uns unsichtbar, es sind Steuerzeichen, die sitzen aber am Ende jeder Zeile einer HTTP-Nachricht. Um diese Zeichen zu erzeugen, öffnet Notepad.exe unter Windows und drückt ein paar mal Enter. Wenn ihr nun den Text zwischen zwei Zeilen kopiert (Ihr markiert zwei Zeilen, es werden dabei aber keine Zeichen markiert), habt ihr ein `\r\n` markiert. Es ist quasi der Zeilenumbruch selbst, der das Zeichen darstellt.

In diversen Editoren (Sublime Text, Notepad++) könnt ihr diese Steuerzeichen auch sichtbar machen, um es besser nachvollziehen zu können.


#### HTTP Methoden
Das `GET` steht für die **HTTP Methode**. Dies ist quasi die "Funktionalität", die wir in HTTP nutzen wollen.
Folgende HTTP Methoden werden für euch mittelfristig noch eine wichtige Rolle spielen:

- **GET** um einfach nur den Inhalt zu holen. Wir senden nichts, wir wollen einfach nur die Seite sehen bzw. holen.
- **POST** um Daten zu übermitteln (z.B. Kontaktformular). Ein Beispiel eines POST kommt gleich. HTML unterstützt primär GET und POST.
- **PUT** um Daten zu erstellen. Ein neuer Datensatz soll angelegt werden. Nutzt man PUT, ist POST die Update-Funktion von vorhandenen Daten
- **DELETE** um Daten zu löschen.

Mit diesen 4 Methoden lässt sich das sogenannte CRUD-Prinzip anwenden (Create, Read, Update, Delete). Dazu vielleicht später mehr.


#### Query String
Das `/search?q=meine+suche` ist das sogenannte **Request Target**.
Dies ist üblicherweise (und für euch eigentlich immer) ein relativer Pfad zu einer Datei.

Es ist die Aufgabe des Webservers und der dahinter liegenden Web-Applikation, diesen Pfad zu interpretieren. Dies heißt auch, dass z.B. `/search` nicht unbedingt eine Datei sein muss, die irgendwo auf dem Server liegt, sondern auch ein Programm sein kann, dass den zurückzusendenden Inhalt erst dynamisch generiert.

Um eben dieser Dynamik die Möglichkeit zu geben, seine Anfrage zu spezifizieren, gibt es den sogenannten **Query String** oder auch einfach nur **Query**.
Das wäre in unserem Beispiel der `q=meine+suche` Part und folgt immer hinter einem `?` im Pfad.

Der Server kann diesen Query String nun verarbeiten und daraus z.B. Optionen oder Variablen bilden (`var q = 'meine suche'`).

`/search` stellt in diesem Fall bei Google die Suchmaschine selbst dar, mit `?q=meine+suche` übergeben wir unsere Suchanfrage.

Die Suchmaschine nimmt nun unseren `q`-Wert (Der Name ist frei wählbar, Google hat sich für `q` wie in `query` entschieden. Query bedeutet allgemein "Abfrage")

Hat die Suchmaschine unsere Ergebnisse aus der Datenbank geholt, verschönert sie diese mit etwas HTML und antwortet damit auf unsere Anfrage.


#### HTTP Header
Am Ende unserer ersten Zeile im Request steht `HTTP/1.1`, was dem Server mitteilt, welche HTTP-Version wir unterstützen, damit dieser die anschließende Übertragung optimieren kann.

Darunter folgen die sogenannten **HTTP-Header** (Kopfdaten). Wir haben in unserem HTTP-Request genau 2 Header, **Host** und **Connection**.

**Host** ist auf `google.de` gesetzt. Bedenkt, dass jedes mal vor der Verbindung der Name `google.de` in die IP-Adresse (`216.58.214.99`) umgewandelt wird. Der Server weiß also quasi gar nicht, welche Website wir genau aufgerufen haben, nur, dass sie sich irgendwo auf seinem Server befindet. Der Host-Header teilt dem Server noch mal explizit mit, um welche Website es sich handelt.

**Connection** steht auf `close`, damit der Server nach unserer Verbindung die Verbindung selbst wieder schließt. Ein Browser nutzt z.B. meist `keep-alive` und sagen dem Server, dass er die Verbindung noch nicht schließen soll, da wir eventuell noch weitere Anfragen stellen (z.B. für die Bilder der Seite).


### Die Response (Rückgabe)

Hat der Server seine Antwort gefunden, schickt er sie in einem bestimmten Format wieder zurück. Dieses enhält Informationen darüber, um was für eine Art Daten es sich handelt, die wir da angefragt haben (z.B. Dateityp, Dateigröße) und die Daten selbst.


Haben wir nun unser GET-Request übermittelt, könnte eine Response von Google folgendermaßen aussehen:

```
HTTP/1.1 200 OK
Content-Type: text/html; encoding=utf-8
Content-Length: 103446

<!DOCTYPE html><html>......</html>
```

Hier sagt uns der Server mit `HTTP/1.1` erst mal, dass er die Version 1.1 unterstützt und die Seite mit dieser ausgeliefert hat.

#### Status Code
Danach folgt der sogenannte HTTP Status Code. Den bekanntesten, den `404`-Status Code, habt ihr definitiv schonmal gelesen, denn dieser wird ausgeworfen, wenn ein Webserver eine gesuchte Datei nicht findet. Der Status `200` steht hier für "Alles gut gelaufen, unten im Body ist deine Datei"

Nach dem Status Code kommt eine kleine Beschreibung des Fehlers. Bei dem 200er ist das üblicherweise einfach nur `OK`, kurz und knackig auf den Punkt gebracht. Bei 404ern ist dies z.B. standardmässig `Not Found`.

Hier mal eine kleine Liste von Status-Codes, die ihr öfter sehen werdet:
- **200 OK** steht für eine erfolgreiche Kommunikation
- **301 Moved Permanently** ist eine Umleitung und teilt dem Browser mit, dass er den Inhalt an einer anderen Stelle findet und an welcher. Der vorher angefragte Pfad sollte nicht mehr verwendet werden.
- **302 Found** ist allgemeine Umleitung, z.B. eine Abkürzung. Der vorher angefragte Pfad kann ruhig weiter verwendet werden.
- **400 Bad Request** bedeutet, eure HTTP-Anfrage war falsch formuliert.
- **401 Unauthorized** bedeutet, dass man sich nicht authentifiziert hat, dies aber notwendig zum Einsehen der Seite ist.
- **403 Forbidden** bedeutet, man ist zwar womöglich authentifiziert, aber man hat nicht die erforderliche Berechtigung, um den Inhalt einzusehen.
- **500 Internal Server Error** bedeutet, etwas auf dem Webserver funktioniert nicht korrekt, z.B. ein Fehler im Script.


Nach dem Status Code folgen wieder einige HTTP-Header, diese sind hier **Content-Type** und **Content-Length**.

**Content-Type** beschreibt den Inhaltstypen. Der erste Wert `text/html` ist ein sogenannter **MIME-Type** und stammen aus der E-Mail Welt. Es gibt hunderte verschiedene MIME-Types, die alle jeweils einen anderen Dateitypen beschreiben. Der zweite Teil `encoding=utf-8` sagt, dass unsere Daten unten mit dem UTF-8 Charset enkodiert sind und wir dieses auch nutzen sollten, damit uns die Sonderzeichen korrekt angezeigt werden (z.B. ä, ü, ö, ß)

**Content-Length** beschreibt die Länge unseres Körpers der Nachricht, dem sogenannten **Body**. Hier sind es wohl 103446 Byte an Daten, die uns zugesandt wurden.

Nach einer Leerzeile befindet sich darunter dann der Body. Diesen habe ich hier natürlich gekürzt, dieser wäre nun 103446 Byte lang.


In dem Body befindet sich in diesem Fall Hypertext, den der Browser verarbeitet und visuell darstellt.

Natürlich können auch Bilder, Videos und viele andere Formate via HTTP übertragen werden. Diese lassen sich durch die MIME-Typen steuern.

Gängige MIME-Types sind z.B. folgende:
- **text/plain** ist einfacher Text, wie er z.B. in Notepad.exe geschrieben wird. Dieser wird nicht gesondert verarbeitet, sondern einfach nur ausgegeben.
- **text/html** ist HTML. Sie definiert unsere Seitenstruktur.
- **text/xml** ist XML, eine weniger restriktive Überform von HTML, dazu mehr in XML für Noobs
- **image/png** wäre ein normales PNG-Bild
- **image/jpeg** wäre ein JPG oder JPEG Bild
- **image/gif** wäre ein GIF-Bild
- **application/json** wäre eine Sammlung aus JSON-Daten, dazu mehr in JSON für Noobs
- **application/octet-stream** wäre z.B. ein klassischer Datei-Download einer beliebigen Datei 
- **x-www-form/urlencoded** ist das klassische Formular-Übertragungsformat und beinhält einen Query-String mit unseren Formular-Daten
- **multipart/form-data** wird benötigt, um größere Datei-Uploads auf Websites durchzuführen, da die Requests damit in mehrere Teile geteilt und einzeln übertragen werden.


#### POST-Request
Da wir nun wissen, was ein Query-String, Mime-Types und Content-Length sind, zeige ich euch ein Beispiel eines POST-Requests.

```
POST /login HTTP/1.1
Host: yourpage.com
Content-Type x-www-form/urlencoded
Content-Length: 38
Connection: keep-alive

username=torben&password=mypassword123
```


Dies wäre ein klassisches Login-Request, das aus einem HTML-Login-Formular stammen könnte.

Hier schicken wir Daten an unseren Webserver, nämlich einen Query-String, der einen Benutzernamen `username` mit dem Wert `torben` und ein Passwort `password` mit dem Wert `mypassword123` enthält. Der Server kann diese Daten verarbeiten und z.B. prüfen, ob die Login-Daten korrekt sind und dann entsprechend antworten.

Durch POST-Requests werden jegliche Art von Formular-Kommunikation im Web realisiert.


## Fazit

Rufen wir also eine Website auf, wird erst mal ein HTTP Request gemacht. Beim Aufbau der Seite finden sich z.B. Bilder, JavaScripts, StyleSheets, Videos etc., die ebenfalls geladen werden müssen. Für jedes Element wird ein neues HTTP Request an den Server gesendet und der Server antwortet mit der Response und dem entsprechenden Inhalt.

Nach ein paar Requests hat man dann in der Regel eine vollständige Website, die man im Browser darstellen kann.






Vielen Dank für's Zuhören und viel Spaß beim rumnooben!