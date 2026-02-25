# M300---Plattform-bergreifende-Dienste-in-ein-Netzwerk-integrieren

Hallo! Test!

# Dokumentation M300 
<!-- TOC -->

- [M300---Plattform-bergreifende-Dienste-in-ein-Netzwerk-integrieren](#m300---plattform-bergreifende-dienste-in-ein-netzwerk-integrieren)
- [Dokumentation M300](#dokumentation-m300)
- [M300 – 10 Einrichtung der Toolumgebung](#m300--10-einrichtung-der-toolumgebung)
  - [1. Ausgangslages](#1-ausgangslages)
  - [2. Ziel](#2-ziel)
  - [3. Einrichtung GitHub](#3-einrichtung-github)
    - [Account erstellen](#account-erstellen)
    - [Repository erstellen](#repository-erstellen)
    - [SSH-Key erstellen](#ssh-key-erstellen)
  - [4. Installation Git (Git Bash)](#4-installation-git-git-bash)
    - [Konfiguration](#konfiguration)
    - [Repository klonen](#repository-klonen)
    - [Änderungen hochladen](#änderungen-hochladen)
  - [5. Installation VirtualBox](#5-installation-virtualbox)
    - [Ubuntu herunterladen](#ubuntu-herunterladen)
    - [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)
    - [ISO einbinden](#iso-einbinden)
    - [System aktualisieren](#system-aktualisieren)
    - [Apache installieren](#apache-installieren)
  - [6. Installation Vagrant](#6-installation-vagrant)
    - [Erste VM erstellen](#erste-vm-erstellen)
    - [SSH-Verbindung](#ssh-verbindung)
    - [Automatisierung testen](#automatisierung-testen)
  - [7. Visual Studio Code einrichten](#7-visual-studio-code-einrichten)
    - [Extensions installiert](#extensions-installiert)
    - [Einstellungen angepasst](#einstellungen-angepasst)
  - [8. Ergebnis](#8-ergebnis)
  - [9. Erkenntnisse](#9-erkenntnisse)
  - [10. Fazit](#10-fazit)
- [M300 – 20 Infrastruktur-Automatisierung](#m300--20-infrastruktur-automatisierung)
  - [1. Ausgangslage](#1-ausgangslage)
  - [2. Ziel](#2-ziel-1)
  - [3. Cloud Computing Grundlagen](#3-cloud-computing-grundlagen)
    - [**Service-Modelle**](#service-modelle)
  - [4. Dynamic Infrastructure Platform](#4-dynamic-infrastructure-platform)
    - [Beispiele](#beispiele)
  - [5. Infrastructure as Code (IaC)](#5-infrastructure-as-code-iac)
  - [6. Vagrant – Automatisierte VM-Erstellung](#6-vagrant--automatisierte-vm-erstellung)
    - [Schritte](#schritte)
    - [Provisionierung](#provisionierung)
    - [Fehler \& Lösungen](#fehler--lösungen)
  - [7. Packer – Eigene Images erstellen](#7-packer--eigene-images-erstellen)
    - [Installation \& Test](#installation--test)
    - [Image erstellen](#image-erstellen)
    - [Fehler \& Lösungen](#fehler--lösungen-1)
  - [8. AWS Cloud Integration](#8-aws-cloud-integration)
    - [Schritte](#schritte-1)
    - [Vagrant AWS Plugin installieren](#vagrant-aws-plugin-installieren)
    - [VM in AWS erstellen](#vm-in-aws-erstellen)
    - [Fehler \& Lösungen](#fehler--lösungen-2)
  - [9. Varianten – Pro / Kontra](#9-varianten--pro--kontra)
    - [Lokale Virtualisierung (VirtualBox)](#lokale-virtualisierung-virtualbox)
    - [AWS Cloud](#aws-cloud)
    - [Packer vs. Manuelle Installation](#packer-vs-manuelle-installation)
  - [10. Verifikation \& Tests](#10-verifikation--tests)
  - [11. Erkenntnisse](#11-erkenntnisse)
  - [12. Fazit](#12-fazit)
- [M300 – 25 Infrastruktur-Sicherheit](#m300--25-infrastruktur-sicherheit)
  - [1. Ausgangslage](#1-ausgangslage-1)
  - [2. Ziel](#2-ziel-2)
  - [3. Firewall \& Reverse Proxy](#3-firewall--reverse-proxy)
    - [3.1 Firewall (UFW)](#31-firewall-ufw)
    - [Regeln konfigurieren](#regeln-konfigurieren)
    - [Tests](#tests)
    - [Fehler \& Lösungen](#fehler--lösungen-3)
  - [3.2 Reverse Proxy](#32-reverse-proxy)
    - [Module aktivieren](#module-aktivieren)
    - [Beispielkonfiguration](#beispielkonfiguration)
  - [4. Benutzer- \& Rechteverwaltung](#4-benutzer---rechteverwaltung)
    - [Fehler \& Lösungen](#fehler--lösungen-4)
  - [5. SSH – Sichere Kommunikation](#5-ssh--sichere-kommunikation)
    - [Public-Key-Verfahren](#public-key-verfahren)
    - [SSH-Tunnel](#ssh-tunnel)
  - [6. Authentifizierung \& Autorisierung](#6-authentifizierung--autorisierung)
    - [6.1 HTTPS aktivieren](#61-https-aktivieren)
    - [6.2 Passwortschutz](#62-passwortschutz)
    - [6.3 LDAP](#63-ldap)
  - [7. Verifikation \& Tests](#7-verifikation--tests)
  - [8. Varianten – Pro / Kontra](#8-varianten--pro--kontra)
    - [UFW](#ufw)
    - [Reverse Proxy](#reverse-proxy)
    - [SSH Public Key](#ssh-public-key)
    - [LDAP](#ldap)
  - [9. Erkenntnisse](#9-erkenntnisse-1)
  - [10. Fazit](#10-fazit-1)
- [M300 – 30 Container](#m300--30-container)
  - [1. Ausgangslage](#1-ausgangslage-2)
  - [2. Ziel](#2-ziel-3)
  - [3. Container – Grundlagen](#3-container--grundlagen)
    - [Geschichte](#geschichte)
  - [4. Docker – Architektur \& Konzepte](#4-docker--architektur--konzepte)
    - [Docker Daemon](#docker-daemon)
    - [Docker Client](#docker-client)
    - [Images](#images)
    - [Container](#container)
    - [Docker Registry](#docker-registry)
  - [5. Wichtige Docker-Befehle](#5-wichtige-docker-befehle)
    - [Container starten](#container-starten)
    - [Container anzeigen](#container-anzeigen)
    - [Images anzeigen](#images-anzeigen)
    - [Container löschen](#container-löschen)
    - [Images löschen](#images-löschen)
    - [Container Infos](#container-infos)
  - [6. Dockerfile – Eigene Images erstellen](#6-dockerfile--eigene-images-erstellen)
    - [Build \& Run](#build--run)
    - [Wichtige Dockerfile-Anweisungen](#wichtige-dockerfile-anweisungen)
    - [Testen im Container](#testen-im-container)
  - [7. Netzwerk-Anbindung](#7-netzwerk-anbindung)
    - [Ports weiterleiten](#ports-weiterleiten)
    - [Dockerfile](#dockerfile)
    - [MySQL-Zugriff vom Host](#mysql-zugriff-vom-host)
    - [Docker Netzwerke](#docker-netzwerke)
    - [Netzwerke verwalten](#netzwerke-verwalten)
    - [Container in Netzwerk starten](#container-in-netzwerk-starten)
  - [8. Volumes – Persistente Daten](#8-volumes--persistente-daten)
    - [Arten von Volumes](#arten-von-volumes)
    - [Beispiele](#beispiele-1)
    - [Daten prüfen](#daten-prüfen)
  - [9. Image-Bereitstellung](#9-image-bereitstellung)
    - [Tags \& Namen](#tags--namen)
    - [Docker Hub Upload](#docker-hub-upload)
    - [Suche \& Pull](#suche--pull)
    - [Export / Import](#export--import)
    - [Private Registry](#private-registry)
  - [10. Verifikation \& Tests](#10-verifikation--tests-1)
  - [11. Varianten – Pro / Kontra](#11-varianten--pro--kontra)
    - [Container vs. VMs](#container-vs-vms)
    - [Docker Hub vs. Private Registry](#docker-hub-vs-private-registry)
  - [12. Erkenntnisse](#12-erkenntnisse)
  - [13. Fazit](#13-fazit)
- [M300 – 35 Container-Sicherheit](#m300--35-container-sicherheit)
  - [1. Ausgangslage](#1-ausgangslage-3)
  - [2. Ziel](#2-ziel-4)
  - [3. Protokollieren \& Überwachen](#3-protokollieren--überwachen)
    - [3.1 Logging](#31-logging)
    - [Logging-Treiber](#logging-treiber)
    - [Beispiele](#beispiele-2)
    - [Log-Streaming](#log-streaming)
    - [Syslog-Logging](#syslog-logging)
  - [3.2 Monitoring – cAdvisor](#32-monitoring--cadvisor)
  - [4. Container sichern \& beschränken](#4-container-sichern--beschränken)
    - [4.1 Best Practices](#41-best-practices)
      - [Container **nicht als root** betreiben](#container-nicht-als-root-betreiben)
      - [setuid/setgid-Binaries entfernen](#setuidsetgid-binaries-entfernen)
      - [Dateisystem schreibgeschützt machen](#dateisystem-schreibgeschützt-machen)
      - [Speicher begrenzen](#speicher-begrenzen)
      - [CPU begrenzen](#cpu-begrenzen)
      - [Neustarts begrenzen](#neustarts-begrenzen)
      - [Capabilities reduzieren](#capabilities-reduzieren)
      - [ulimit anwenden](#ulimit-anwenden)
  - [5. Container nach Host trennen](#5-container-nach-host-trennen)
  - [6. Weitere Sicherheitstipps](#6-weitere-sicherheitstipps)
  - [7. Automatisches Bauen (Continuous Integration)](#7-automatisches-bauen-continuous-integration)
    - [Tools](#tools)
  - [8. Jenkins \& Blue Ocean](#8-jenkins--blue-ocean)
    - [Blue Ocean starten](#blue-ocean-starten)
    - [Docker Images automatisch bauen](#docker-images-automatisch-bauen)
    - [Beispiel-Test](#beispiel-test)
  - [9. Verifikation \& Tests](#9-verifikation--tests)
  - [10. Erkenntnisse](#10-erkenntnisse)
  - [11. Fazit](#11-fazit)
- [M300 – 40 Kubernetes (K8s)](#m300--40-kubernetes-k8s)
  - [1. Ausgangslage](#1-ausgangslage-4)
  - [2. Ziel](#2-ziel-5)
  - [3. Grundbegriffe](#3-grundbegriffe)
    - [**Service Discovery**](#service-discovery)
    - [**Vernetzung (Networking)**](#vernetzung-networking)
    - [**Lastverteilung (Load Balancing)**](#lastverteilung-load-balancing)
    - [**Cluster**](#cluster)
  - [4. Kubernetes (K8s)](#4-kubernetes-k8s)
    - [**Merkmale**](#merkmale)
  - [5. Kubernetes‑Objekte](#5-kubernetesobjekte)
    - [**Pod**](#pod)
    - [**ReplicaSet**](#replicaset)
    - [**Deployment**](#deployment)
    - [**Service**](#service)
    - [**Ingress**](#ingress)
  - [6. Beispiel‑YAML – Apache Webserver](#6-beispielyaml--apache-webserver)
  - [7. Erkenntnisse](#7-erkenntnisse)
  - [8. Fazit](#8-fazit)

<!-- /TOC -->
# M300 – 10 Einrichtung der Toolumgebung
 
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


# M300 – 35 Container-Sicherheit

## 1. Ausgangslage
Im Modul M300 wurde nach der Einführung in Docker und Containerisierung der Fokus auf die **Sicherheit** von containerisierten Anwendungen gelegt. Container sind leichtgewichtig und flexibel, bringen jedoch neue Risiken und Herausforderungen mit sich. Um Container produktiv betreiben zu können, müssen Logging, Monitoring, Absicherung und automatisierte Builds gewährleistet sein.

---

## 2. Ziel
Ziele dieses Auftrags waren:
- Logs und Monitoring für Container einrichten
- Sicherheitsrisiken verstehen und reduzieren
- Container gegen Angriffe absichern
- Ressourcenbeschränkungen anwenden
- Jenkins & Blue Ocean für automatisierte Builds nutzen
- CI/CD-Grundlagen verstehen

---

## 3. Protokollieren & Überwachen

### 3.1 Logging
Container senden standardmässig alles an **STDOUT** und **STDERR**. Diese Logs können mit
```bash
docker logs <container>
```
abgerufen werden.

### Logging-Treiber
- `json-file` (Standard)
- `syslog` (Host-Systemlog)
- `none` (Logging deaktiviert)

### Beispiele
```bash
docker run --name logtest ubuntu bash -c 'echo "stdout"; echo "stderr" >&2'
docker logs logtest
docker rm logtest
```

### Log-Streaming
```bash
docker logs -f streamtest
```

### Syslog-Logging
```bash
docker run -d --log-driver=syslog ubuntu
```
Logs anzeigen:
```bash
tail -f /var/log/syslog
```

---

## 3.2 Monitoring – cAdvisor
cAdvisor zeigt Metriken wie:
- CPU
- RAM
- Netzwerk
- Laufzeit
- I/O

Start:
```bash
docker run -d --name cadvisor -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys:ro -v /var/lib/docker/:/var/lib/docker:ro -p 8080:8080 google/cadvisor:latest
```
Zugriff: **http://localhost:8080**

---

## 4. Container sichern & beschränken
Container haben besondere Sicherheitsrisiken, unter anderem:
- Kernel Exploits
- DoS-Angriffe
- Container-Breakouts
- Manipulierte Images
- Verlorene Secrets
- Zu hohe Berechtigungen

### 4.1 Best Practices
#### Container **nicht als root** betreiben
```bash
RUN groupadd -r user_grp && useradd -r -g user_grp user
USER user
```

#### setuid/setgid-Binaries entfernen
```bash
RUN find / -perm +6000 -type f -exec chmod a-s {} \; || true
```

#### Dateisystem schreibgeschützt machen
```bash
docker run --read-only ubuntu touch x
```

#### Speicher begrenzen
```bash
docker run -m 128m --memory-swap 128m image
```

#### CPU begrenzen
```bash
docker run -c 512 image
```

#### Neustarts begrenzen
```bash
docker run -d --restart=on-failure:10 my-image
```

#### Capabilities reduzieren
```bash
docker run --cap-drop all --cap-add CHOWN ubuntu
```

#### ulimit anwenden
```bash
docker run --ulimit cpu=12:14 image
```

---

## 5. Container nach Host trennen
In Multi-Tenant-Setups sollte jeder Benutzer einen eigenen Docker-Host haben, um Breakouts oder Angriffe zu isolieren.

---

## 6. Weitere Sicherheitstipps
- Container immer aktuell halten
- Debug-Modi deaktivieren
- Nur Reverse Proxy nach aussen öffnen
- SELinux / AppArmor aktivieren
- Secrets niemals im Image speichern
- Netzwerkzugriff stark begrenzen
- Regelmässige Security-Audits durchführen
- Interne Kommunikation verschlüsseln

---

## 7. Automatisches Bauen (Continuous Integration)
Continuous Integration (CI) bedeutet:
- Automatisches Bauen nach jedem Commit
- Automatische Tests
- Höhere Softwarequalität
- Kürzere Release-Zyklen

### Tools
- TravisCI
- Jenkins
- Blue Ocean (GUI-Erweiterung für Jenkins)

---

## 8. Jenkins & Blue Ocean
### Blue Ocean starten
```bash
docker run --rm -u root -p 8082:8080 -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock -v "$HOME":/home jenkinsci/blueocean
```

Zugriff über: **http://localhost:8082**

### Docker Images automatisch bauen
Nach erfolgreichem Build erscheinen neue Images:
```bash
docker image ls
```

### Beispiel-Test
```bash
docker run -p 8081:8080 -d misegr/scsesi_order
```
Browser öffnen: **http://localhost:8081**

---

## 9. Verifikation & Tests
Erfolgreich getestet wurden:
- Logging (json, syslog)
- Monitoring (cAdvisor)
- Rechte- und Ressourcenbeschränkungen
- Sicherheitsmechanismen
- CI/CD-Pipelines in Jenkins
- Automatischer Docker-Build
- Bereitstellung der Applikation

**Ergebnis:** Container liefen sicher, stabil und reproduzierbar.

---

## 10. Erkenntnisse
- Container-Sicherheit ist entscheidend für Produktivsysteme
- Monitoring ist unverzichtbar
- DoS-Risiken lassen sich durch Limits stark reduzieren
- CI/CD steigert Qualität und Sicherheit
- Root in Containern vermeiden
- Images immer verifizieren

---

## 11. Fazit
In diesem Auftrag wurde vermittelt:
- Wie Container überwacht werden
- Wie man Container absichert
- Wie Ressourcen kontrolliert werden
- Wie automatisierte Builds funktionieren

Damit sind alle Grundlagen geschaffen, um Container sicher, performant und professionell zu betreiben.


# M300 – 40 Kubernetes (K8s)

## 1. Ausgangslage
Im Modul M300 wurde nach Docker und Containerisierung als nächster Schritt das Thema **Kubernetes (K8s)** eingeführt. Kubernetes ist der Standard für die Orchestrierung von Containern und ermöglicht den automatisierten Betrieb verteilter Anwendungen. In diesem Auftrag ging es darum, wichtige Grundbegriffe zu verstehen und erste Kubernetes‑Konzepte kennenzulernen.

---

## 2. Ziel
Ziel dieses Auftrags war es:
- Die Grundlagen von Service Discovery, Lastverteilung und Clustering zu verstehen
- Kubernetes als Orchestrierungsplattform kennenzulernen
- Die wichtigsten Kubernetes‑Objekte zu verstehen (Pod, ReplicaSet, Deployment, Service, Ingress)
- Die Funktionsweise einer Kubernetes‑Umgebung nachvollziehen zu können
- Ein erstes Verständnis für YAML‑Konfigurationsdateien aufzubauen

---

## 3. Grundbegriffe

### **Service Discovery**
Service Discovery stellt sicher, dass Clients automatisch die benötigten Verbindungsinformationen (IP‑Adresse, Port) zu einer passenden Service‑Instanz erhalten. Dies ist vor allem bei:
- verteilten Systemen
- dynamischen Microservice‑Umgebungen
- häufig wechselnden Instanzen
entscheidend.

Typische Zusatzfunktionen:
- Health Checks
- Failover
- Lastverteilung
- Verschlüsselte Kommunikation
- Isolation von Service‑Gruppen

---

### **Vernetzung (Networking)**
Bei der Containervernetzung geht es nicht um physische Kabel, sondern darum, dass zwischen Containern und Hosts eine funktionierende Route existiert – z. B. über das Internet oder einen Switch. Kubernetes übernimmt:
- Routing
- IP‑Adressierung
- DNS‑Namen
- interne Service‑Kommunikation

Service Discovery sorgt dafür, dass Clients Instanzen finden – Networking stellt sicher, dass sie erreichbar sind.

---

### **Lastverteilung (Load Balancing)**
Load Balancing verteilt Anfragen gleichmässig auf mehrere Instanzen eines Services. Dies ist besonders wichtig bei:
- Webservern
- Microservices
- skalierenden Anwendungen

Kubernetes nutzt Services und Ingress, um Lastverteilung automatisch bereitzustellen.

---

### **Cluster**
Ein Kubernetes‑Cluster besteht aus mehreren miteinander verbundenen Computern:

- **Master Node** (Steuerung)
- **Worker Nodes** (führen Container aus)

Cluster werden u. a. eingesetzt für:
- High Performance Computing (HPC)
- High Availability (HA)

Der Cluster wird häufig als **Serverfarm** bezeichnet.

---

## 4. Kubernetes (K8s)
Kubernetes ist ein Open‑Source‑System zur Automatisierung von:
- Bereitstellung von Containern
- Skalierung
- Verwaltung von containerisierten Anwendungen

Es wurde ursprünglich von Google entwickelt und später der **Cloud Native Computing Foundation (CNCF)** übergeben. Kubernetes wird heute von nahezu allen grossen Cloud‑Anbietern unterstützt:
- Microsoft Azure
- Amazon AWS
- IBM Bluemix
- Red Hat OpenShift

### **Merkmale**
- Immutable Infrastruktur (Container werden ersetzt, nicht verändert)
- Deklarative Konfiguration
- Selbstheilende Systeme (Neustart bei Absturz)
- Entkoppelte APIs (Services, Ingress)
- Skalierbarkeit durch Änderung der Deklaration
- Anwendungsorientiertes Denken statt Serverdenken
- Infrastruktur wird abstrahiert

---

## 5. Kubernetes‑Objekte

### **Pod**
Ein Pod ist die kleinste ausführbare Einheit in Kubernetes und enthält einen oder mehrere Container.

### **ReplicaSet**
Stellt sicher, dass immer die gewünschte Anzahl Pods aktiv ist.

### **Deployment**
Erweitert ReplicaSets um deklarative Updates (z. B. Version 1.0 → 1.1 mehrere Container gleichzeitig).

### **Service**
Bietet eine stabile Verbindung zu Pods (IP & Port). Pods können ersetzt werden, der Service bleibt unverändert.

### **Ingress**
Funktioniert ähnlich wie ein Reverse Proxy und stellt externen Zugriff über URLs bereit.

Eine anschauliche Einführung bietet die Broschüre **„Phippy Goes to the Zoo – A Kubernetes Story“**.

---

## 6. Beispiel‑YAML – Apache Webserver
Ein Apache‑Server kann mit Kubernetes‑YAML wie folgt bereitgestellt werden:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: apache
  labels:
    app: apache
    group: web
    tier: frontend
spec:
  type: LoadBalancer
  ports:
  - port: 80
    protocol: TCP
  selector:
    app: apache
---
apiVersion: apps/v1
kind: Deployment
metadata:
  name: apache
spec:
  replicas: 1
  selector:
    matchLabels:
      app: apache
  template:
    metadata:
      labels:
        app: apache
        group: web
        tier: frontend
    spec:
      containers:
      - name: apache
        image: httpd
        ports:
        - containerPort: 80
          name: apache
```

Dieses Beispiel zeigt:
- einen LoadBalancer‑Service
- ein Deployment mit einem Pod
- ein Container‑Image aus Docker Hub (`httpd`)

---

## 7. Erkenntnisse
- Kubernetes abstrahiert komplette Infrastruktur
- Service Discovery ist essenziell für Microservice‑Kommunikation
- YAML ermöglicht deklarative und reproduzierbare Deployments
- Services bleiben stabil, auch wenn Pods ersetzt werden
- Kubernetes bietet automatische Skalierung, Self‑Healing und klare API‑Strukturen

---

## 8. Fazit
Dieser Auftrag vermittelte die Grundlagen von Kubernetes und seinen Konzepten. Durch das Verständnis der Begriffe und Objekte wurde die Basis geschaffen, um zukünftig komplette Kubernetes‑Cluster bereitzustellen und containerisierte Anwendungen skalierbar zu betreiben.