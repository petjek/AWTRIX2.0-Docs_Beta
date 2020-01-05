![AWTRIX Pro](\assets\awtrix_pro.jpg)

AWTRIX (**AW**some ma**TRIX**) ist eine Vollfarb-Dot-Matrix, die Anwendungen von der simplen Darstellung der Uhrzeit bis zu Statistiken des Fortnite-Accounts anzeigt.

Die Technik dahinter basiert auf wenigen Komponenten, sodass sie auch von Anwendern mit weniger technischem Geschick leicht nachgebaut werden kann. Das Projekt. Angetrieben wird die Matrix (32 × 8 WS2812B-LEDs) von dem WLAN-Mikrocontroller ESP8266, der mit einen Java-basiertem Host kommuniziert. Als Server kann nahezu jedes bestehendes System auf Windows-, MacOS- oder Linux-Basis dienen.

Natürlich schreit so ein Projekt danach, mit dem Einplatinenrechner Raspberry Pi zu laufen. Der Vorteil: der Server kann direkt mit in das Gehäuse eingebaut werden und es ergibt sich ein kleines aber nicht minder feines, autark funktionierendes System. Ein druckbares Gehäuse habe ich auf der 3D-Druckplattform Thingiverse bereitgestellt und viele kreative User haben eigene Entwürfe beigesteuert. Die Projekte der äußerst aktiven Community gibt es [in meinem Forum zu sehen](https://forum.blueforcer.de/d/22-show-your-awtrix/), darunter Installationen in Holzgehäusen, unter Glastischen und vieles mehr. Awtrix 2.0 ist der Nachfolger der Version 1.0 und mit viel Input aus der Community entstanden. Die kostenlose Anleitung zum Nachbau mit Bauteilliste und Software gibt es online.

Die Hardware lässt sich auch erweitern und um zusätzliche Funktionen ergänzen. Helligkeitssensoren zur automatischen Anpassung der Leuchtkraft, ein Modul zur Tonausgabe, sowie eine Steuerung über kapazitive Taster sein hier genannt. Nach Zusammenbau der Komponenten und Einrichtung der Software erfolgt die weitere Steuerung über den integrierten Webserver. Dieser kommuniziert entweder über WLAN oder über die serielle Schnittstelle (USB oder TX/RX) mit dem ESP8266. Eine eigene Platine ist ebenfalls in meinem Shop zu erwerben.

Neben einfachen Funktionen wie Stoppuhr und Timer baut das Projekt hauptsächlich auf Apps auf, die im integrierten App Store kostenlos heruntergeladen werden können. Neben Apps zu Wetterdaten, Facebook- oder Instagram-Likes sind auch PC-Spiele-Klassiker wie Snake oder Pong vertreten. Letztere werden über ein Smartphone oder am Browser (optional mit angeschlossenem Gamepad) gesteuert. Auch die Einbindung in eine Heimautomatisierung wie FHEM, ioBroker, Home Assistant oder mehr ist möglich. Dir fehlt die eine App, die das Ganze erst so richtig rund machen würde? Kein Problem, denn mit ein wenig Programmierkenntnissen kann man sie einfach selbst schreiben und zur Veröffentlichung einreichen.
Dank der sehr gut dokumentierten API und Schnittstellen für die IoT-Protokolle REST und MQTT lassen sich beliebige Informationen an die Matrix senden. Ob Temperatur, Luftfeuchtigkeit, Stromverbrauch oder einfach nur der Song, der gerade auf Spotify läuft – alles kein Problem. Und wem die lokale Ansteuerung aus dem Netzwerk noch nicht reicht, dem sei die Verbindung zur Awtrix-Cloud empfohlen, mit der unter anderem eine komplett anonyme Anbindung an den Verknüpfungsdienst IFTTT und seine unzähligen Receipts möglich ist.

Bei der Erstellung eigener Notifications hilft ein weiteres Feature: der Awtrixer. Mit diesem mächtigen integrierten Tool lassen sich Icons für die Awtrix herstellen und es können alternativ bereits vorhandene Bilder von 8×8 Pixeln automatisch umgewandelt werden. Auch animierte Icons sind kein Problem. Selbsterstellte Icons werden mit der Community geteilt. Awtrixer gibt es im integrierten Webinterface oder als abgespeckte Version auf Android- und iOS aus dem Store. 

Zum Abschluss hier nochmal eine kurze Auflistung aller Funktionen von AWTRIX:

- Platformunabhängig
- API Schnittstellen für MQTT und REST
- Anzeige von Benachrichtigungen aus deinem Smarthome
- Zugriff auf die Icon Datenbank
- Integrierter Appstore
- Anpassung der Appschleife
- Anpassung der Farbkorrektur für die Matrix
- AWTRIX Arcade für kleinere Spiele auf der Matrix
- Update des Controllers und Hosts über das Webinterface
- Stoppuhr
- Timer

Premium Funktionen:
- Wecker
- Fritz!Box CallMonitor
- Zugriff auf die AWTRIX Cloud
- Pushover Client
- Wecker
- Schlafmodus