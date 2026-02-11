# M300---Plattform-bergreifende-Dienste-in-ein-Netzwerk-integrieren

Hallo! Test!

# 09.02.2026
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
Konfiguration
git config --global user.name "Name"git config --global user.email "Mail" 
Repository klonen
git clone <repository-link>
Änderungen hochladen
git add -A
git commit -m "Kommentar"git push
Damit konnten Dateien lokal bearbeitet und online gespeichert werden.

## 5. Installation VirtualBox
VirtualBox wurde installiert, um virtuelle Maschinen auszuführen.
Ubuntu herunterladen
Ein Ubuntu Desktop ISO wurde heruntergeladen und gespeichert.
Virtuelle Maschine erstellen
In VirtualBox wurde eine neue VM erstellt:
Typ: Linux Ubuntu
RAM: ca. 2 GB
Speicher: ca. 25 GB
ISO eingebunden
Ubuntu wurde anschliessend installiert.
System aktualisieren
Nach der Installation wurden Updates durchgeführt:
sudo apt updatesudo apt upgrade
Apache installieren
Ein Webserver wurde installiert:
sudo apt install apache2
Test im Browser:
http://localhost 

## 6. Installation Vagrant
Vagrant wurde installiert, um virtuelle Maschinen automatisch zu erstellen.
Erste VM erstellen
Ordner erstellt:
mkdir VagrantVMcd VagrantVM
VM initialisiert und gestartet:
vagrant init ubuntu/xenial64
vagrant up
SSH-Verbindung:
vagrant ssh
Die VM lief nun automatisch und konnte verwendet werden.
Automatisierung testen
Ein Beispielprojekt mit Webserver wurde gestartet:
vagrant up
Webseite über Browser getestet:
http://localhost:8080 
VM wieder gelöscht:
vagrant destroy -f

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


# 10.02.2026
# Dokumentation M300 – Infrastruktur-Automatisierung

## 1. Ausgangslage
Im Modul M300 wurde eine dynamische Infrastruktur-Plattform aufgebaut.  
Ziel war es, virtuelle Maschinen automatisiert zu erstellen und zu konfigurieren.  
Die Umsetzung erfolgte mit Vagrant und VirtualBox im Sinne von Infrastructure as Code.

## 2. Zielsetzung
Es sollte eine Umgebung entstehen, in der virtuelle Server nicht manuell, sondern über Konfigurationsdateien erstellt werden.  
Dabei musste sichergestellt werden, dass die Infrastruktur jederzeit reproduzierbar ist.

## 3. Grundlagen

### Cloud Computing
Cloud Computing bezeichnet die Bereitstellung von IT-Ressourcen über ein Netzwerk.  
Dazu gehören:

- Rechenleistung  
- Speicher  
- Netzwerke  
- Software  

Man unterscheidet:

- **IaaS:** virtuelle Maschinen und Infrastruktur  
- **PaaS:** Plattform für Entwicklung  
- **SaaS:** fertige Software über Internet  

### Infrastructure as Code
Infrastructure as Code bedeutet, dass Infrastruktur über Code definiert wird.  
Server, Netzwerke und Software werden automatisch erstellt.

**Vorteile:**
- wiederholbare Umgebung  
- schnellere Bereitstellung  
- weniger Fehler  
- einfache Änderungen  
- Versionierung möglich  

## 4. Verwendete Werkzeuge
Für die Umsetzung wurden folgende Tools eingesetzt:

- VirtualBox als Virtualisierungssoftware  
- Vagrant zur Automatisierung von virtuellen Maschinen  
- Bash/Shell für Provisioning  
- optional Packer zur Image-Erstellung  

## 5. Umsetzung

### 5.1 Vorbereitung
Zuerst wurde die benötigte Software installiert:

- VirtualBox  
- Vagrant  

Danach wurde geprüft, ob Vagrant korrekt installiert ist:

```bash
vagrant --version