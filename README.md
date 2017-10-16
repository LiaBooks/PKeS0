<!--

author:   Georg Jäger

email:    gjaeger@ovgu.de

version:  1.0.0

language: de_DE

narrator:  Deutsch Female

-->

# PKES 0

                                       --{{0}}--
Willkommen bei dem eLearning-System *eLab*! Es wird euch bei der Bearbeitung der
praktischen Aufgaben zur Vorlesung
`Prinzipien und Komponenten eingebetteter Systeme` unterstützen.

                                       --{{1}}--
Alle Kurse findet ihr auch online und falls ihr Verbesserungen, Korrekturen,
eigene Versionen oder vertiefende Kurse anbieten wollt, so freuen wir uns über
eure Beiträge ;-)


Source: * https://github.com/liaScript/PKeS0 *

__Ziele:__

1. Kennenlernen der Kurs- und Entwicklungsumgebung
2. Einführung in Programmierung und Kommunikation mit dem Arduino
   _(Kennenlernen eures Microcontrollers)_


## Entwicklungsumgebung

                                       --{{0}}--
Falls ihr euch erfolgreich angemeldet habt dann müsstet ihr eine IDE sehen, wie
sie im Bild dargestellt ist. Diese besteht grob gesehen aus vier Elementen, die
in den folgenden Folien kurz vorgestellt werden.

![ide overview](https://github.com/liaScript/PKeS0/raw/master/pics/ide0.png)<!-- width: 100% -->

                                       --{{1}}--
Bitte fliegt kurz über die folgenden IDE-Abschnitte und macht euch mit den
Bedienelementen vertraut.

### IDE

Im folgenden wird zunächst ein kleiner Überblick über den eLab-Editor gegeben.

#### IDE - Tabs

                                       --{{0}}--
Die verschiedenen Dateien könnt ihr über die jeweiligen Tabs ansteuern, wobei
der erste Tab einen Link auf die serielle Ein- und Ausgabe zur Verfügung stellt.

![editor](https://github.com/liaScript/PKeS0/raw/master/pics/editor.gif)<!-- width: 100% -->

#### IDE - Dateien

                                       --{{0}}--
Über das DropDown-Menü könnt ihr neue Dateien hinzufügen, beziehungsweise alte
Dateien umbenennen oder löschen.

![file handling](https://github.com/liaScript/PKeS0/raw/master/pics/files.gif)<!-- width: 100% -->

                                       --{{1}}--
Sollte es manchmal nicht möglich sein Dateien, wie zum Beispiel `Display.h` zu
erstellen, dann existieren diese Dateien bereits im Hintergrund und sind Teil
unserer vorgefertigten Aufgabe. Diese Dateien sind dann leider nicht sichtbar
für euch. Probiert einfach einen andere Namen ;-)


#### IDE - Compiler

                                       --{{0}}--
Im Hintergrund läuft ein normaler Arduino-Compliler, sollte ausnahmsweise eines
eurer Programme einen Fehler haben, dann wird euch dieser auch direkt in der IDE
an der entsprechenden Stelle angezeigt.

![editing and compilation](https://github.com/liaScript/PKeS0/raw/master/pics/editing.gif)<!-- width: 100% -->

                                       --{{1}}--
Falls alles geklappt hat, dann seht ihr das durch einen grünen Execution-Button.
Um euer Programm dann auch auf einen Roboter zu flashen, müsst ihr euch auf
einem freien Roboter einwählen.

#### IDE - Versionierung

                                       --{{0}}--
Euch steht ein lineares Versionssystem zur Verfügung, ihr könnt durch alle
Lösungen gehen und alte Funktionierende Versionen auch kompilieren und wieder
ausführen, nur diese editieren oder Verzweigungen einzufügen ist nicht möglich.

![linear versioning](https://github.com/liaScript/PKeS0/raw/master/pics/versions.gif)<!-- width: 100% -->


### Roboterauswahl

                                       --{{0}}--
In der linken Leiste seht ihr alle zur Verfügung stehenden Roboter. Freie
Roboter erkennt ihr an der grünen Farbe. Ihr könnt einzeln die Roboter
auswählen, jeder Klick verändert gegebenenfalls auch den Video-Stream. Per
Doppel-Klick loggt ihr euch auf einem Roboter ein und sperrt dann den Zugriff
für die anderen Nutzer.

![robot selection](https://github.com/liaScript/PKeS0/raw/master/pics/robot.gif)<!-- width: 100% -->

                                       --{{1}}--
Wichtig ist, dass ihr euch nur auf einem Roboter einloggt, wenn ihr euer
Programm auch tatsächlich ausführen wollt. Zum reinen entwickeln benötigt ihr
keinen Roboter, also solltet ihr diese für eure Komilitonen freigeben.


### Video-Stream

                                       --{{0}}--
Die Video-Streams sind an die Roboter gekoppelt, ihr habt die Möglichkeit
zwischen drei Stream-Qualitäten zu wählen oder diesen auszuschalten.

![show video-stream](https://github.com/liaScript/PKeS0/raw/master/pics/lifestream.gif)<!-- width: 100% -->

                                       --{{1}}--
Beim Klick auf den unteren Link könnt ihr euren Stream entkoppeln und in einem
anderen fenster anzeigen lassen.

### ArduinoView 1

                                       --{{0}}--
Wenn man über einen Web-Zugriff auf eingebettete Hardware verfügt, warum sollte
man diese dann nicht auch mit den Möglichkeiten einen modernen Web-Browsers
programmieren? [Arduinoview](https://gitlab.com/OvGU-ESS/arduinoview) ist ein
Tool, welches es euch ermöglichen soll euren Roboter mit Web-Elementen
fernzusteuern aber auch eure Daten zu visualisieren, wie es eine serielle
Schnittstelle nicht kann.

![arduinoview](https://github.com/liaScript/PKeS0/raw/master/pics/execute.gif)<!-- width: 100% -->

                                       --{{1}}--
Wie in der Abbildung dargestellt, flashed ihr euer Programm auf euren zuvor
ausgewählten Roboter mit Klick auf den `Execute` Button. Wenn sich dieser rot
färbt, dann bedeuted dies, das euer Programm gestartet ist. Eine zusätzliche
Ausgabe über die serielle Schnittstellt sollte als einfache Log- sowie Debug-
Möglichkeit genutzt werden.

### ArduinoView 2

                                       --{{0}}--
Die zweite Abbildung zeigt wie eure Lösung aussehen kann. Ihr müsst dabei nicht
immer den Roboter neu flashen um euer Programm neu zu starten. Ein einfacher
Klick auf den Reset-Button reicht und euer Roboter startet neu...

![arduinoview](https://github.com/liaScript/PKeS0/raw/master/pics/solution.gif)<!-- width: 100% -->


## Probleme?

Sollten Probleme bei der IDE oder mit den Robotern auftreten, so erstellt bitte
einen aussagekräftigen kleinen Bericht. Oben unter dem Link __Issue__!


## Aufgabe 0

                                       --{{0}}--
Um zunächst einen Eindruck von dem System, sowie dem damit verbundenen
Arbeitsablauf, zu bekommen, sollt ihr in dieser *nullten* Aufgabe das *Hello*
*World*-Programm der eingebetteten Programmierung implementieren; das An- und
Ausschalten einer LED.

1. Inbetriebnahme (sollte abgeschlossen sein)
2. Embedded `Hello World` --> Blinken einer LED
   * Kennenlernen des Microcontrollers:
     [AVR ATmega32U4](http://www.microchip.com/wwwproducts/en/ATmega32u4)
   * Kennenlernen der Hardware: (Peripherie, d.h Sensorik und Aktorik)
     [Schaltbelegungsplan](https://github.com/liaScript/PKeS0/blob/master/materials/robubot_stud.pdf?raw=true)
   * Debug- und Logging-Ausgaben: mittels der seriellen Schnittstelle
   * Interaktion mit dem Microcontroller via
     [Arduinoview](https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md)




                                       --{{1}}--
Während der Bearbeitung der Aufgabe sollen verschiedene Themen zur
Programmierung eingebetteter Systeme angesprochen werden.  Wesentlich für den
weiteren Verlauf der Vorlesung ist, dass ihr den Mikrocontroller, AVR
ATmega32U4, kennenlernt. Dieser wird während der Aufgaben zu programmieren sein.

                                       --{{2}}--
Eines der Ziele dieser Aufgabe ist es, eine LED an dem Roboter zum Blinken zu
bringen. Neben dem Mikrocontroller selbst, solltet ihr dazu den
Schaltbelegungsplan studieren. So könnt ihr herausfinden, wie periphäre
Komponenten, also Sensorik und Aktorik, an den Mikrocontroller angeschlossen
sind.

                                       --{{3}}--
Da die Programmierung eingebetteter Systeme, wie auch bei der
Anwendungsprogrammierung, zuweilen das Aufspüren und Beseitigen von Fehlern in
der Implementierung beinhaltet, werdet ihr das Framework
[Arduinoview](https://gitlab.com/OvGU-ESS/arduinoview) benutzen um
Daten/Zustände des Mikrocontrollers zu visualisieren und Funktionalitäten ein-
und auszuschalten.


**Ziel(e)**

* Recherchieren der nötigen Informationen zur Bearbeitung einer Aufgabe. Welche
  Dokumente sind relevant?
* Einarbeiten in die Programmierung des Systems. Wo finde ich Hilfe und
  Erklärungen zu Bibliotheken und Funktionen?
* Implementieren der Lösung entsprechend der Recherchierten Informationen. Wie
  funktioniert der Kompilierungs-, Assemblierungs- und Linkprozess für
  eingebettete Systeme?


### Weitere Informationen

**[C](https://en.wikipedia.org/wiki/C_%28programming_language%29)/[C++](https://en.wikipedia.org/wiki/C%2B%2B):**

                                       --{{0}}--
Da im Bereich der Programmierung eingebetteter Systeme die Programmiersprache
C/C++ vorherrscht, solltet ihr euch durch Tutorials, Bücher oder Videos
entsprechend einarbeiten. Im speziellen sind Bitoperationen zur Bearbeitung der
*nullten* Aufgabe, aber auch zur Programmierung von Mikrocontrollern im
allgemeinen, hilfreich.


* Tutorials: http://www.learncpp.com
* Bücher: https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list
* Videos: https://www.youtube.com/watch?v=Rub-JsjMhWY

  !![C++Tutorial](https://www.youtube.com/embed/Rub-JsjMhWY)<!--
    width: 560px;
    height: 315px;
  -->

* Bitoperationen: https://de.wikipedia.org/wiki/Bitweiser_Operator


**Eingebettete Programmierung:**

                                       --{{1}}--
Für Interessierte gibt es darüber hinaus auch Tutorials, die direkt auf die
Programmierung eingebetteter Systeme eingehen. Für die Bearbeitung der Aufgaben
solltet ihr sowohl das Datenblatt des Mikrocontrollers, als auch den
Schaltbelegungsplan studieren.

* Tutorials für eingebettet Systeme: https://www.mikrocontroller.net/articles/AVR-Tutorial
* Arduino Serielle I/O Funktionen: https://www.arduino.cc/en/reference/Serial
* Arduino Blink Beispiel: https://www.arduino.cc/en/Tutorial/Blink
* circuits.io - Autodesk Circuits: https://circuits.io


**PKeS:**

* Datenblatt des AVR ATmega32U4: http://www.atmel.com/Images/Atmel-7766-8-bit-AVR-ATmega16U4-32U4_Datasheet.pdf
* Schaltbelegungsplan: https://github.com/liaScript/PKeS0/blob/master/materials/robubot_stud.pdf?raw=true
* Arduinoview: https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md
* ArduinoLib: https://github.com/fesselk/ArduinoviewLib


### Problemstellung

                                       --{{1}}--
In der *nullten* praktischen Aufgabe sollt ihr zunächst eine LED auf dem Roboter
zum Blinken bringen, bevor ihr mit Hilfe des Frameworks *Arduinoview* Daten des
Mikrocontrollers visualisiert.

**Teilaufgaben:**

1. Lasst eine LED auf dem Roboter periodisch blinken.
2. Nutzt *Arduinoview* um eine LED auf dem Roboter ein- und auszuschalten.
3. Visualisiert Daten, die auf dem Mikrocontroller generiert wurden, mit Hilfe
   von *Arduinoview*.


#### Teilaufgabe 1

                                       --{{0}}--
In dieser Aufgabe sollt ihr zwei LEDs konfigurieren und sie unterschiedlich
ansteuern.

**Ziel:** Konfiguriert 2 LEDs und schaltet sie ein und aus.

                                       --{{1}}--
Im ersten Teilschritt konfiguriert ihr PIN 31 und einen weiteren PIN eurer Wahl,
an dem eine LED angeschlossen ist (!), als Ausgang. Außerdem implementiert ihr
eine Funktion um die LED an PIN 31 mit einer Periodendauer von 0.5 Sekunden
blinken zu lassen.

                                       --{{2}}--
Im zweiten Teilschritt schaltet ihr das Blinken ein, nach dem der Benutzer eine
entsprechende Eingabe durch die serielle Schnittstelle an den Mikrocontroller
gesendet hat (z.B.: 'B' für 'Begin'). Sendet der Nutzer ein weiteres
Zeichen (z.B.: 'S' für 'Stop') soll das Blinken beendet werden.

**Teilschritte:**

1. Konfiguriert den PIN 31 und einen weiteren PIN, an dem eine LED angeschlossen
   ist, als Ausgang. Dies soll in der Funktion `setupLED()` geschehen.
   Implementiert darüber hinaus die Funktion `blink()`, in der die LED, die an
   `PIN 31` angeschlossen ist, ein- und wieder ausgeschaltet wird. Implementiert
   eine Periodendauer von 0.5 Sekunden.

2. Startet das Blinken nachdem der Nutzer ein entsprechendes Kommando über die
   serielle Schnittstelle gesendet hat, z.B. ein 'B'. Stoppt das Verhalten, wenn
   ein weiteres Kommando, z.Bsp. ein 'S', gesendet wird.


#### Teilaufgabe 2

**Ziel:** Nutzt *Arduinoview* zur Interaktion mit dem Nutzer und zum
**Visualisieren von Daten.

                                       --{{1}}--
In der letzten Teilaufgabe habt ihr gelernt wie ihr einzelne PINs an dem
Mikrocontroller zur Ausgabe von digitalen Signalen konfiguriert und eine
einfache Interaktion mit dem Nutzer über die serielle Schnittstelle realisiert.

                                       --{{2}}--
In dieser Teilaufgabe soll das Verhalten des Mikrocontrollers erweitert werden.
Diesesmal soll *Arduinoview* für die Interaktion genutzt werden.

                                       --{{3}}--
Im ersten Teilschritt sollt ihr dazu das Klicken auf den Button 'LED On/Off'
nutzen, um die von euch gewählte LED, d.h. nicht die LED an PIN 31, ein- bzw.
auszuschalten.

                                       --{{4}}--
Im zweiten Teilschritt fügt ihr der Visualisierung durch *Arduinoview* ein
Diagramm hinzu.

                                       --{{5}}--
Das zuvor hinzugefügte Diagramm soll in dem dritten Teilschritt genutzt werden,
um alle 500 ms neue Daten anzuzeigen. Die Daten, die angezeigt werden sollen,
werden durch die bereits vorhandenen Funktionen `data0()` und `data1()`
generiert. Ihr müsst lediglich die Funktion `sendValues()` implementieren, um die
Daten an das erstellte Diagramm zu senden.

                                       --{{6}}--
Im letzten Teilschritt fügt ihr *Arduinoview* noch einen weiteren Button 'Graph
On/Off' hinzu um die Visualisierung der Daten durch den Graphen ein- bzw.
auszuschalten.

**Teilschritte:**

1. Nutzt den Button 'LED On/Off' um die zweite LED ein- bzw. auszuschalten.
2. Generiert ein Diagramm mit Hilfe von *Arduinoview*.
3. Visualisiert die Daten, die durch die Funktionen `data0()` und `data1()`
   generiert werden, in dem neuen Diagramm. Alle 500 ms sollen neue Daten
   gesendet werden.
4. Fügt einen Button zum ein- und ausschalten des Sendens der Daten an das
   Diagramm hinzu.


## Quellcodeverständnis

                                       --{{1}}--
Nachdem ihr nun erste Erfahrungen mit der Implementierung eingebetteter Systeme
sammeln konntet, haben wir noch ein paar kurze Fragen an euch, die ihr mit euren
Tutoren in den Übungen diskutieren solltet:

**Fragen zum Quellcode:**


1. Welchen Nachteil hat die Funktion `delay([ms])`?

   Stellt einen Programmablauf mit einer Funktionalität (z.B. nur das Blinken
   der LED) mit einem Programmablauf mit mehreren Funktionalitäten (z.B. das
   Blinken der LED zusammen mit dem Senden von Daten an das Diagramm) gegenüber.

2. Welche Unterschiede ergeben sich software- und hardwareseitig, wenn ein PIN
   als Ein- oder Ausgang konfiguriert wird?

3. Was ist ein Baud?

4. Wozu wird in der C/C++ Programmierung die `#include` Direktive verwendet und
   welche Gemeinsamkeiten/Unterschiede hat sie zu weiteren Befehlen;
   beispielsweise einem `#define`?

## Quizze

### Macros 1

Welche Aussagen treffen auf C-Macros zu?

    [[X]] Beginnt immer mit einem `#`.
    [[ ]] Wird vom Compiler augerufen.
    [[X]] Kann **nur** während des Compilevorgangs Programmelemente ersetzen.
    [[X]] Ist nur eine Textersetzung.
    [[ ]] Macros können genutzt werden um neue Macros zu erzeugen.
    [[ ]] `#include` ist kein Makro.
    [[[

1. Ja, neben `#define` oder `#include` gibt es noch weitere Macrodirektiven.
2. Nur der Präprozessor ersetzt Macros,
3. wobei es sich um eine reine Textersetzung handelt.
4. Dieser Schritt wird vor dem eigentlichen Kompilieren durchgeführt
5. und nur einmalig, Rekursion oder Schleifen oder komplexere
   Programmersetzungen (wie in Lisp, Elixir, etc.) sind nicht möglich.
6. Beim `#include` wird der Inhalt einer gesamten Datei eingesetzt. Der
   Unterschied zwischen den Angaben `"file1.h"` und `<file2.h>` liegt am
   Speicherort der Datei. Erstere ist lokal im gleichen Verzeichnis und die
   zweite in einem Systemverzeichnis.


https://de.wikipedia.org/wiki/C-Pr%C3%A4prozessor

]]]

### Macros 2

``` C
#define square(X) X*X

square(3+2); // wie lautet das Ergebnis?
```

Wie sieht das Resultat der folgenden Quadrierung aus, bitte gib dein Ergebnis
als Zahl in das folgende Textfeld ein:

    [[11]]
    [[[

Das Ergebnis der Ersetzung ist `3+2*3+2` also ist hier die richtige Antwort 11
und nicht 25. Ihr solltet also durchaus Vorsichtig mit Makros umgehen ...

]]]


### Ports

Wie viele general purpose PORTs hat der verwendete Controller

    [[ ]] 4
    [[X]] 5
    [[ ]] 6
    [[ ]] 7
    [[[

Der Atmel ATmega32U4 hat 5 GPIO (General Purpose Input-Output) Interfaces - B, C,
D, E und F. Interessanter Weise wird PORTA einfach ausgelassen. Probieren
Sie mal aus für diesen die entsprechenden Register PINA oder PORTA zu beschreiben

Handbuch Seite 4: Block Diagram

]]]

### DDRx Register

Welche Aufgabe übernimmt das DDRx Register bei der Konfiguration bezüglich eines
Pins?

    [[X]] Festlegung des Zustandes (high, low)
    [[X]] Definition des Pins als Eingang oder Ausgang
    [[ ]] Datenformat des Eingangs
    [[ ]] Taktrate der Leseoperationen
    [[ ]] Klassifikation der physischen Verfügbarkeit
    [[[

Der Name Data Directory Register ist Programm, die Bits dieser Register, die auf
dem Controller für B, C, D, E und F existieren definieren die Richtung des
Betriebs eines Pins (0 = Eingang, 1 = Ausgang).

]]]

### Widerstand?

Der elektrische Schaltplan zeigt das jede Diode LED 1-4 mit einem Widerstand
verbunden ist. Was ist dessen Aufgabe?

    [[ ]] Konfiguartion des Farbprofils der Diode
    [[X]] Beschränkung des Stromflusses durch die Diode
    [[ ]] Filtern und Glätten von Störimpulsen
    [[ ]] Galvanische Trennung des Prozessors von der Umgebung
    [[[

Als Faustformel kann für Standarddioden von einer maximal zulässigen Stromfluß
von 20mA und einer Durchflussspannung von 2.2V ausgegangen werden. Unser
Mikrocontroller wird mit 3.3V betrieben Der (überdimensionierte) Widerstand
übernimmt die Begrenzung des Stromflusses durch die Diode und die weniger
kritische Spannungsanpassung. Damit wird eine lange Lebensdauer garantiert.

]]]


### Debugging?

Aussgaben über die serielle Schnittstelle werden bei eingebetteten Systemen
häufig für das Debugging genutzt. Was sind die Konsequenzen, wenn das Schreiben
dieser Ausgaben für die finale Version abgeschalten wird?

    [[ ]] Speicherüberlauf
    [[X]] Verringert Stromaufnahme des Controllers
    [[ ]] Reduzierung der Programmgröße
    [[X]] Änderung des Zeitverhaltens des Programms
    [[[

Ein zu erwartendes Resultat, wenn die Serielle Schnittstelle vollständig
abgeschalten wird, ist die Verringerung der Stromaufnahme des Prozessor. Dazu
genügt es aber nicht nur auf die Schreib-/Lese-Operationen zu verzichten,
vielmehr muss die Schnittestelle deaktiviert werden (Standardzustand beim
Booten).

Die Schreib-/Lese-Operationen verlangen eine nicht unerhebliche
Prozessorleistung. Entsprechend ändert sich die Laufzeit des Programms, was in
zeitkritischen Anwendungen bei "fragwürdiger" Programmierung zu einem gänzlich
veränderten Verhalten führen kann.

]]]
