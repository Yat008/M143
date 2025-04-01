# 📚 Detaillierte Zusammenfassung: Backup & Restore Lernziele

---

## 1. RAID-Level (S. 50–51, Kapitel 8)

| RAID-Level | Funktionsweise | Vorteile | Nachteile |
|------------|----------------|----------|-----------|
| RAID 0     | Striping ohne Parität | Höchste Leistung | Keine Redundanz |
| RAID 1     | Spiegelung (Mirroring) | Ausfallsicherheit | Speicherplatz halbiert |
| RAID 4     | Striping mit dedizierter Paritätsplatte | Gute Lesegeschwindigkeit | Paritätsdisk = Flaschenhals |
| RAID 5     | Striping mit verteilter Parität | Gute Performance, Redundanz | Kein Schutz bei 2 Plattenausfällen |
| RAID 6     | Wie RAID 5 + doppelte Parität | Zwei Plattenausfälle möglich | Langsamere Schreibgeschwindigkeit |
| RAID 10    | Mirroring + Striping (1+0) | Hohe Geschwindigkeit + Redundanz | Hoher Speicherbedarf |
| RAID 01    | Striping + Mirroring (0+1) | Gute Performance | Weniger robust bei Mehrfachausfall |

---

## 2. USV-Typen (S. 52)

| Typ | Merkmale | Vorteile | Nachteile |
|-----|----------|----------|-----------|
| Offline-USV | Stromversorgung direkt, schaltet bei Ausfall um | Preiswert | Kurze Umschaltzeit kann kritisch sein |
| Online-USV  | Dauerbetrieb über Batterie/Wechselrichter | Keine Umschaltzeit | Höherer Preis & Stromverbrauch |

---

## 3. Zu sichernde Daten (S. 58)

- System- und Konfigurationsdaten
- Anwendungen & Betriebssysteme
- Benutzer- & Geschäftsdaten
- Kundendaten, Verträge, E-Mails, Datenbanken
- Alles Relevante für Geschäftsfortführung

---

## 4. Sicherungsmodalitäten (S. 62–63)

| Art | Beschreibung | Speicher | Restore-Aufwand |
|-----|--------------|----------|------------------|
| Vollsicherung | Alles wird gesichert | Hoch | Gering |
| Differenzielle Sicherung | Änderungen seit letzter Vollsicherung | Mittel | Mittel |
| Inkrementelle Sicherung | Änderungen seit letzter Sicherung (egal welcher) | Gering | Hoch |

- **Generationenkonzept**: Großvater – Vater – Sohn

---

## 5. Mehrstufiges Backupkonzept (S. 64–66)

- Kombiniert verschiedene Sicherungsarten
- Zeitpläne: täglich, wöchentlich, monatlich
- Speicherorte: lokal, extern, Cloud
- Wiederherstellungstests
- Zugriffsschutz und Verschlüsselung

---

## 6. Aufbewahrung von Datenträgern (S. 72–74)

- Schutz vor Wasser, Feuer, Magnetismus
- Sichere Lagerung (Tresor, Klima)
- Gekennzeichnete Datenträger
- Einhaltung gesetzlicher Fristen (6–10 Jahre)
- Regelmäßige Prüfung der Lesbarkeit

---


---

## 🧑‍🏫 Detaillierte Rollenbeschreibung im Backup/Restore-Konzept (S.76)

### 🔧 1. Backup-Administrator / IT-Verantwortlicher
- Plant und implementiert das Backup- und Wiederherstellungskonzept
- Wählt geeignete Backup-Software und -Hardware aus
- Richtet Zeitpläne für Sicherungen ein (z. B. Vollsicherung jeden Sonntag, inkrementell Mo–Sa)
- Überprüft regelmäßig Protokolle und Meldungen auf Fehler
- Führt Test-Restores durch, um die Wiederherstellbarkeit zu gewährleisten
- Dokumentiert alle Vorgänge und Änderungen im Backup-System
- Setzt Maßnahmen bei Fehlern oder Sicherheitsverletzungen um

### 🧩 2. System- oder Fachverantwortliche
- Legen fest, welche Daten/Ordner/Applikationen kritisch und daher zu sichern sind
- Kooperieren mit dem Backup-Admin zur Definition von Backup-Prioritäten
- Prüfen nach Wiederherstellungen, ob die Daten vollständig und korrekt sind
- Melden Veränderungen im Datenbestand, die Auswirkungen auf das Backup haben

### 💼 3. Management / Geschäftsleitung
- Verantwortlich für strategische Entscheidungen rund um Backup & Restore
- Genehmigt das Budget für Speichermedien, Software, Personal, Cloudlösungen etc.
- Legt Sicherheitsstandards und Notfallverfahren fest
- Muss im Schadensfall gegenüber Aufsichtsbehörden und Versicherungen Rechenschaft ablegen
- Fördert Schulungen und Sensibilisierung der Mitarbeiter

### 🔍 4. Auditoren / Revision / Datenschutzbeauftragte
- Überwachen die Einhaltung von rechtlichen Vorgaben (z. B. DSGVO, GoBD)
- Prüfen, ob Backup-Zyklen und Aufbewahrungsfristen eingehalten werden
- Kontrollieren Zugriffsrechte auf Backupdaten und Wiederherstellungen
- Führen Audits durch (intern/extern) und dokumentieren Ergebnisse
- Machen Verbesserungsvorschläge aus organisatorischer Sicht


| Rolle | Aufgaben |
|-------|----------|
| Backup-Admin | Umsetzung, Überwachung, Tests |
| Systemverantwortliche | Auswahl der zu sichernden Daten |
| Management | Ressourcenbereitstellung, Strategie |
| Auditor / Revision | Prüfung auf Regelkonformität |

---

## 8. Notfallhandbuch (S. 81–88)

- Notfallkontakte
- Recovery- und Kommunikationsplan
- Zuständigkeiten
- Checklisten & Ablaufbeschreibungen
- Dokumentation aller Systeme

---

## 9. Backup/Restore testen (S. 89–91)

- Regelmäßige Restore-Tests
- Prüfung auf Performance & Datenintegrität
- Testprotokolle & Auswertungen
- Optimierung der Backupstrategie

---

## 10. Linux `tar`-Befehl (Aufgabe 12.6)

- Archiv erstellen: `tar -cvf backup.tar /pfad`
- Entpacken: `tar -xvf backup.tar`
- Gzip verwenden: `tar -czvf backup.tar.gz /pfad`

| Schalter | Bedeutung |
|----------|-----------|
| -c | create |
| -x | extract |
| -v | verbose |
| -f | file |
| -z | gzip-Kompression |

---

## 11. Robocopy & Archivbit (Aufgaben 12.3 & 12.4)

- `robocopy Quelle Ziel /A /E` → nur Dateien mit Archivbit
- `robocopy Quelle Ziel /M /S` → mit Rücksetzen des Archivbits

| Schalter | Funktion |
|----------|----------|
| /A | Nur mit gesetztem Archivbit |
| /M | Mit Rücksetzen des Archivbits |
| /E | Alle Unterverzeichnisse inkl. leerer |
| /S | Alle Unterverzeichnisse außer leerer |

- **Archivbit** zeigt an, ob Datei verändert wurde seit letzter Sicherung

