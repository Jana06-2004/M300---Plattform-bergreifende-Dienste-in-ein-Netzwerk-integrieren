# M300---Plattform-bergreifende-Dienste-in-ein-Netzwerk-integrieren

Hallo! Test!

# Dokumentation M300 – Einrichtung der Toolumgebung
 
## 1. Ausgangslages
Für das Modul M300 musste eine vollständige Arbeitsumgebung eingerichtet werden.  
Diese Umgebung dient dazu, virtuelle Maschinen zu erstellen, Projekte zu verwalten und Infrastruktur automatisiert aufzubauen.
 
Die Toolumgebung besteht aus:
- GitHub  
- Git (Git Bash)  
- VirtualBox  
- Vagrant  
- Visual Studio Code  
 
## 2. Ziel
Das Ziel war es, alle benötigten Programme zu installieren und korrekt zu konfigurieren.  
Am Ende sollte eine funktionierende Umgebung vorhanden sein, mit der virtuelle Maschinen automatisiert erstellt und Projekte versioniert werden können.
 
## 3. Einrichtung GitHub

### Account erstellen
Zuerst wurde ein GitHub-Account erstellt.  
Dieser wird verwendet, um Projekte und Dokumentationen online zu speichern.
 
### Repository erstellen
Ein neues Repository wurde erstellt:
- Name definiert  
- Öffentlich eingestellt  
- README-Datei erstellt  
 
Das Repository dient als zentraler Speicherort für alle Arbeiten im Modul.
 
### SSH-Key erstellen
Damit eine sichere Verbindung zu GitHub möglich ist, wurde ein SSH-Key erstellt:
Der öffentliche Schlüssel wurde im GitHub-Account unter SSH Keys eingefügt 
 
## 4. Installation Git (Git Bash)

Git wurde installiert, um lokal mit dem GitHub-Repository arbeiten zu können.

### Konfiguration

```bash
git config --global user.name "Name"
git config --global user.email "Mail"
```

### Repository klonen

```bash
git clone <repository-link>
```

### Änderungen hochladen

```bash
git add -A
git commit -m "Kommentar"
git push
```

Damit konnten Dateien lokal bearbeitet und online gespeichert werden.

---

## 5. Installation VirtualBox

VirtualBox wurde installiert, um virtuelle Maschinen auszuführen.

### Ubuntu herunterladen

Ein Ubuntu Desktop ISO wurde heruntergeladen und gespeichert.

### Virtuelle Maschine erstellen

In VirtualBox wurde eine neue VM erstellt:

- Typ: Linux Ubuntu  
- RAM: ca. 2 GB  
- Speicher: ca. 25 GB  

### ISO einbinden

Ubuntu wurde anschliessend installiert.

### System aktualisieren

Nach der Installation wurden Updates durchgeführt:

```bash
sudo apt update
sudo apt upgrade
```

### Apache installieren

Ein Webserver wurde installiert:

```bash
sudo apt install apache2
```

Test im Browser:

```
http://localhost
```

---

## 6. Installation Vagrant

Vagrant wurde installiert, um virtuelle Maschinen automatisch zu erstellen.

### Erste VM erstellen

Ordner erstellen:

```bash
mkdir VagrantVM
cd VagrantVM
```

VM initialisieren und starten:

```bash
vagrant init ubuntu/xenial64
vagrant up
```

### SSH-Verbindung

```bash
vagrant ssh
```

Die VM lief nun automatisch und konnte verwendet werden.

---

### Automatisierung testen

Ein Beispielprojekt mit Webserver wurde gestartet:

```bash
vagrant up
```

Webseite über Browser testen:

```
http://localhost:8080
```

VM wieder löschen:

```bash
vagrant destroy -f
```


## 7. Visual Studio Code einrichten
Visual Studio Code wurde als Entwicklungsumgebung installiert.
 
### Extensions installiert
- Markdown All in One  
- Vagrant Extension  
- PDF Extension  
 
Diese helfen beim Schreiben der Dokumentation und beim Arbeiten mit Vagrant.
 
### Einstellungen angepasst
Bestimmte Ordner wie `.vagrant` wurden ausgeschlossen, damit sie nicht ins Repository hochgeladen werden.
 
## 8. Ergebnis
Die komplette Toolumgebung wurde erfolgreich eingerichtet.  
Alle Programme funktionieren korrekt zusammen.

Es ist nun möglich:
- Projekte mit Git zu verwalten  
- Virtuelle Maschinen zu erstellen  
- Infrastruktur zu automatisieren  
- Dokumentationen zu schreiben  
 
## 9. Erkenntnisse
Die Einrichtung der Umgebung ist eine wichtige Grundlage für die weiteren Module.  
Durch die Kombination der Tools kann effizient und strukturiert gearbeitet werden.  
Besonders Vagrant erleichtert die Erstellung von virtuellen Maschinen erheblich.
 
## 10. Fazit
Die eingerichtete Toolumgebung bildet die Basis für Infrastructure as Code und Cloud-Themen im Modul M300.  
Mit Git, VirtualBox, Vagrant und Visual Studio Code steht eine vollständige Entwicklungsumgebung zur Verfügung.


# M300 – 20 Infrastruktur-Automatisierung

## 1. Ausgangslage
Im Modul M300 wurde im zweiten Schritt das Thema **Infrastruktur-Automatisierung** behandelt. Dabei ging es darum, eine dynamische Infrastruktur-Plattform (Private Cloud) praktisch aufzubauen.
Verwendete Tools:

**Bereits vorhanden:**
- GitHub
- Git
- VirtualBox
- Vagrant
- Visual Studio Code

**Neu hinzugekommen:**
- Packer
- AWS (Amazon Web Services)
- Vagrant AWS Plugin

---

## 2. Ziel
Ziele der Aufgabe:

- Cloud-Modelle (IaaS, PaaS, SaaS, CaaS) verstehen
- Infrastructure as Code (IaC) erklären
- Automatisierte VM-Erstellung mit Vagrant
- Eigene Images mit Packer bauen
- VM in der Cloud (AWS) automatisch bereitstellen

Endergebnis:
→ Eine reproduzierbare, automatisierte Infrastruktur.

---

## 3. Cloud Computing Grundlagen
Cloud Computing bedeutet, IT‑Ressourcen über ein Netzwerk bereitzustellen statt lokal zu betreiben.

### **Service-Modelle**
**Infrastructure as a Service (IaaS)**
Der Benutzer verwaltet virtuelle Maschinen selbst.
Beispiel: *AWS EC2*

**Platform as a Service (PaaS)**
Nur die Anwendung wird bereitgestellt, die Infrastruktur übernimmt der Anbieter.
Beispiel: *Microsoft Azure*

**Software as a Service (SaaS)**
Fertige Software wird direkt im Browser genutzt.
Beispiel: *Google Workspace*

**Container as a Service (CaaS)**
Containerisierte Anwendungen werden verwaltet.
Beispiel: *Docker*

---

## 4. Dynamic Infrastructure Platform
Eine dynamische Infrastruktur-Plattform stellt virtualisierte Ressourcen bereit:
CPU • RAM • Storage • Netzwerk

### Beispiele
**Public Cloud:**
- Amazon Web Services
- Microsoft Azure

**Private Cloud:**
- OpenStack
- CloudStack

**Lokale Virtualisierung:**
- Oracle VM VirtualBox

---

## 5. Infrastructure as Code (IaC)
Früher wurden Server manuell eingerichtet. Heute geschieht dies automatisch über Konfigurationsdateien.

IaC bedeutet:
- Infrastruktur wird als Code definiert
- versioniert (Git)
- getestet
- automatisch ausgerollt

**Vorteile:**
- Wiederholbarkeit
- Schnellere Bereitstellung
- Weniger Fehler
- Bessere Zusammenarbeit

---

## 6. Vagrant – Automatisierte VM-Erstellung
Vagrant erstellt virtuelle Maschinen automatisiert.

### Schritte
**Box hinzufügen:**
```bash
vagrant box add ubuntu/xenial64
```

**Projekt erstellen:**
```bash
mkdir myserver
cd myserver
vagrant init ubuntu/xenial64
vagrant up
```

**SSH Verbindung:**
```bash
vagrant ssh
```

### Provisionierung
Im *Vagrantfile*:
```ruby
config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update
  sudo apt-get -y install apache2
SHELL
```

**Test:**
Browser öffnen:
`http://localhost:8080` → Apache Testseite

### Fehler & Lösungen
**Port belegt:**
→ anderen Host-Port im Vagrantfile definieren

**VM startet nicht:**
```bash
vagrant destroy -f
vagrant up
```

---

## 7. Packer – Eigene Images erstellen
Packer erstellt eigene VM‑Images.

### Installation & Test
- Packer herunterladen
- In Verzeichnis kopieren
- PATH setzen
- Test:
```bash
packer
```

### Image erstellen
Benötigt:
- Ubuntu ISO
- JSON-Template
- Preseed Datei
- Shell-Skripte

**Build:**
```bash
packer build template.json
```

**Ergebnis:**
- Automatische Ubuntu-Installation
- Konfiguration via Shell
- Erstellung einer Vagrant-Box

### Fehler & Lösungen
- ISO nicht gefunden → Pfad korrigieren
- Preseed lädt nicht → HTTP Server prüfen
- SSH Fehler → SSH Server in Preseed aktivieren

---

## 8. AWS Cloud Integration
Für die Cloud-Integration wurde **AWS** genutzt.

### Schritte
- Root Account erstellt
- IAM User (`vagrant-user`)
- *EC2FullAccess* Policy
- Security Group (Port 22 & 80 offen)
- Key Pair erstellt

### Vagrant AWS Plugin installieren
```bash
vagrant plugin install vagrant-aws
vagrant box add dummy https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box
```

### VM in AWS erstellen
```bash
vagrant up web --provider=aws
```

**Ergebnis:**
- EC2 Instanz automatisch erstellt
- Apache installiert
- Zugriff über Public IP

### Fehler & Lösungen
- Auth Fehler → Keys überprüfen
- SSH Timeout → Security Group prüfen
- Falsche Region → Region in config.rb anpassen

---

## 9. Varianten – Pro / Kontra

### Lokale Virtualisierung (VirtualBox)
**Vorteile:**
- Keine Cloud-Kosten
- Offline nutzbar
- Einfach zu testen

**Nachteile:**
- Begrenzte Ressourcen
- Weniger produktionsnah

### AWS Cloud
**Vorteile:**
- Skalierbar
- Realistische Umgebung
- Weltweit verfügbar

**Nachteile:**
- Kosten
- Komplexer
- Sicherheitsrisiko bei Fehlkonfiguration

### Packer vs. Manuelle Installation
**Packer Vorteile:**
- Wiederholbar
- Automatisiert
- Schnell

**Manuell – Nachteile:**
- Fehleranfällig
- Zeitaufwendig
- Nicht standardisiert

---

## 10. Verifikation & Tests
Durchgeführte Tests:

- `vagrant status`
- Browser-Test (Apache)
- SSH Verbindung
- Mehrfaches Destroy & Rebuild
- AWS EC2 Dashboard geprüft

**Ergebnis:**
→ Infrastruktur ist reproduzierbar und stabil.

---

## 11. Erkenntnisse
- IaC reduziert manuelle Fehler deutlich.
- Automatisierung spart viel Zeit.
- Cloud-Plattformen sind leistungsfähig, aber komplex.
- Sicherheit (IAM, SGs, Keys) ist essenziell.

---

## 12. Fazit
Die dynamische Infrastruktur-Plattform wurde erfolgreich umgesetzt.

Mit:
- Vagrant
- Packer
- Oracle VM VirtualBox
- Amazon Web Services

konnte eine automatisierte und reproduzierbare Infrastruktur aufgebaut werden.
Damit ist die Basis für professionelle Cloud- und DevOps-Prozesse geschaffen.


# M300 – 25 Infrastruktur-Sicherheit

## 1. Ausgangslage
Im dritten Teil des Moduls M300 ging es um das Thema **Infrastruktur-Sicherheit**. Während in den vorherigen Aufträgen die Toolumgebung eingerichtet und eine dynamische Infrastruktur aufgebaut wurde, lag der Fokus nun darauf, diese Infrastruktur abzusichern.

Die behandelten Sicherheitsaspekte umfassen:
- Firewall-Konfiguration (UFW)
- Reverse Proxy
- Benutzer- und Rechteverwaltung
- SSH-Sicherheit (Public Keys, Tunnel)
- Authentifizierung & Autorisierung (Apache / LDAP)

---

## 2. Ziel
Ziel dieses Auftrags war es, verschiedene Sicherheitsmechanismen zu verstehen und praktisch umzusetzen, darunter:

- Absicherung der VMs durch eine Firewall
- Nutzung eines Reverse Proxy zur Verschlüsselung und Adressmaskierung
- Saubere Benutzer- und Rechteverwaltung
- Sichere SSH-Verbindungen via Public-Key-Verfahren
- Absicherung des Apache-Webservers mit HTTPS und LDAP

Am Ende sollte eine sichere und geschützte Infrastruktur entstehen.

---

## 3. Firewall & Reverse Proxy

### 3.1 Firewall (UFW)
Zuerst wurden die offenen Ports geprüft:
```bash
netstat -tulpen
```

UFW Installation & Aktivierung:
```bash
sudo apt-get install ufw
sudo ufw enable
```

### Regeln konfigurieren
**SSH nur für Host freigeben:**
```bash
sudo ufw allow from <Meine-IP> to any port 22
```

**HTTP für alle öffnen:**
```bash
sudo ufw allow 80/tcp
```

**MySQL nur für Webserver öffnen:**
```bash
sudo ufw allow from <Web-IP> to any port 3306
```

### Tests
```bash
curl -f 192.168.55.101
curl -f 192.168.55.100:3306
```

### Fehler & Lösungen
- SSH blockiert → falsche Regel → IP korrigiert
- MySQL nicht erreichbar → Webserver-IP falsch → neu gesetzt

---

## 3.2 Reverse Proxy
Apache als Reverse Proxy einrichten.

### Module aktivieren
```bash
sudo a2enmod proxy
sudo a2enmod proxy_html
sudo a2enmod proxy_http
```

### Beispielkonfiguration
```apache
ProxyRequests Off
<Proxy *>
    Order deny,allow
    Allow from all
</Proxy>

ProxyPass /master http://master
ProxyPassReverse /master http://master
```

Ergebnis: Aufrufe wurden korrekt an das Backend weitergeleitet.

---

## 4. Benutzer- & Rechteverwaltung
Linux trennt Benutzer und deren Rechte strikt. Im Auftrag wurde behandelt:

- root, Systembenutzer, normale Benutzer
- Gruppen & Gruppenzugehörigkeiten
- Dateisystemrechte & Inodes

Rechte anzeigen:
```bash
ls -ldh /var/mail
```

Rechte ändern:
```bash
chmod 755 datei
chown user:group datei
chgrp gruppe datei
```

### Fehler & Lösungen
- Falsche Rechte setzten → Apache konnte nicht starten → Rechte korrigiert

---

## 5. SSH – Sichere Kommunikation
SSH wurde erweitert um:
- Public-Key-Verfahren
- SSH-Tunneling

### Public-Key-Verfahren
Key generieren:
```bash
ssh-keygen -t rsa -b 4096
```

Key verteilen:
```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub admin01@db01
```

Login testen:
```bash
ssh admin01@db01
```

### SSH-Tunnel
**Webserver über lokalen Port 8000 erreichen:**
```bash
ssh -L 8000:localhost:80 web01 -N &
```

Test:
```bash
curl http://localhost:8000
```

**MySQL über Remote-Tunnel erreichbar machen:**
```bash
ssh -R 3307:localhost:3306 db01 -N &
```

---

## 6. Authentifizierung & Autorisierung
### 6.1 HTTPS aktivieren
```bash
sudo a2ensite default-ssl.conf
sudo a2enmod ssl
sudo service apache2 restart
```

### 6.2 Passwortschutz
```bash
sudo htpasswd -c /etc/apache2/.htpasswd guest
```

Apache erweitern:
```apache
<Directory "/var/www/html">
    AuthType Basic
    AuthName "Restricted Content"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

### 6.3 LDAP
LDAP-Einträge im LDIF-Format wurden importiert und anschliessend Apache mit LDAP-Auth erweitert.

---

## 7. Verifikation & Tests
Folgende Tests wurden durchgeführt:
- UFW-Regeln geprüft (`sudo ufw status`)
- Curl-Anfragen für Ports
- SSH-Key-Login ohne Passwort
- Reverse Proxy über Browser getestet
- HTTPS-Aufruf
- LDAP-Login via Webinterface

**Ergebnis:** Sicherheitseinstellungen funktionierten stabil und reproduzierbar.

---

## 8. Varianten – Pro / Kontra
### UFW
**Pro:** Einfach, schnell, ideal für kleine Systeme
**Kontra:** Weniger flexibel als iptables

### Reverse Proxy
**Pro:** Versteckt interne Systeme, zusätzliche Sicherheit
**Kontra:** Falsche Konfiguration = Risiko

### SSH Public Key
**Pro:** Sehr hohe Sicherheit
**Kontra:** Einrichtung fehleranfällig

### LDAP
**Pro:** Zentrale Benutzerverwaltung
**Kontra:** Komplex, erfordert präzise Konfiguration

---

## 9. Erkenntnisse
- Sicherheit ist ein Zusammenspiel vieler Komponenten
- Eine Fehlkonfiguration kann Systeme unzugänglich machen
- SSH Public Key ist Passworten überlegen
- LDAP mächtig, aber komplex
- Apache bietet viele Sicherheitsfeatures

---

## 10. Fazit
Mit Firewall, Reverse Proxy, SSH, HTTPS und LDAP wurde die Infrastruktur erfolgreich abgesichert. Damit wurde ein Sicherheitsniveau erreicht, das für professionelle Umgebungen geeignet ist.


# M300 – 30 Container

## 1. Ausgangslage
Im vierten Teil des Moduls M300 wurde das Thema **Containerisierung** behandelt. Dabei wurde untersucht, wie Applikationen und Services in Containern betrieben werden können. Ziel war es, Docker als modernes Werkzeug kennenzulernen, um Anwendungen effizient, portabel und isoliert betreiben zu können.

---

## 2. Ziel
In diesem Auftrag sollten folgende Fähigkeiten erarbeitet werden:
- Applikationen als Container starten und verwalten
- Eigene Images mit Dockerfiles erstellen
- Netzwerke zwischen Containern konfigurieren
- Persistente Speicherung mit Volumes umsetzen
- Images bereitstellen (Docker Hub & private Registry)

Am Ende sollte eine containerisierte Umgebung stehen, die portabel, reproduzierbar und flexibel einsetzbar ist.

---

## 3. Container – Grundlagen
Container ermöglichen eine komplett neue Art der Softwareentwicklung:
- Starten in Millisekunden
- Teilen den Kernel des Host-Systems
- Benötigen kaum Ressourcen
- Ideal für Microservices
- Portabel auf jeder Plattform

### Geschichte
Container existieren schon lange, z.B. durch *chroot*, *FreeBSD Jails*, *Solaris Zones* und *OpenVZ*. 2013 machte Docker Container massentauglich durch:
- Portable Images
- Einfache CLI
- Eigene Registry

---

## 4. Docker – Architektur & Konzepte
Docker besteht aus:

### Docker Daemon
- Startet Container
- Baut und speichert Images

### Docker Client
- Befehlseingabe (CLI)
- Kommuniziert per REST-API

### Images
- Unveränderliche Templates
- Versioniert (Tags, z. B. `ubuntu:20.04`)

### Container
- Laufende Instanzen eines Images
- Änderungen werden im Overlay-Filesystem gespeichert

### Docker Registry
- Speicherung von Images (öffentlich oder privat)

---

## 5. Wichtige Docker-Befehle
### Container starten
```bash
docker run hello-world
docker run -it ubuntu /bin/bash
docker run -d ubuntu sleep 20
docker run -d --rm ubuntu sleep 20
```

### Container anzeigen
```bash
docker ps
docker ps -a
docker ps -aq
```

### Images anzeigen
```bash
docker images
docker image ls
```

### Container löschen
```bash
docker rm <name>
docker rm -f $(docker ps -aq)
```

### Images löschen
```bash
docker rmi ubuntu
docker rmi $(docker images -q -f dangling=true)
```

### Container Infos
```bash
docker logs <id>
docker inspect <id>
docker diff <id>
docker top <id>
```

---

## 6. Dockerfile – Eigene Images erstellen
Ein Dockerfile beschreibt Schritt für Schritt, wie ein Image erstellt wird.

### Build & Run
```bash
docker build -t mysql .
docker run --rm -d --name mysql mysql
```

### Wichtige Dockerfile-Anweisungen
- **FROM** – Basisimage
- **RUN** – Befehle beim Build
- **COPY/ADD** – Dateien kopieren
- **CMD/ENTRYPOINT** – Startbefehle
- **EXPOSE** – Ports freigeben
- **ENV** – Umgebungsvariablen
- **VOLUME** – Persistente Speicherorte

### Testen im Container
```bash
docker exec -it mysql bash
ps -ef
netstat -tulpen
```

---

## 7. Netzwerk-Anbindung
### Ports weiterleiten
```bash
docker run -d -p 3306:3306 mysql
docker run -d -P mysql
```

### Dockerfile
```Dockerfile
EXPOSE 3306
```

### MySQL-Zugriff vom Host
```bash
mysql -u root -p admin -h 127.0.0.1
```

### Docker Netzwerke
Standardnetzwerke:
- **bridge**
- **host**
- **none**

### Netzwerke verwalten
```bash
docker network ls
docker network inspect bridge
```

### Container in Netzwerk starten
```bash
docker run -d --network=isolated_nw --name mysql mysql
docker run -it --network=isolated_nw ubuntu bash
```

---

## 8. Volumes – Persistente Daten
### Arten von Volumes
- Anonyme Volumes
- Host-Mounts
- Named Volumes

### Beispiele
```bash
docker run -v /data busybox
docker run -v ~/data/mysql:/var/lib/mysql mysql
docker volume create mysql
docker run -v mysql:/var/lib/mysql mysql
```

### Daten prüfen
```bash
docker inspect <container>
sudo cat /var/lib/docker/volumes/.../_data/*
```

---

## 9. Image-Bereitstellung
### Tags & Namen
```bash
docker build -t mysql:1.0 .
docker tag mysql username/mysql
```

### Docker Hub Upload
```bash
docker push username/mysql
```

### Suche & Pull
```bash
docker search mysql
docker pull ubuntu
```

### Export / Import
```bash
docker save mysql -o mysql.tar
docker load -i mysql.tar
```

### Private Registry
```bash
docker run -d -p 5000:5000 --restart=always --name registry \  
-v /var/spool/docker-registry:/var/lib/registry registry:2
```

---

## 10. Verifikation & Tests
Durchgeführte Tests:
- Container erfolgreich gestartet und beendet
- Eigene Images gebaut und getestet
- Netzwerkkommunikation via Curl überprüft
- Persistente Daten über Volumes gespeichert
- Images exportiert, importiert und in eine Registry gepusht

**Ergebnis:** Alle Tests funktionierten stabil und reproduzierbar.

---

## 11. Varianten – Pro / Kontra
### Container vs. VMs
**Pro:** Schnell, leichtgewichtig, portabel
**Kontra:** Weniger Isolation als VMs

### Docker Hub vs. Private Registry
**Private Registry – Pro:** Kontrolle, schnell im LAN, keine Limits
**Docker Hub – Pro:** Öffentlich, einfach

---

## 12. Erkenntnisse
- Container sind essenziell für moderne IT-Strukturen
- Docker erleichtert Entwicklung und Deployment enorm
- Volumes und Netzwerke sind fundamental für produktive Umgebungen
- Eigene Images können leicht gebaut und geteilt werden

---

## 13. Fazit
Mit Docker wurde eine vollständige containerisierte Umgebung aufgebaut. Damit stehen nun Werkzeuge bereit, die in Cloud-, DevOps- und Microservice-Architekturen essenziell sind.