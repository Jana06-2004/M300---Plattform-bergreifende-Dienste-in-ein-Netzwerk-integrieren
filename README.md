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