# 📚 Vollständige und Ausführliche Zusammenfassung: Backup & Restore Lernziele

---

## 1. RAID-Level (RAID 0, 1, 4, 5, 6, 10, 01)

**RAID (Redundant Array of Independent Disks)** dient der Steigerung von Ausfallsicherheit, Leistung oder beidem durch Kombination mehrerer physischer Festplatten.

| RAID | Beschreibung | Vorteile | Nachteile |
|------|--------------|----------|-----------|
| RAID 0 | Striping ohne Redundanz – Daten werden blockweise auf mehrere Platten verteilt. | Höchste Performance bei Lesen/Schreiben | Kein Schutz bei Ausfall – komplette Datenverluste |
| RAID 1 | Spiegelung – Daten werden auf zwei Festplatten gleichzeitig geschrieben. | Hohe Ausfallsicherheit, einfache Wiederherstellung | Nur 50 % des Speicherplatzes nutzbar |
| RAID 4 | Striping mit dedizierter Paritätsplatte | Gute Leseleistung, einfache Paritätskontrolle | Paritätsplatte ist Flaschenhals |
| RAID 5 | Striping mit verteilter Parität | Effiziente Nutzung von Kapazität, gute Leseleistung | Komplexe Wiederherstellung, keine Toleranz bei 2 Plattenausfällen |
| RAID 6 | Wie RAID 5, aber zwei Paritätsblöcke | Ausfallsicherheit bei zwei gleichzeitigen Fehlern | Noch komplexere Berechnung, geringere Schreibgeschwindigkeit |
| RAID 10 | Kombination aus RAID 1 + 0 (Mirroring + Striping) | Hohe Performance und Ausfallsicherheit | Hoher Speicherbedarf |
| RAID 01 | Kombination aus RAID 0 + 1 (Striping + Mirroring) | Gute Performance | Weniger robust als RAID 10 bei mehreren Ausfällen |

---

## 2. USV-Anlagen (Offline- und Online-USV)

- **Offline-USV (Standby-USV):**
  - Erkennt Stromausfall und schaltet auf Batterie um.
  - Geeignet für unkritische Systeme mit kurzer Umschaltzeit (<10 ms).
  - Vorteile: günstig, effizient
  - Nachteile: kleine Unterbrechung beim Umschalten möglich

- **Online-USV (Dauerbetrieb über Wechselrichter):**
  - Strom läuft ständig durch Batterie – keine Umschaltzeit.
  - Geeignet für Server, Rechenzentren, kritische Infrastruktur.
  - Vorteile: unterbrechungsfrei, sauberer Strom
  - Nachteile: teuer, höherer Energiebedarf

---

## 3. Zu sichernde Daten

Folgende Datenarten sollten regelmäßig gesichert werden:

- **Betriebssysteme und Programme** – Für schnelle Wiederherstellung im Notfall
- **Systemkonfigurationen** – Netzwerk, Benutzerrechte, Dienste
- **Datenbanken** – Geschäftsdaten, Kundendaten, ERP-Systeme
- **Benutzerdaten** – Eigene Dateien, Projektverzeichnisse
- **E-Mails, Dokumente, Verträge** – Rechtlich und operativ notwendig
- **Protokolle und Logdateien** – Für Analyse, Nachvollziehbarkeit

---

## 4. Sicherungsmodalitäten

| Sicherungstyp | Beschreibung | Vorteil | Nachteil |
|---------------|--------------|---------|----------|
| **Vollbackup** | Komplettes Abbild aller Daten | Einfache Wiederherstellung | Hoher Speicher- & Zeitbedarf |
| **Differenziell** | Seit letzter Vollsicherung geänderte Daten | Schneller als Vollbackup, weniger Speicher | Langsamere Restore-Zeit als Vollbackup |
| **Inkrementell** | Seit letzter Sicherung geänderte Daten | Sehr platzsparend | Restore dauert am längsten |

- Kombination empfohlen: z. B. sonntags Vollbackup, werktags inkrementell

**Generationenkonzept:**
- Großvater (monatlich), Vater (wöchentlich), Sohn (täglich)
- Sicherung wird rollierend ersetzt – schützt vor Datenverlust durch mehrere Wiederherstellungspunkte

---

## 5. Mehrstufiges Backupkonzept

Ein sicheres Konzept besteht aus:

1. **Backup-Zeitplan**: täglich inkrementell, wöchentlich voll, monatlich archivieren
2. **Speicherorte**: 
   - Lokal: Schnell verfügbar, z. B. NAS
   - Extern: Brandschutz, z. B. Bankschließfach
   - Cloud: Geo-redundant
3. **Medienarten**:
   - Festplatten, Bänder, Cloudspeicher
4. **Zugriffsregelung**:
   - Nur autorisierte Personen
   - Verschlüsselung bei Transport/Speicherung
5. **Automatisierung**: Zeitgesteuerte Backups mit Logs
6. **Monitoring und Test**: Protokolle prüfen, regelmäßige Restore-Tests

---

## 6. Aufbewahrung von Datenträgern

### Anforderungen:
- **Sicher vor**: Hitze, Feuchtigkeit, Magnetismus, unbefugtem Zugriff
- **Aufbewahrung nach DSGVO/GoBD**:
  - Geschäftsdaten: 6–10 Jahre
  - Personal-/Steuerdaten: mind. 10 Jahre
- **Ort**: Feuerschränke, klimatisierte Räume
- **Medienpflege**: Datenträger regelmäßig überprüfen, evtl. migrieren

---

## 7. Rollen und Verantwortlichkeiten

### Backup-Administrator
- Implementierung, Wartung, Durchführung, Kontrolle
- Restore-Test und Fehlerbehebung

### Systemverantwortliche
- Legen fest, was gesichert wird
- Prüfen Datenkonsistenz, melden Änderungen

### Management
- Budgetfreigabe, Strategie, Richtlinien
- Verantwortung für Risikomanagement und Governance

### Auditoren/Revision
- Überprüfung auf Rechtssicherheit, DSGVO, GoBD
- Kontrolle der Backup-Dokumentation

---

## 8. Notfallhandbuch

Enthält:
- **Kontaktlisten** (IT, Management, Externe)
- **Notfallablaufpläne**
- **Wiederanlaufstrategien**
- **Kommunikationspläne**
- **Checklisten für Wiederherstellung**
- **Systemübersichten** mit IPs, Zugangsdaten, Backuproutinen
- **Testprotokolle & Änderungsverfolgung**

---

## 9. Test Backup/Restore-Konzept

- **Regelmäßige Restore-Tests** mit ausgewählten Daten
- Prüfung von:
  - Dauer der Wiederherstellung
  - Vollständigkeit und Integrität
- **Dokumentation**:
  - Testergebnisse
  - Fehleranalyse
- **Ziel**: Sicherstellung, dass Restore im Notfall möglich ist

---

## 10. Linux `tar`-Befehl

### Archivieren:
```bash
tar -cvf backup.tar /pfad/zur/datei
