!> Die Hostsoftware ist auf nicht absehbarer Zeit closed source!

Bitte beachte, dass Java nicht sehr ressourcenschonend ist.
Wenn Du einen Raspberry verwenden möchtes, empfehlen wir mindestens einen Raspberry 3+ oder vergleichbar. Einige Benutzer habe AWTRIX auch auf einemRaspberry Zero W laufen, dies ist jedoch nicht zu empfehlen, da die Ressourcen eigentlich nicht ausreichend für den Betrieb des Hosts sind. Also nicht meckern, wenn's nicht klappt.


AWTRIX 2.0 kann auf jeder Plattform (Windows, MacOS, Linux) laufen, die einzige Voraussetzung ist die Unterstützung von Java 8 (1.8_232). Es handelt sich um eine Nicht-GUI-Anwendung, sodass keine Desktop-Umgebung benötigt wird.   
Dieses Tutorial beschreibt die Installation auf einem Linux-Rechner.  


## Schnellstart
Dieses kurze Beispiel zeigt, wie man die Java-Anwendung startet.
Gehe zum nächsten Punkt für die Installation auf einer Linux-Maschine.

Die aktuelle [AWTRIX Java-Anwendung](https://blueforcer.de/awtrix/beta/awtrix.jar)
 herunterladen

 und starten über die Kommandozeile oder das Terminal. 

**Linux & MacOS:**    
 ``` sudo java -jar awtrix.jar ```      
 **Windows:**    
 ``` java -jar awtrix.jar ```

   
!> **sudo** wird nicht immer benötigt. Es hängt davon ab, in welchem Ordner Du die Anwendung starten möchten. AWTRIX muss neue Ordner und Dateien erstellen, so dass AWTRIX in wenigen Fällen keine Schreibrechte hat.

Kurz nach dem Start kann das Webinterface über http://awtrix_ip:7000 aufgerufen werden.

## Raspberry Installer
Für die automatische Installation aller benötigter Komponenten den folgenden Befehl im Terminal eingeben.
 ```wget -N https://blueforcer.de/awtrix/AWTRIX.sh ; sudo sh AWTRIX.sh```

?> Kurz nach dem Start kann das Webinterface über http://awtrix_ip:7000 aufgerufen werden.  
Der Befehl kann auch für Updates deiner aktuellen Installation genutzt werden.

## Beta
Wir empfehlen die aktuelle Beta des Hosts zu benutzen!  
[Infos zum Beta Host](https://forum.blueforcer.de/d/295)  

Der Installer kann auch hier genutzt werden. Es muss nur der Parameter "beta" hinzugefügt werden:
 ```wget -N https://blueforcer.de/awtrix/AWTRIX.sh ; sudo sh AWTRIX.sh beta```  
Manueller Download: [AWTRIX BETA Host](https://blueforcer.de/beta/awtrix.jar)  


## Installation auf einem Linux-Rechner mit Autostart


Überprüfe zunächst, ob Java installiert ist.  
```Java -Version```
  
Andernfalls installiere die neueste Java8:  
```sudo apt-get install oracle-java8-jdk```
installieren  

Stelle die Zeitzone ein: z.B.  
``` sudo timedatectl set timezone Europe/Berlin``` 


### AWTRIX Server herunterladen

```sudo mkdir /usr/local/awtrix```  
```cd /usr/local/awtrix```    
```sudo wget https://blueforcer.de/downloads/awtrix.jar```  


### Autostart

Erzeuge eine neue Datei unter **/etc/systemd/system/** mit nano oder vi.  
```sudo nano /etc/systemd/system/awtrix.service```  
  
Füge den untenstehenden Code in diese neue Datei ein:

```
[Unit]
Description = AWTRIX Service
After network.target = awtrix.service

[Service]
Type = forking
WorkingDirectory =/usr/local/awtrix
ExecStart = /usr/local/bin/awtrix.sh start
ExecStop = /usr/local/bin/awtrix.sh stop
ExecReload = /usr/local/bin/awtrix.sh reload

[Install]
WantedBy=multi-user.target
```



Erstelle eine neue Datei unter ***/usr/local/bin/***.   
```sudo nano /usr/local/bin/awtrix.sh```  
und füge diesen Code ein

```
#!/bin/sh
SERVICE_NAME=awtrix
PATH_TO_JAR=/usr/local/awtrix/awtrix.jar
PID_PATH_NAME=/tmp/awtrix-pid
case $1 in
    start)
        echo "Starting $SERVICE_NAME ..."
        if [ ! -f $PID_PATH_NAME ]; then
            sudo nohup java -jar $PATH_TO_JAR /tmp 2>> /dev/null >> /dev/null &
                        echo $! > $PID_PATH_NAME
            echo "$SERVICE_NAME started ..."
        else
            echo "$SERVICE_NAME is already running ..."
        fi
    ;;
    stop)
        if [ -f $PID_PATH_NAME ]; then
            PID=$(cat $PID_PATH_NAME);
            echo "$SERVICE_NAME stoping ..."
            kill $PID;
            echo "$SERVICE_NAME stopped ..."
            rm $PID_PATH_NAME
        else
            echo "$SERVICE_NAME is not running ..."
        fi
    ;;
    restart)
        if [ -f $PID_PATH_NAME ]; then
            PID=$(cat $PID_PATH_NAME);
            echo "$SERVICE_NAME stopping ...";
            kill $PID;
            echo "$SERVICE_NAME stopped ...";
            rm $PID_PATH_NAME
            echo "$SERVICE_NAME starting ..."
            sudo nohup java -jar $PATH_TO_JAR /tmp 2>> /dev/null >> /dev/null &
                        echo $! > $PID_PATH_NAME
            echo "$SERVICE_NAME started ..."
        else
            echo "$SERVICE_NAME is not running ..."
        fi
    ;;
esac
```

Speichere die Datei und erteile Ausführungsrechte

``` sudo chmod +x /usr/local/bin/awtrix.sh``` 

Teste, ob es damit läuft:  
```sudo /usr/local/bin/./awtrix.sh start```     

Wenn das geklappt hat, teste, ob es mit:   
```sudo /usr/local/bin/./awtrix.sh stop```
stoppt.     

Der Neustart testet man mit:  
```sudo /usr/local/bin/./awtrix.sh restart```     

Wenn alles funktioniert, aktiviere den Dienst mit 

```sudo systemctl enable awtrix``` 

Ab nun kannst du

AWTRIX starten mit 
```sudo systemctl start awtrix.service ```  
AWTRIX stoppen mit
```sudo systemctl stop awtrix.service```
und   
AWTRIX neu starten mit
```sudo systemctl restart awtrix.service``` 