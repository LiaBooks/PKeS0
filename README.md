<!--

author:   Georg Jäger

email:    gjaeger@ovgu.de

version:  1.0.0

language: de_DE

narrator:  Deutsch Female

-->

# Einführung eLab

--{{1}}--
In diesem Kurs soll das eLearning-System *eLab* vorgestellt werden. Studenten, die die Vorlesung *Prinzipien und Komponenten eingebetteter Systeme* hören, werden es zur Bearbeitung der praktischen Aufgaben benutzen. 


--{{2}}--
Zunächst sollen anhand einer einfachen Aufgabe (An-/Ausschalten einer LED) verschiedene Komponenten der Vorlesung eingeführt werden.

**Themen:**

1. Der Mikrocontroller [AVR ATmega32U4](http://www.microchip.com/wwwproducts/en/ATmega32u4), der während der Vorlesung programmiert wird.
2. Der Anschluss der Peripherie, d.h Sensorik und Aktorik, an den Mikrocontroller.
3. Das eLearning System über das, u.a., der Roboter/Mikrocontroller programmiert und angesteuert wird.


## Weitere Informationen

--{{1}}--
Da im Bereich der Programmierung eingebetteter Systeme die Programmiersprache C/C++ vorherrscht, solltet ihr euch durch Tutorials, Bücher oder Videos entsprechend einarbeiten.


--{{2}}--
Im speziellen sind Bitoperationen zur Bearbeitung der *nullten* Aufgabe, aber auch zur Programmierung von Mikrocontrollern im allgemeinen, hilfreich.

**Zusätzliche Hilfsmittel:**

* [Tutorials](http://www.learncpp.com/), [Bücher](https://stackoverflow.com/questions/388242/the-definitive-c-book-guide-and-list) oder [Videos](https://www.youtube.com/watch?v=Rub-JsjMhWY) zu [C](https://en.wikipedia.org/wiki/C_%28programming_language%29)/[C++](https://en.wikipedia.org/wiki/C%2B%2B)
* [Bitoperationen](https://de.wikipedia.org/wiki/Bitweiser_Operator)

# Aufgabe 0

--{{1}}--
In der ersten praktischen Aufgabe sollen zwei verschiedene Aspekte fokusiert werden. Zum einen soll die hardwarenahe Programmierung des Mikrocontrollers AVR ATmega32U4 eingeführt werden. Zum anderen soll Arduinoview als Framework zur Visualisierung von Daten und Zuständen des eingebetteten Systems vorgestellt werden.

--{{2}}--
Diese Aspekte sollen durch das *Hello World* Programm der Mikrocontroller - blinken lassen einer LED - verdeutlicht werden.

--{{3}}-- 
Da darüber hinaus der Datenaustausch sowie die Kommunikation mit dem eingebetteten System wesentlich für die erfolgreiche Programmierung ist, soll im zweiten Teil das Framework *Arduinoview* eingeführt werden. 

**Fokus:**

1. Hardwarenahe Programmierung des [AVR ATmega32U4](http://www.microchip.com/wwwproducts/en/ATmega32u4) durch das An-/Ausschalten einer LED
2. Visualisierung von Daten/Zuständen des Mikrocontrollers durch [Arduinoview](https://github.com/fesselk/Arduinoview/blob/master/doc/Documetation.md)

## AVR ATmega32U4

--{{1}}--
Hier könnt ihr das Datenblatt, sowie den Schaltbelegungsplan des Mikroncontrollers finden.


* [Datenblatt](http://www.atmel.com/Images/Atmel-7766-8-bit-AVR-ATmega16U4-32U4_Datasheet.pdf).
* [Schaltbelegungsplan](./robubot_stud.pdf) 

## Zusätzliches Material

--{{1}}--
Neben dem Datenblatt und dem Schaltbelegungsplan, können euch diese Hilfsmittel eventuell auch weiter helfen.

* [Arduino Serielle I/O Funktionen](https://www.arduino.cc/en/reference/Serial)
* [Arduino Blink Beispiel](https://www.arduino.cc/en/Tutorial/Blink)
* [circuits.io - Autodesk Circuits](https://circuits.io/)


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



#### Anwendung/Beispiel



Setzen eines einzelnen Bits/Pins auf 1:
  PORTC |= 1 << 2; --> "Bit 2"/ 3. Stelle
  
  + alternative schreibweise für 
  
Setzen eines einzelnen Bits/Pins auf 0:
  PORTC &= ~(1 << 2); --> "Bit 2"/ 3. Stelle# IDE

test
