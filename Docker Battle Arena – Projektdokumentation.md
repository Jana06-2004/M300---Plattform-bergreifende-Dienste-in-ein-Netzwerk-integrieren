# Docker Battle Arena – Projektdokumentation

## 1. Zweck des gewählten Service
Die **Docker Battle Arena** ist ein containerisiertes Browser‑Shooter‑Game. Das Frontend stellt das Spiel dar, während das Backend die erworbenen Punktzahlen der Spieler*innen verarbeitet und dauerhaft in einer MySQL‑Datenbank speichert. Das Projekt demonstriert praxisnah den Aufbau eines vollständigen Web‑Stacks aus mehreren Containern, inklusive persistenter Datenhaltung und Monitoring.

---

## 2. Aufbau & logische Struktur des Projekts
Das Projekt besteht aus fünf Hauptkomponenten, die über **Docker Compose** orchestriert werden:

### **Frontend (Nginx)**
- Statischer Webserver für HTML, CSS und JavaScript
- Läuft unter `localhost:8080`
- Kommuniziert mit dem Backend per Fetch‑Requests

### **Backend (Node.js / Express)**
- API‑Server mit dem Endpoint `POST /score`
- Speichert Name + erreichte Punkte in der MySQL‑Datenbank
- Läuft unter `localhost:3000`

### **MySQL-Datenbank**
- Speichert alle Highscores dauerhaft
- Kommuniziert intern unter dem Hostnamen `db`
- Volume: `db_data:/var/lib/mysql`

### **Adminer**
- Browserbasierte Datenbankverwaltung
- Erreichbar unter `localhost:8081`

### **cAdvisor (Monitoring)**
- Zeigt CPU‑, RAM‑, I/O‑ und Netzwerkverbrauch aller Container
- Erreichbar unter `localhost:8082`

### **Architekturübersicht**
```
Browser → Frontend (Nginx :8080)
              ↓ fetch()
        Backend API (Node :3000)
              ↓ SQL
          MySQL DB (:3306)
              │
         Adminer (:8081)
              │
      cAdvisor Monitoring (:8082)
```

---

## 3. Dienst konfigurieren & Monitoring einsetzen
Alle Services sind in der Datei **docker-compose.yml** definiert. Wichtige Umgebungsvariablen wie `DB_HOST`, `DB_USER`, `DB_PASSWORD` und `DB_NAME` steuern die Backend‑Datenbankverbindung.

### **Monitoring (cAdvisor)**
Ich habe cAdvisor nachträglich ergänzt, da ich beim ersten Aufbau des Projekts das Monitoring vergessen hatte. Der Dienst wurde vollständig integriert und funktioniert nun korrekt.

```yaml
cadvisor:
  image: gcr.io/cadvisor/cadvisor:latest
  container_name: cadvisor
  ports:
    - "8082:8080"
  volumes:
    - /:/rootfs:ro
    - /var/run:/var/run:ro
    - /sys:/sys:ro
    - /var/lib/docker/:/var/lib/docker:ro
  restart: unless-stopped
```

Aufruf im Browser: **http://localhost:8082**

![alt text](<Fotos-Projekt/Screenshot 2026-02-25 085343.png>)

---

## 4. Netzwerkverbindungen & Ports
Die Netzwerkverbindungen zwischen Host und Containern sind wie folgt konfiguriert:

| Dienst      | Hostport → Containerport | Zweck |
|-------------|---------------------------|--------|
| Frontend    | 8080 → 80                | Spiel / Weboberfläche |
| Backend     | 3000 → 3000              | API‑Requests |
| MySQL       | 3306 → 3306              | Datenbankzugriff |
| Adminer     | 8081 → 8080              | Datenbank‑UI |
| cAdvisor    | 8082 → 8080              | Monitoring‑Dashboard |

Interne Kommunikation erfolgt über Docker‑DNS:
- **Backend → MySQL:** `db:3306`
- **Frontend → Backend:** `http://localhost:3000`

---

## 5. Interaktion Hostsystem ↔ Container (Volumes)
Persistente Datenhaltung wird über ein Named Volume realisiert:

```yaml
volumes:
  db_data:
```

MySQL verwendet dieses Volume für sein Datenverzeichnis:
```yaml
volumes:
  - db_data:/var/lib/mysql
```

### **Nachweis der Persistenz**
- Daten bleiben auch nach `docker compose down` erhalten
- Adminer zeigt gespeicherte Highscores
- Im Docker Dashboard ist das Volume sichtbar

---

## 6. Fehler & deren Behebung
### Fehler: Monitoring‑Tool (cAdvisor) wurde vergessen
Während der ersten Version des Projekts wurde das Monitoring nicht implementiert. Dadurch fehlte eine wichtige Anforderung der Handlungsziele.

### Lösung:
- cAdvisor wurde nachträglich korrekt in die `docker-compose.yml` integriert
- Ports und Host‑Volumes wurden ergänzt
- Funktion wurde getestet und unter `localhost:8082` erfolgreich bestätigt

Damit ist das Monitoring jetzt vollständig dokumentiert und funktionsfähig.

---

## 7. Ergänzende Hinweise / Kontext
- Das Game speichert für jede Runde Name + Score
- Das Backend stellt ausschliesslich API‑Routen bereit → daher zeigt `localhost:3000` „Cannot GET /“ (korrekt!)
- Adminer dient zur Einsicht in die Datenbank
- cAdvisor liefert Live‑Monitoring aller Container
- Das Projekt ist ideal geeignet, um Web‑Stack‑Architektur mit Containern zu demonstrieren

---

## 8. Fazit
Die **Docker Battle Arena** zeigt ein vollständiges, modernes Web‑Setup und demonstriert klar, wie mehrere Container zusammenarbeiten, um ein komplettes System zu bilden.