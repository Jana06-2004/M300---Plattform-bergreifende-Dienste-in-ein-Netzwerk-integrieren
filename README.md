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


# 10.02.2026
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