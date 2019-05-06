M300 - LB2 Dokumentation Stefan Seslak
===
Die Dokumentation zeigt alle Schritte auf, die ich während der LB2 gemacht und was ich dazu gelernt habehabe.

## Inhaltsverzeichnis
- [M300 - LB2 Dokumentation Stefan Seslak](#m300---lb2-dokumentation-stefan-seslak)
  - [Inhaltsverzeichnis](#inhaltsverzeichnis)
  - [Vagrant](#vagrant)
  - [Visual Studio Code](#visual-studio-code)
  - [Git-Client](#git-client)
  - [SSH-Key](#ssh-key)
  - [GitHub Account](#github-account)
  - [Docker](#docker)
  - [Sicherheit](#sicherheit)
  - [Testen](#testen)
    - [Webserver](#webserver)
    - [Phpmyadmin](#phpmyadmin)
  - [Webserver](#webserver-1)
  - [MYSQL](#mysql)
  - [Phpmyadmin](#phpmyadmin-1)
  - [Vergleich Vorwissen - Wissenszuwachs](#vergleich-vorwissen---wissenszuwachs)
  - [Reflexion](#reflexion)
_



> [⇧ *Nach oben*](#inhaltsverzeichnis)
 
  ## VirtualBox

1. Als erstes habe ich  [VirtualBox](https://www.virtualbox.org) und [Ubuntu Desktop 16.04.05](https://www.ubuntu.com/#download)heruntergeladen.
2. Danach habe ich Virtualbox auf meinem PC installiert.

*Nachdem ich das gemacht habe, habe ich die VM erstellt, mit der ISO Datei die ich vorhin heruntergeladen habe und mit Hilfe dieser Anleitung:*
1. VirtualBox starten
2. Mit einem klick auf `Neu` eine neue VM erstellen.
3. Als nächstes muss man folgende Attribute angeben:
   *  Name:           `M300_Ubuntu_XX.04_Desktop`
   *  Typ:            `Linux`
   *  Version:        `Ubuntu (64-bit)`
   *  Speichergrösse: `2048 MB`
   *  Platte:         `[X] Festplatte erzeugen`
4. Nun auf `Erzeugen` klicken
5. Im nächsten Fenster, folgende Informationen eintragen:
   *  Dateipfad:                       standard
   *  Dateigrösse:                     `10.00 GB`
   *  Dateityp der Festplatte:         `VMDK (Virtual Maschine Disk)`
   *  Storage on physical hard disk:   `dynamisch alloziert`
6. Nun erneut auf `Erzeugen` klicken, dann im Hauptmenü die VM anwählen (blau markiert) und den Punkt `Ändern` aufrufen
7. Im Abschnitt `Massenspeicher` den SATA-Controller anwählen und auf das CD+Symbol klicken
8. Unter `Medium auswählen` das zuvor heruntergeladene Systemabbild (ISO-Datei) anwählen
9. Alle Änderungen speichern und die VM starten
10. Nun den Installationsanweisungen der OS-Installation folgen. 

Nun ist die VM mit all diesen Vorgaben erstellt.

*Danach habe ich in der Bash von Ubuntu folgende Befehle ausgeführt um das System auf den neusten Stand zu bringen.*

1. Paketliste neu einlesen und Pakete aktualisieren:
   
   
	 $  sudo apt-get update   #Paketlisten des Paketmanagement-Systems "APT" neu einlesen
   
   $  sudo apt-get update   #Installierte Pakete wenn möglich auf verbesserte Versionen aktualisieren

   $  sudo reboot           #System-Neustart durchführen
   
2. Software Controlcenter "Synaptic" installieren:
   $  sudo apt-get install synaptic
   
3. Nach erfolgreicher Installation in der Suche nach "Synaptic Package Manager" suchen und diesen starten
4. Innerhalb des Managers nach "apache" (Webserver-Programm) suchen und dieses (inkl. aller Abhängigkeiten) installieren
5. System-Neustart durchführen:
   $  sudo reboot
   
6. Danach habe ich geprüft, ob der Standart-Content des Webservers unter "http://127.0.0.01:80"(Localhost) erreichbar ist



## Vagrant
> [⇧ *Nach oben*](#inhaltsverzeichnis)

Zuerst habe ich [Vagrant](https://www.vagrantup.com/ "vagrantup.com")    heruntergeladen und installiert.

*Danach habe ich mit Vagrant eine VM erstellt.*
1. Terminal öffnen
2. Einen neuen Ordner für die VM anlegen:
    Shell
      $ cd C:\Users\stefan.seslak\Desktop\Meinrepository
      $ mkdir MeineVagrantVM
      $ cd MeineVagrantVM
     
3. Vagrantfile erzeugen, VM erstellen und entsprechend starten:
    Shell
      $ vagrant box add http://10.1.66.11/vagrant/ubuntu/xenial64.box --name ubuntu/xenial64  #Vagrant-Box vom Netzwerkshare hinzufügen
      $ vagrant init ubuntu/xenial64        #Vagrantfile erzeugen
      $ vagrant up --provider virtualbox    #Virtuelle Maschine erstellen & starten
     
4. Die VM ist nun bereit und kann mit SSH-Zugriff bedient werden:
    Shell
      $ cd C:\Users\stefan.seslak\Desktop\Meinrepository\MeineVagrantVM      #Zum Verzeichnis der VM wechseln
      $ vagrant ssh                       																	 #SSH-Verbindung zur VM aufbauen
     
Ich habe geshen, dass es viel einfacher und schneller ist mit Vagrant eine VM zu erstellen.

*Daraufhin habe ich eine VM mit Apache Webserver von einem bereits abgeänderten File erstellt aus dem M300-Repository:*

1. Terminal öffnen
2. In das M300-Verzeichnis wechseln:
      $ cd C:\Users\stefan.seslak\Desktop\Meinrepository\M300\vagrant\web
     
3. VM erstellen und starten:
      $ vagrant up
     
4. Danach habe ich im Webbrowser geprüft, ob der Standard-Content des Webservers unter "http://127.0.0.01:8080" (localhost) erreichbar ist
5. Danach habe ich im Ordner `\web` die Hauptseite `index.html` editiert und das Resultat überprüft.
6. Abschliessend habe ich die VM wieder gelöscht:
      $ vagrant destroy -f
    

## Visual Studio Code
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*In diesem Abschnit habe ich Visual Studio Code heruntergeladen, installiert und kleine Einstellungen vorgenommen.*

1. Ich habe [Visual Studio Code](https://code.visualstudio.com/"visualstudio.com") heruntergelden installiert.
2. Daraufhin habe ich dem Editor drei wichtige Extensions hinzugefügt:

* Markdown All in One (von Yu Zhang)
* Vagrant Extension (von Marco Stanzi)
* vscode-pdf Extension (von tomiko1207)

Dazu habe ich folgende Anweisungen befolgt: 

  1. Visual Studio Code öffnen
  2. Die Tastenkombination `CTRL` + `SHIFT` + `X` drücken und in der Suchleiste die erwähnten Extensions suchen
  3. Auf `Install` klicken und anschliessend auf `Reload`, um die Extension in den Arbeitsbereich zu laden.

*Um die Dokumentation lokal mit Visual Studio Code zu bearbeiten, arbeite ich folgendermassen:*

  1. Änderungen am Readme-File von meinem Repositorys vornehmen
  2. Datei speichern und in der linken Leiste das Symbol mit einer "1" aufrufen
  3. Unter dem Abschnitt *Changes* die betroffenen Files bezüglich ihres Changes "stagen" indem ich auf das "Plus-Symbol" klicke
  4. Nachricht hinterlegen und auf commit klicken
  5. Bei den 3 Punkten (...) auf *Push* klicken
  6. Warten, bis Dateien vollständig hochgeladen wurden

## Git-Client
> [⇧ *Nach oben*](#inhaltsverzeichnis)

Damit ich die Befehle lokal auf dem eigenen PC machen konnte, musste ich den "Git Client", auf Windows "Git/Bash" installieren. 

*Client installieren*
Ich habe die [Client-Installation](https://git-scm.com/downloads) heruntergeladen und installiert.

*Danach habe ich den Client konfiguriert:*
1. Terminal öffnen
2. Git konfigurieren mit Informationen des GitHub-Accounts:


      $ git config --global user.name "StefanZ54"
      $ git config --global user.email "stef4n7@gmail.com"
     

*Damit ich meine Files lokal bearbeiten und hochladen kann, habe ich mein Repository heruntergeladen und aktualisiert.*

1. Terminal öffnen
2. Ordner für Repository erstellen:
      $ cd C:\Users\stefan.seslak\Desktop\Meinrepository
      $ mkdir M300_Stefan
     
3. Repository mit SSH klonen:
      $ git clone git@github.com:StefanZ54/M300_Stefan.git

      Cloning into 'M300_Stefan'...
     
4. Repository aktualisieren und Status anzeigen:
      $ git pull

      Already up to date.
    

## SSH-Key 
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Zuerst musste ich Lokal einen SSH-Key erstellen für mein Repository:*

1.  Folgenden Befehl mit der Account-E-Mail von GitHub in die Bash einfügen damit der Schlüssel generiert wird:
      $  ssh-keygen -t rsa -b 4096 -C "stef4n7@gmail.com"
    
2. Neuer SSH-Key wird erstellt:
      Generating public/private rsa key pair.
    
3. Bei der Abfrage, unter welchem Namen der Schlüssel gespeichert werden soll, die Enter-Taste drücken (für Standard):
      Enter a file in which to save the key (~/.ssh/id_rsa): [Press enter]
    
4. Nun habe ich ein Passwort für den Key festgelegt:
      Enter passphrase (empty for no passphrase): [Passwort]
      Enter same passphrase again: [Passwort wiederholen]
    
*Danach kann ich den SSH-Key dem Client hinzufügen:*
1. Auf www.github.com im Benutzerkonto *Settings* aufrufen
2.  Unter den Menübereichen auf der linken Seite zum Abschnitt *SSH und GPG keys* wechseln
3.  Auf *New SSH key* klicken
4.  Im Formular unter *Title* die Bezeichnung vergeben()
5.  Den Key von der Datei *C:\Users\stefan.selak\.ssh\id_rsa.pub* kopieren und im Github einfügen und auf *Add SSH key* klicken




## GitHub Account
> [⇧ *Nach oben*](#inhaltsverzeichnis)

*Ich habe folgendermassen einen Github Account erstellt:*
1. Auf [GitHub.com](https://github.com) gehen
2. Auf *Sign up* klicken
3. Username, E-mail und Passwort eingeben
4. Auf *Create an Account* klicken
5. E-Mail zur Verifizierung bestätigen



> [⇧ *Nach oben*](#inhaltsverzeichnis)


## Docker

- Ich habe [Docker Desktop](https://hub.docker.com/editions/community/docker-ce-desktop-windows) heruntergeladen und installiert 
- Ich habe eine Dockerfile erstellt und folgendes eingegeben:

FROM php:7.1-apache
RUN docker-php-ext-install mysqli

*Hier wird das php image benutzt. Zusätzlich wird eine Extension für PHP und mysql installiert, damit man phpmyadmin laufen lassen kann.*

- Danach habe ich noch ein Compose File ertsellt dort sind die einzelnen Serverressourcen deffiniert.

-Mit docker-compose up wird dann das File ausgeführt und die Server eingerichtet.

> [⇧ *Nach oben*](#inhaltsverzeichnis)


## Sicherheit

Ich habe hier 3 Sicherheitsaspekte gewählt.

1. Image Poisening
   Um Dies zu verhindern, werden nur Sicher Images aus dem Docker Hub benutzt.

2. Überwachung
   Um die Container zu überwachen habe ich das PRTG-Tool installiert und dort Sensoren eingerichtet

3. Ressorurcen limitieren
   Im Compose File habe ich limiten für die Ressourcen der Container deffiniert.

## Testen

### Webserver
- Ich habe den Websever getestet, indem ich im Web-Browser Localhost(127.0.0.1) eingegeben habe.
- Mein index File welches bei mir hinterlegt ist wird korrekt angezeigt. 


### Phpmyadmin
-Ich habe die Graphische Oberfläche von MYSQL getestet, indem ich localhost(127.0.0.1) und zusätzlich noch den Port 8080 im Webbrowser eingegeben habe.
-Die Oberfläche wird angezeigt und das Login Funtioniert auch mit den hinterlegten logins. 
    


> [⇧ *Nach oben*](#inhaltsverzeichnis)
 
## Webserver

*Ich habe im Compose-File den Webserver installiert:*

1. Compose-File öffnen
2. Folgende Zeilen einfügen:
  php:
    build: php
    ports:
      - "80:80"
      - "443:443"
    restart: on-failure
    volumes:
      - ./php/www:/var/www/html
    cpus: 1
    mem_limit: 1024m
     
## MYSQL

*Ich habe im Compose-File MYSQL installiert:*

1. Compose-File öffnen
2. Folgende Zeilen einfügen:
  db:
    image: mysql:5.7
    ports:
     - "3306:3306"
    volumes:
     - /var/lib/mysql
    restart: on-failure
    environment:
     - MYSQL_ROOT_PASSWORD=1234Abcd
     - MYSQL_DATABASE=datenbank
    cpus: 1
    mem_limit: 1024m

> [⇧ *Nach oben*](#inhaltsverzeichnis)
    
## Phpmyadmin

*Ich habe im Compse-File phpmyadmin installiert(Graphische Oberfläche für MYSQL):*

1. Compose-File öffnen
2. Folgende Zeilen einfügen:
  phpmyadmin:
    image: phpmyadmin/phpmyadmin
    links:
        - db:db
    ports:
        - 8080:80
    restart: on-failure
    environment:
        MYSQL_ROOT_PASSWORD: 1234Abcd
    cpus: 1
    mem_limit: 1024m   



> [⇧ *Nach oben*](#inhaltsverzeichnis)
 

## Vergleich Vorwissen - Wissenszuwachs

*Bereits bekannt*

- Die bereits bekannte aufwendigere Virtualisierung, habe ich schon oft  in VMware,Hyper-V und Virtualbox in der Schule oder im Geschäft gemacht.
- Den Begriff Container kannte ich schon aber habe ich noch nie angewendet.

*Neu*

 - Docker war vor diesem Modul ein ganz neues Gebiet für mich und ich brauchte schon etwas Zeit um damit zurecht zu kommen.
 - Microservices kannte ich gar nicht vor diesem Modul waren mir nur monolytische Applikationen und Dienste bekannt. Nun weiss ich, dass es andere varianten also mit kleinen unabhängigen "Teilen" eine Applikation bereitzustellen.
 - Nun verstehe ich den Begriff Containeriserung auch besser. Der grösste Unterschied, ist dass Container den Kernel des physischen Host benutzen im gegensatz zur alten virtualisierung. Man kann aber auch Dienste in Container packen und bereitstellen.


*Fazit*

In diesem Modul habe ich viel neues gelernt. Jetzt weiss ich dass es auch andere einfachere Wege gibt Virtuelle Maschinen zu erstellen und Applikationen bereitzustellen. Ich bin auch zufrieden mit dem Endprodukt
> [⇧ *Nach oben*](#inhaltsverzeichnis)
## Reflexion

Für die LB3 hatte ich recht viel Zeit gebraucht um zu verstehen, wie Docker funktioniert und was das genau ist. Wenn man es versteht ist es wirklich praktisch so neue Virtuelle Maschinen/Dienste in Betrieb zu nehmen und vorallem kann man das immer wieder als Vorlage benutzen. Schlussendlich hatte ich einen Mailserver, Webserver und zusätzlich noch das Frontend des Mailservers. Ich habe gelernt wie man einen Container bildet und wie man sie in Betrieb nimmt. Alles in allem muss ich wirklich sagen, dass diese LB3 sehr lehrreich für mich war. 
> [⇧ *Nach oben*](#inhaltsverzeichnis)