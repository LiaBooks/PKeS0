<!--
author:   André Dietrich, Karl Fessel

email:    andre.dietrich@ovgu.de

version:  0.0.2

language: de

narrator: Deutsch Female

comment:  Einführung in das eLab.


@run_main
<script>
events.register("@0", e => {
		if (!e.exit)
    		send.lia("output", e.stdout);
		else
    		send.lia("eval",  "LIA: stop");
});

send.handle("input", (e) => {send.service("@0",  {input: e})});
send.handle("stop",  (e) => {send.service("@0",  {stop: ""})});


send.service("@0", {start: "CodeRunner", settings: null})
.receive("ok", e => {
		send.lia("output", e.message);

		send.service("@0", {files: {"main.c": `@input`}})
		.receive("ok", e => {
				send.lia("output", e.message);

				send.service("@0",  {compile: "gcc main.c -o a.out", order: ["main.c"]})
				.receive("ok", e => {
						send.lia("log", e.message, e.details, true);

						send.service("@0",  {execute: "./a.out"})
						.receive("ok", e => {
								send.lia("output", e.message);
								send.lia("eval", "LIA: terminal", [], false);
						})
						.receive("error", e => { send.lia("log", e.message, e.details, false); send.lia("eval", "LIA: stop"); });
				})
				.receive("error", e => { send.lia("log", e.message, e.details, false); send.lia("eval", "LIA: stop"); });
		})
		.receive("error", e => { send.lia("output", e.message); send.lia("eval", "LIA: stop"); });
})
.receive("error", e => { send.lia("output", e.message); send.lia("eval", "LIA: stop"); });

"LIA: wait";
</script>

@end


-->

# PKES 0: Input & Output

    --{{0}}--
Willkommen bei dem eLearning-System eLab! Es wird euch bei der Bearbeitung der
praktischen Aufgaben zur Vorlesung Prinzipien und Komponenten eingebetteter
Systeme unterstützen.

    --{{1}}--
Alle Kurse findet ihr auch online und falls ihr Verbesserungen, Korrekturen,
eigene Versionen oder vertiefende Kurse anbieten wollt, so freuen wir uns über
eure Beiträge ;-)

Source: * https://github.com/liaScript/PKeS0 *

Ziele:

* Kennenlernen der Kurs- und Entwicklungsumgebung
* Möglichkeiten der Interaktion (Input & Output)
* Einführung in Programmierung und Kommunikation mit dem Arduino (Kennenlernen
  eures Microcontrollers)


## C-Programme

    --{{0}}--
Wir werden die Aufgaben ein wenig mischen. Um die wenigen Roboter nicht in Gänze
auslasten zu müssen werden einige Programme in C geschrieben und auf dem Server
ausgeführt:

``` c main.c
#include <stdio.h>

int main()
{
  printf("Hallo Welt")
  return 0;
}
```
@run_main(hallo_welt)


    --{{1}}--
Wenn du auf play klicks, wird das Projekt auf den Server kopiert, kompiliert und
ausgeführt. Das Programm enthält jedoch einen syntaktischen Fehler, auf den dich
der Editor hinweist. Führst du das fehlende Semikolon in Zeile 5 ein, dann
sollte  das Programm erfolgreich kompilieren und ausgeführt werden.

    --{{2}}--
Wie du jetzt bemerkt haben solltest, hast du eine neue Version deines Ursprungs
Programm erzeugt und kannst auch wieder zu deinen alten Versionen zurückkehren
und diese auch wieder editieren.

    --{{3}}--
Daneben gibt es natürlich auch nicht ausführbaren Code, solche Snippets dienen dann nur der Erklärung oder Verdeutlichung eines Sachverhaltes und besitzen keinen Play-Button.

     {{3-4}}
``` c
...
int main()
{
  printf("Hallo, ich bin nicht ausführbar ...");
  return 0;
}
```

    --{{4}}--
In Zukunft wird es natürlich auch noch größere Projekte geben, du kannst
ausführbare Dateien auch schileßen oder öffnen indem du auf die Titelleiste
klickst. Mit einem klick auf den Pfeil rechts in der Titelleiste kannst du
zwischen Vollbild (ganze Datei) und minimaler Darstellung (maximal 12 Zeilen)
wechseln.


### Eingaben via `scanf`

    --{{0}}--
Wie man mit `printf` Ausgaben mit C generiert hast du ja bereits in teilen
gesehen. Jetzt geht es darum, das Programm ein wenig zu erweitern.

* Nutze die Funktion `scanf` um Zahlen einzugeben.
* Formatiere in `printf` Ausgabe damit der aktuelle Zähler angezeigt wird.

``` c main.c
#include <stdio.h>

int main()
{
  int i = 0;
  int max = 5;

  printf("Wie oft soll gegrüßt werden: ");

  // TODO: insert scanf here

  for(i; i<max; ++i) {
    // TODO: change printf to print out the value of i
    printf("Hallo # i\n");
  }

  return 0;
}
```
@run_main(nummer_welt)


## Arduino

    --{{0}}--
Wie du im unteren Code-Abschnitt siehst, so unterscheidet sich ein
Arduino-Programm von einem Standard-C Programm einmal durch die Dateiendung
`ino` und einmal durch das Fehlen der `main`-Funktion. Diese ist aufgeteilt in
eine `setup` und eine `loop` -Funktion. Ein Programm für einem Microcontroller
schreibt man für die "Ewigkeit" das nur von einigen "Resets" neu gestartet wird.
Deshalb diese Konvention, in der einmalig `setup` zur Initialisierung aufgerufen
wird und `loop` sonst in einer Endlosschleife ausgeführt wird:

``` c sketch.ino
int counter;

// the setup routine runs once when you press reset:
void setup() {
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
  // initialize the counter variable
  counter = 0;
}

// the loop routine runs over and over again forever:
void loop() {

  Serial.print("Hello World ");
  Serial.println(++counter);

  delay(1000);        // delay in between reads for stability
}
```
@run_main(hallo_welt)

    --{{1}}--
Unter dem Startknopf befinden sich mehrere Roboter die du zur Ausführung deines
Programms auswählen kannst. _Mit großer Macht kommt auch große Verantwortung._
Falls du dein Programm auch tatsächlich ausführen möchtest, dann wähle einen
dieser Roboter aus. Wenn sich der Button grün färbt, dann hast du diesen für
dich  und dein Programm exklusiv reserviert und dein Programm wird automatisch
auf den dazugehörigen Microcontroller übertragen, man spricht in diesem
Zusammenhang auch von "flashen".

    --{{2}}--
Drückst du auf Stop, so wird dein Programm beendet und du wirst erstmal vom
Roboter abgemeldet. Gehe bitte Ressourcensparend vor und logge einen Roboter nur
wenn du auch tatsächlich dein Programm ausführen möchtest, so haben andere
Studenten auch die Möglichkeit ihre Programme zu Testen und wir haben einen
höheren Durchsatz.



### Eingaben via `Serial.read`

    --{{0}}--
Das folgende Programm dient nur der Fingerübung und zeigt dir, wie du über die
Serielle Schnittstelle mit dem System kommunizieren kannst. Versuch doch mal das
Programm zu erweitern und ein Hallo-Welt Programm zu schreiben, das in mehreren
Sprachen grüßt, in Abhänigkeit von deiner Eingabe.

``` c
char receivedChar;
boolean newData = false;

void setup() {
  Serial.begin(9600);
  Serial.println("<Arduino is ready>");
}

void loop() {
  recvOneChar();
  showNewData();
}

void recvOneChar() {
  if (Serial.available() > 0) {
    receivedChar = Serial.read();
    newData = true;
  }
}

void showNewData() {
  if (newData == true) {
    Serial.print("This just in ... ");
    Serial.println(receivedChar);
    newData = false;
  }
}
```

## Arduinoview

    --{{0}}--
Wenn wir schon über eine Weboberfläche programmieren, dann sollte es zumindest
auch die Möglichkeit geben, mit eurem System mithilfe von Webtechnologien zu
interagieren. Mit ArduinoView habt ihr die Möglichkeit HTML- und
JavaScript-Elemente auf eurem Bot abzulegen, die über die Serielle Schnittstelle
an euer Web-Interface übergeben werden.

    --{{1}}--
ArduinoView ermöglicht euch eine bi-direktionale Kommunikation, sodass ihr nicht
nur Messergebnisse in Diagrammen analysieren könnt, sondern auch Buttons und
Slider oder andere Elemente zur Steuerung eures Roboters nutzen könnt. Auf den
folgenden Seiten erhaltet ihr einen Chrash-Kurs in der Nutzung von ArduinoView.

````
  _________________________                        _________________________
 |                         |      {Messages}      |                         |
 |      Application        |< - - - - - - - - - ->|   HTML5 & JavaScript    |
 |_________________________|                      |_________________________|

  _________________________                        _________________________
 |                         | {Arduinoview frames} |                         |
 |     Framer-Unframer     |< - - - - - - - - - ->|     Framer-Unframer     |
 |_________________________|                      |_________________________|

  _________________________                        _________________________
 |                         |                      |                         |
 |     Arduino-Serial      |                      |      OS -> Browser      |
 |_________________________|                      |_________________________|

  __________________________________________________________________________
 |                                                                          |
 |                             Serial over WiFi                             |
 |__________________________________________________________________________|

````

ArduinoView on Github: TODO

### Arduino -> ArduinoView

    --{{0}}--
ArduinoView kommuniziert, wie in der Grafik zuvor skizziert, in abgeschlossenen
Frames. Ein Frame beginnt mit dem ersten `frm.print` und wird mit `frm.end`
abgeschlossen. Ein solcher Frame kann als vollständige Anweisung interpretiert
werden. Die ersten zwei Zeichen werden als "runner" interpretiert, sie stellen
die Funktionalität dar, die auf der Gegenseite aufgerufen wird. ArduinoView
unterstütz insgesamt 7 unterschiedliche "runner", die auch erweitert werden
können.

    {{0}}
``` c
  frm.print("!h");
  frm.print("<h1>ArduinoView</h1>");
  ...
  frm.end();
```

    --{{1}}--
Im obigen Beispiel wird der runner "!h" aufgerufen, er ersetzt per default den
Inhalt von ArduinoView durch den darauf folgenden HTML-Code. Mehrfache Aufrufe
dieser Art ersetzten die vorhergehende Darstellung.

    --{{2}}--
Anders ist dies bei "!H". Dies ergänzt den vorhandenen HTML-Code. Dies kann auch
als "append" interpretiert werden.

    {{2}}
``` c
  frm.print("!H");
  frm.print("<h2>Demo 0 - Hello World </h2>");
  frm.end();
```

    --{{3}}--
Der runner "!j" führt Javascript im Kontext des ArduinoView-Fensters aus. Dieser
kann auch komplexere Befehle wie `document.getElementById`, `console.log` oder
die Definition von Javascript-Funktionen genutzt werden.

    {{3}}
``` c
  frm.print("!j");
  frm.print("alert(\"3+5=\"+(3+5))");
  frm.end();
```

    --{{4}}--
Der runner "!w" ändert das gegenwärtige Workelement, auf welches alle
HTML-Befehle auswirken. Wie unten dargestellt, kann der Inhalt jedes
HTML-Knotens auf diese Weise dynamisch angepasst werden.

    {{4}}
``` c
  // create a state div
  frm.print("!H");
  frm.print("<div id=\"status\">");
  frm.print("noch kein Status ...");
  frm.print("</div>");
  frm.end();

  // set the work element to an existing id
  frm.print("!wstatus");
  frm.end();
  // and change its content
  frm.print("!hsomething has changed ...");
  frm.end();

  // reset work element to default (body)
  frm.print("!w"); frm.end();
```

Der "!!" runner kommt nur in dieser Kurzschreibweise vor. Er führt zu einer
Neuinitilisierung des ArduinoView-Fensters. Nach der Initialisierung antwortet
ArduinoView seinerseits mit einem "!!". An dieses Ereignis sollte auch die
Initialisierung der graphischen Bedienoberfläche gebunden werden.

    {{5}}
``` c
  frm.print("!!");
  frm.end();
```

#### Shorthands

Beispiel Buttons:

``` c
  // !Sb(utton)[id]v(Some Text)
  // always as complete frame
  frm.print("!Sb01vklick Mich");
  frm.end();
```

Arduinoview shorthand provides some graphical "standard" elements through the
runner "!S". It suffers from the problem of Arduviz an Guino in that it provides
only a set of GUI elements. Each element is represented by a character which is
followed by a 2 byte ID that is written to the IDs array and can be accessed by
the workelement object.


```
<Shorthand Frame>   : !S<E><ID><DATA>
<E>                 : <Character>
<ID>                : <Character><Character>
<Data>              : < ! separated Information >
```

interpretation of E

| Shorthand | Description |
|---|-----------------------------------------------------------------------------------------|
| l | adds a line break |
| b | adds a Button <DATA> value will be interpreted as Caption; onclick it will send g  its 2 byte ID |
| s | adds a slider (range); onchange it will send !g + its 2 byte ID + it value (0-255) |
| c | adds a checkbox; onchange it will send !g + its 2 byte ID + its value (t or f) |
| G | adds a graph using the flot.js library (defaults to a moving Graph)|
| t | adds a textinput; onchange it will send !g + its 2 byte ID + its value |
| d | adds a div block that is styled as a inline block |

interpretation of DATA

the Data is partitioned by ! and each part is interpreted by its first character

| character | interpretation |
|---|-------------------------------------|
| s | css style the element |
| w | css width |
| h | css height |
| v | value (interpretation depends on the Element) |


Example: consecutive Frames

```
!Sdlew49%
```

adds a div with a width of 49% with the IDs[] entry "le"

```
!Sdriw49%
```

adds a div with a width of 49% with the IDs[] entry "ri"

The two div will be side by side.

```
!wle
```

switch to the left div

```
!SMgl
```

adds a moving graph to the left div with the IDs[] entry "gl" without further
attributes it defaults to 100% width and 20em height

```
!wri
```

switch to the right div

**Diagrams**

```
!SGgrw80%!h300px
```

adds a not moving graph to the right div with the IDs[] entry "gr" its width
will be 80% of the right div and its height 300px


The graphs may now be filled with Data, this can be done by either accessing the
plot container via JavaScript GUI-data runner of the Graph '!d'.

```
!dgr100,200
```

writes the values 100 and 200 to the GUI Elemet gr, the graph will interprete
them as values to be attached to the graph.



### Arduino <- ArduinoView

    --{{0}}--
Nachrichten von der Weboberfläche (ArduinoView) werden auf dem Arduino mittels
der ArduinoView-Library als Callbacks interpretiert. Hierzu muss in `loop` die
Funktion `frm.run()` aufgerufen werden. Dabei kann zwischen zwei Verfahren
unterschieden werden, ein greedy- und non-greedy-Variante.

``` c
// greedy, use for simple programs
void loop() {
  // process all characters available
  while(frm.run());
  ...
}
// non-greedy, to be used for complex tasks
void loop() {
  // process a single character only,
  // it gives other processes/functions a chance to work
  frm.run();
  ...
}
```

Welcher runner an welche Funktion gebunden ist, wird in der runnerlist
definiert. Der `callrunner` übergibt keine Parameter an die aufgerufene
Funktion. Der `fwdrunner` entfernt die ersten beiden Zeichen (Kopf) aus der
Nachricht und übergibt den Rest der Nachricht an die aufgerufen Funktion.

```c
beginrunnerlist();
callrunner(!!,InitGUI);      // call function(void)
fwdrunner(tx,print2serial);  // call function(char* str, size_t length)
fwdrunner(LD,LEDrunnerlist); // forward to another runnerlist
endrunnerlist();
```

> Beachte, dass bei Runnerlisten unbeding `runnerlist` im aufrufenden `fwdrunner`
> definiert sein muss, dieser Begriff jedoch in der Definition der aufgerufenen
> Runnerlist fehlt.

```c
beginrunnerlist(LED);        // <- See the title (no runnerlist)
fwdrunner(gr,setGreenLed);   // call setGreenLed(char* str, size_t length)
fwdrunner(bl,setBlueLed);    // call setBlueLed(char* str, size_t length)
fwdrunner(rd,setRedLed);     // call setRedLed(char* str, size_t length)
endrunnerlist();
```

### Initialisierung der Kommunikation

    --{{0}}--
Im unteren Snippet ist dargestellt, welche Schritte noch zur Initialisierung von
ArduinoView notwendig sind.

> Bei der Initialisierung für das eLab ist hierbei nur zu beachten, das
> `FrameStream` auf die  serielle Schnittstelle 1 (`Serial1`) gelegt wird.
> `Serial` ohne 1 publiziert auf die Konsole. Mit `Serial1.begin`, welches
> innerhalb der `setup` Funktion aufgerufen wird, wird die Schnittstellt
> initialisiert.

```c
#include <FrameStream.h>
#include <Frameiterator.h>

#define OUTPUT__BAUD_RATE 57600
FrameStream frm(Serial1);

...
// definition of runnerlists
beginrunnerlist();
callrunner(!!,InitGUI);
endrunnerlist();

...
void setup() {
  // init serial communication for ArduinoView
  Serial1.begin(OUTPUT__BAUD_RATE1);

  // request reset of gui
  frm.print("!!");
  frm.end();

  // give it some time to initialize
  delay(500);
  ...
```

### Hallo

    --{{0}}--
Die Folgenden Seiten enthalten Kurze ausführbare Beispiele, mit denen du
Experimentieren kannst um später komplexere Darstellungen und Interaktionen mit
deinem Roboter zu implementieren

1. Yet another HalloWOrld-Program
2. Eye-Candy-Diagrams
3. Wahoo-Super-Buttons

Weitere Beispiele findest du unter: TODO

#### ArduinoView

Arduino goes HTML:

``` c sketch.ino
// -----------------------------------------------------------------
// Examples of the ArduinoView Library
// 0. Hello World
// -----------------------------------------------------------------
// This example demonstates the integration of html content within
// the arduino code

#include <FrameStream.h>
#include <Frameiterator.h>

#define OUTPUT__BAUD_RATE 57600
FrameStream frm(Serial1);

// We do not have any interaction in this example, but a default
// callback definition is need for frm.run().
// GUI initialisation request

beginrunnerlist();
callrunner(!!,InitGUI);
endrunnerlist();

void InitGUI(){
  frm.print("!h<h1>ArduinoView</h1>");
  frm.print("<h2>Demo 0 - Hello World </h2>");
  frm.print("<p>Congratulation you transmitted the first HTML Code from your Arduino!!!</p>");
  frm.print("<img src=\"https://upload.wikimedia.org/wikipedia/commons/8/87/Arduino_Logo.svg\" height=\"200\" width=\"200\" >");
  frm.end();
}

void setup() {
  Serial.begin(OUTPUT__BAUD_RATE1);

  //request reset of gui
  frm.print("!!");
  frm.end();

  delay(500);
}

void loop() {
  frm.run();
}
```
<script>@input</script>

#### Diagramm

Extended Shorthands:

``` c
#include <FrameStream.h>
#include <Frameiterator.h>

#define OUTPUT__BAUD_RATE 57600
FrameStream frm(Serial1);

beginrunnerlist();
callrunner(!!,InitGUI);
endrunnerlist();

void setup() {
  //prepare Serial interfaces
  Serial1.begin(OUTPUT__BAUD_RATE);
  frm.print("!!");
  frm.end();

  delay(500);
}

void InitGUI()
{
    // Generating the diagram
    frm.print("!SGgrv50");
    frm.end();
}

void loop() {
    while(frm.run());

    frm.print("!dgr");
    frm.print(random(300));
    frm.end();

    delay(500);
}
```

#### Button

Comunicating from Arduino -> Web -> Arduino

``` c
#include <FrameStream.h>
#include <Frameiterator.h>

#define OUTPUT__BAUD_RATE 57600
FrameStream frm(Serial1);

// hierarchical runnerlist, that connects the gui elements with
// callback methods
declarerunnerlist(GUI);

beginrunnerlist();
callrunner(!!,InitGUI);
fwdrunner(!g,GUIrunnerlist);
endrunnerlist();

beginrunnerlist(GUI);
callrunner(GO,callback_GO);
endrunnerlist();


void callback_GO(){
  static int i = 0;

  // change workelement to st
  frm.print("!wst");
  frm.end();

  // change content
  frm.print("!h");
  frm.print(i);
  frm.end();

  // reset we
  frm.print("!w");
  frm.end();

  Serial.print("klick ");
  Serial.println(i);

  i++;
}

void setup() {
  //prepare Serial interfaces
  Serial1.begin(OUTPUT__BAUD_RATE);
  Serial.begin(9600);
  frm.print("!!");
  frm.end();

  delay(500);
}

void InitGUI()
{
    frm.print("!h<h1>Status-Counter</h1>");
    frm.end();

    // generate (S)horthand (d)iv with id st
    frm.print("!Sdst");
    frm.end();

    // generate (S)horthand (b)utton with id GO and (v)alue Klick
    frm.print("!SbGOvKlick");
    frm.end();
}

void loop() {
    while(frm.run());
}
```

## Aufgabe 0

Klick to switch on LED?

```

```

## Quizze

### Macros 1

Welche Aussagen gelten für C-Macros?

    [[X]] Beginnt immer mit einem `#`.
    [[ ]] Wird vom Compiler aufgerufen.
    [[X]] Ist nur eine Textersetzung.
    [[ ]] Macros können genutzt werden um neue Macros zu erzeugen.
    [[ ]] `#include` ist kein Makro.
********************************************************************************

Ja, neben `#define` oder `#include` gibt es noch weitere Macrodirektiven.

Nur der Präprozessor ersetzt Macros vor dem eigentlichen Kompilieren, dabei
handelt es sich um eine reine Textersetzung. Diese wird nur einmalig
durchgeführt, Rekursion oder Schleifen oder komplexere Programmersetzungen (wie
in Lisp, Elixir, etc.) sind nicht möglich.

Beim `#include` wird der Inhalt einer gesamten Datei eingesetzt. Der Unterschied
zwischen den Angaben `"file1.h"` und `<file2.h>` liegt am Speicherort der Datei.
Erstere ist lokal im gleichen Verzeichnis und die zweite in einem
Systemverzeichnis.

https://de.wikipedia.org/wiki/C-Pr%C3%A4prozessor

********************************************************************************

### Macros 2


``` c
#define square(X) X*X

square(3+2); // wie lautet das Ergebnis?
```

Wie sieht das Resultat der folgenden Quadrierung aus, bitte gib dein Ergebnis
als Zahl in das folgende Textfeld ein:

    [[11]]
********************************************************************************


Das Ergebnis der Ersetzung ist `3+2*3+2` also ist hier die richtige Antwort 11
und nicht 25. Probiert es einfach aus, wenn ihr es nicht glaubt. Ihr könnt ja
noch für euch selber testen wie man das Macro anpassen muss, damit es das
richtige Ergebnis liefert.

``` c
#include <iostream>
using namespace std;

#define square(X) X*X

int main() {
    cout << "square 3+2 = " << square(3+2) << endl;
    return 0;
}
```
@run_main(square)

********************************************************************************

### Serielle Schnittstelle

Ausgaben über die serielle Schnittstelle werden bei eingebetteten Systemen
häufig für das Debugging genutzt. Was sind die Konsequenzen, wenn das Schreiben
dieser Ausgaben für die finale Version abgeschaltet wird?

    [[ ]] Speicherüberlauf
    [[X]] Verringert Stromaufnahme des Controllers
    [[ ]] Reduzierung der Programmgröße
    [[X]] Änderung des Zeitverhaltens des Programms
*******************************************************************************

Ein zu erwartendes Resultat, wenn die Serielle Schnittstelle vollständig
abgeschaltet wird, ist die Verringerung der Stromaufnahme des Prozessor. Dazu
genügt es aber nicht nur auf die Schreib-/Lese-Operationen zu verzichten,
vielmehr muss die Schnittstelle deaktiviert werden (Standardzustand beim
Booten).

Die Schreib-/Lese-Operationen verlangen eine nicht unerhebliche
Prozessorleistung. Entsprechend ändert sich die Laufzeit des Programms, was in
zeitkritischen Anwendungen bei "fragwürdiger" Programmierung zu einem gänzlich
veränderten Verhalten führen kann.

*******************************************************************************


## Umfrage ...

Kommt nocht


## Quellen

__C und C++:__

Im Kurssystem haben wir das Wikipedia Buch C-Programmierung für euch in ein
interaktives LiaScript übersetzt, das könnt ihr als Referenzhandbuch nehmen und
mit den aufgezeigten Beispielen experimentieren, das Buch durchsuchen oder
einfach nur schmökern ;-)

* Tutorials: http://www.learncpp.com
* Bücher: https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list
* Videos: https://www.youtube.com/watch?v=Rub-JsjMhWY
* Bitoperationen: https://de.wikipedia.org/wiki/Bitweiser_Operator

__Eingebettete Programmierung:__

    --{{1}}--
Für Interessierte gibt es darüber hinaus auch Tutorials, die direkt auf die
Programmierung eingebetteter Systeme eingehen. Für die Bearbeitung der Aufgaben
solltet ihr sowohl das Datenblatt des Mikrocontrollers, als auch den
Schaltbelegungsplan studieren.

* Tutorials für eingebettet Systeme: https://www.mikrocontroller.net/articles/AVR-Tutorial
* Arduino Serielle I/O Funktionen: https://www.arduino.cc/en/reference/Serial
* Arduino Blink Beispiel: https://www.arduino.cc/en/Tutorial/Blink
* circuits.io - Autodesk Circuits: https://circuits.io

__PKeS:__

* Datenblatt des AVR ATmega32U4: http://www.atmel.com/Images/Atmel-7766-8-bit-AVR-ATmega16U4-32U4_Datasheet.pdf
* Schaltbelegungsplan: https://github.com/liaScript/PKeS0/blob/master/materials/robubot_stud.pdf?raw=true
* Arduinoview: https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md
* ArduinoviewLib: https://github.com/fesselk/ArduinoviewLib
