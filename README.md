<!--

author:   Georg Jäger

email:    gjaeger@ovgu.de

version:  1.0.0

language: de_DE

narrator:  Deutsch Female

-->

# Einführung

--{{1}}--
Willkommen bei dem eLearning-System *eLab*! Es wird euch bei der Bearbeitung der praktischen Aufgaben zur Vorlesung *Prinzipien und Komponenten eingebetteter Systeme* unterstützen. 

--{{2}}--
Um zunächst einen Eindruck von dem System, sowie dem damit verbundenen Arbeitsablauf, zu bekommen, sollt ihr in dieser *nullten* Aufgabe das *Hello World*-Programm der eingebetteten Programmierung implementieren; das An- und Ausschalten einer LED.

## Themen und Ziele

--{{1}}--
Während der Bearbeitung der Aufgabe sollen verschiedene Themen zur Programmierung eingebetteter Systeme angesprochen werden. 

--{{2}}--
Wesentlich für den weiteren Verlauf der Vorlesung ist, dass ihr den Mikrocontroller, AVR ATmega32U4, kennenlernt. Dieser wird während der Aufgaben zu programmieren sein. 

--{{3}}-- 
Zur Programmierung selbst steht in dem eLearning-System eine einfache IDE bereit. Schon zur Bearbeitung dieser Aufgabe werdet ihr diese Nutzen.

--{{4}}--
Eines der Ziele dieser Aufgabe ist es, eine LED an dem Roboter zum Blinken zu bringen. Neben dem Wissen über den Mikrocontroller selbst, sollt ihr dazu den Schaltbelegungsplan studieren. So könnt ihr herausfinden, wie periphäre Komponenten, also Sensorik und Aktorik, an den Mikrocontroller angeschlossen ist.

--{{5}}--
Da die Programmierung eingebetteter Systeme, wie auch bei der Anwendungsprogrammierung, zuweilen das Aufspüren und Beseitigen von Fehlern in der Implementierung beinhaltet, werdet ihr das Framework *Arduinoview* benutzen um Daten/Zustände des Mikrocontrollers zu visualisieren und Funktionalitäten ein- und auszuschalten.

**Themen:**

* Der Mikrocontroller [AVR ATmega32U4](http://www.microchip.com/wwwproducts/en/ATmega32u4).
* Programmierung des Mikrocontrollers über das eLearning-System.
* Der Anschluss der Peripherie, d.h Sensorik und Aktorik, an den Mikrocontroller.
* Das Framework [Arduinoview](https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md)

**Ziel(e):**
* Kennenlernen des Arbeitsablaufs: 
  * Recherchieren der nötigen Informationen zur Bearbeitung einer Aufgabe. Welche Dokumente sind relevant? 
  * Einarbeiten in die Programmierung des Systems. Wo finde ich Hilfe und Erklärungen zu Bibliotheken und Funktionen?
  * Implementieren der Lösung entsprechend der Recherchierten Informationen. Wie funktioniert der Kompilierungs-, Assemblierungs- und Linkprozess für eingebettete Systeme?
  
## Weitere Informationen

--{{1}}--
Da im Bereich der Programmierung eingebetteter Systeme die Programmiersprache C/C++ vorherrscht, solltet ihr euch durch Tutorials, Bücher oder Videos entsprechend einarbeiten.


--{{2}}--
Im speziellen sind Bitoperationen zur Bearbeitung der *nullten* Aufgabe, aber auch zur Programmierung von Mikrocontrollern im allgemeinen, hilfreich.

--{{3}}--
Für Interessierte gibt es darüber hinaus auch Tutorials, die direkt auf die Programmierung eingebetteter Systeme eingehen.


--{{4}}--
Für die Bearbeitung der Aufgaben solltet ihr sowohl das Datenblatt des Mikrocontrollers, als auch den Schaltbelegungsplan studieren.

**C/C++:**

* [Tutorials](http://www.learncpp.com/), [Bücher](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list) oder [Videos](https://www.youtube.com/watch?v=Rub-JsjMhWY) zu [C](https://en.wikipedia.org/wiki/C_%28programming_language%29)/[C++](https://en.wikipedia.org/wiki/C%2B%2B)
* [Bitoperationen](https://de.wikipedia.org/wiki/Bitweiser_Operator)

**Eingebettete Programmierung:**
* [Tutorials für eingebettet Systeme](https://www.mikrocontroller.net/articles/AVR-Tutorial)
* [Arduino Serielle I/O Funktionen](https://www.arduino.cc/en/reference/Serial)
* [Arduino Blink Beispiel](https://www.arduino.cc/en/Tutorial/Blink)
* [circuits.io - Autodesk Circuits](https://circuits.io/)

**PKeS:**
* [Datenblatt](http://www.atmel.com/Images/Atmel-7766-8-bit-AVR-ATmega16U4-32U4_Datasheet.pdf).
* [Schaltbelegungsplan](https://github.com/liaScript/PKeS0/blob/master/materials/robubot_stud.pdf?raw=true) 

# Aufgabe 0

--{{1}}--
In der *nullten* praktischen Aufgabe sollt ihr zunächst eine LED zum Blinken bringen, bevor ihr in der zweiten Teilaufgabe das Framework *Arduinoview* nutzt um Daten und Zustände des Mikrocontrollers, bzw. des eingebetteten Systems, zu visualisieren.


## Aufgabe 0.1

**Ziel:** Lasst die LED an PIN 31 in einem Interval von 0.5 Sekunden aufleuchten und erlischen. 

Begin und Ende des Blinkens soll durch den Button 'Start/Ende', welcher durch das Framework *Arduinoview* visualisiert wird, steuerbar sein.

**Teilschritte:**

1. Konfiguriert den PIN 31 als Ausgang. Dies soll in der Funktion `configurePin()` geschehen.
2. Implementiert zwei Funktion: `ledOn()` zum einschalten der LED, `ledOff()` zum ausschalten der LED.
3. ...


## Aufgabe 0.2

Definition der GUI

2 Frames:
  1. Zurücksetzen der GUI
  2. Anlegen des Button: -> Github Documentation Shorthand Arduinoview
    -> !Sbb1v<Caption>
    
## Aufgabe 0.3

Verbindung von Button und LED/Funktionalität

--> Runner-Konzept
--> Beispiel aus ArduinoviewLib: https://github.com/fesselk/ArduinoviewLib/blob/master/examples/E01_button/E01_button.ino

Programmierung der Oberfläche mittels Arduinoview

https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md
