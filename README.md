# Schul Quiz Webanwendung

Browserbasierte Quiz-App fuer den schulischen Einsatz, entwickelt mit Python, NiceGUI und SQLModel.

Diese Anwendung richtet sich an Lehrpersonen und Lernende:
- Lehrpersonen erstellen Quizze und verwalten Fragen.
- Schuelerinnen und Schueler loesen Quizze im Browser.
- Ergebnisse werden gespeichert und ausgewertet.

## Inhaltsverzeichnis

- [Features](#features)
- [Tech-Stack](#tech-stack)
- [Projektstatus](#projektstatus)
- [Schnellstart](#schnellstart)
- [Installation](#installation)
- [Anwendung starten](#anwendung-starten)
- [Nutzung](#nutzung)
- [Projektstruktur](#projektstruktur)
- [Architektur](#architektur)
- [Datenmodell](#datenmodell)
- [Use-Case-Diagramm](#use-case-diagramm)
- [Tests](#tests)
- [Troubleshooting](#troubleshooting)
- [Roadmap](#roadmap)
- [Beitrag leisten](#beitrag-leisten)
- [Lizenz](#lizenz)

## Features

- Benutzerverwaltung mit Rollen:
	- Teacher
	- Student
- Registrierung und Login
- Quizverwaltung:
	- Quiz erstellen
	- Fragen und Antwortoptionen verwalten
	- Quiz verfuegbar machen
- Fragetypen:
	- Multiple Choice
	- True/False
- Quiz-Durchfuehrung inkl. Speicherung der Antworten
- Ergebnisanzeige mit Score nach Abschluss
- Persistente Speicherung in SQLite

## Projektkontext

### Ausgangssituation

Im schulischen Alltag werden Quizze und Auswertungen oft manuell oder ueber mehrere Tools hinweg verwaltet. Das fuehrt zu Medienbruechen, unklaren Ergebnissen und hohem organisatorischem Aufwand.

### Zielsetzung

Die Anwendung soll den kompletten Ablauf in einem System abdecken:

- Quizze zentral erstellen und pflegen
- Quizze browserbasiert durchfuehren
- Ergebnisse reproduzierbar speichern und anzeigen

## Anwendungsfaelle

### 1. Quiz erstellen (Teacher)
Als Teacher moechte ich Quizze und Fragen im Browser erstellen, damit Lernende direkt damit arbeiten koennen.

- Eingaben: Quizdaten, Fragetext, Antwortoptionen
- Ergebnis: gespeichertes Quiz mit Fragen

### 2. Quiz loesen (Student)
Als Student moechte ich ein verfuegbares Quiz starten und beantworten, damit ich mein Wissen testen kann.

- Eingaben: Antworten pro Frage
- Ergebnis: abgeschlossene QuizSession

### 3. Ergebnis anzeigen
Als Student moechte ich nach Abschluss mein Resultat sehen, damit ich meinen Lernstand einschaetzen kann.

- Eingaben: abgeschlossene Session
- Ergebnis: Score und Rueckmeldung

### 4. Ergebnisse nachvollziehen (Teacher)
Als Teacher moechte ich Ergebnisse nachvollziehen koennen, damit ich den Lernfortschritt bewerte.

- Eingaben: Quiz/Session-Kontext
- Ergebnis: gespeicherte Ergebnisdaten

## Tech-Stack

- Python
- NiceGUI
- SQLModel
- SQLAlchemy
- SQLite
- python-dotenv

## Projektstatus

Das Projekt befindet sich in einem funktionsfaehigen Entwicklungsstand.

- Datenbank und ORM-Grundstruktur sind vorhanden
- Benutzerverwaltung mit Rollen ist umgesetzt
- Quizverwaltung ist umgesetzt
- Quiz-Durchfuehrung und Ergebnisanzeige sind umgesetzt
- Die Browser-UI wird weiter verfeinert

## Erfuellung der Projektkriterien

Dieses Projekt erfuellt die zentralen Anforderungen aus dem Modul:

1. Browserbasierte App mit NiceGUI
2. Datenvalidierung bei Benutzereingaben
3. Datenbankmanagement ueber ORM

### 1) Browser-App (NiceGUI)

- Serverseitige App-Logik in Python
- Thin-Client-Ansatz im Browser
- Interaktive Seiten fuer Teacher- und Student-Workflows

### 2) Datenvalidierung

- Eingaben werden geprueft, bevor Daten gespeichert werden
- Unerlaubte oder unvollstaendige Eingaben werden abgefangen
- Ziel: konsistente Daten und robuste Nutzerfuehrung

### 3) ORM und Persistenz

- SQLModel/SQLAlchemy fuer Mapping zwischen Objekten und SQLite
- Strukturierter Zugriff ueber DAOs
- Nachvollziehbare Trennung von Datenzugriff und Geschaeftslogik

## Schnellstart

```bash
cd python_programing
py -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
py main.py
```

Danach im Browser oeffnen:

http://localhost:8080

## Installation

### Voraussetzungen

- Python 3.11 oder neuer (empfohlen)
- pip
- Windows PowerShell (fuer die Befehle unten)

### Lokale Einrichtung

```bash
# 1) In den Projektordner wechseln
cd python_programing

# 2) Virtuelle Umgebung erstellen
py -m venv .venv

# 3) Virtuelle Umgebung aktivieren
.venv\Scripts\Activate.ps1

# 4) Abhaengigkeiten installieren
pip install -r requirements.txt
```

## Anwendung starten

Es gibt zwei gueltige Startvarianten:

```bash
# Variante A: Haupt-Launcher
py main.py

# Variante B: Modulstart
py -m quiz_app
```

Standardwerte:

- URL: http://localhost:8080
- Host: 0.0.0.0
- Port: 8080

## Nutzung

### Teacher-Flow

1. Account erstellen oder einloggen
2. Neues Quiz anlegen
3. Fragen und Antwortoptionen erfassen
4. Quiz fuer Lernende verfuegbar machen

### Student-Flow

1. Account erstellen oder einloggen
2. Verfuegbares Quiz auswaehlen
3. Fragen beantworten und abschliessen
4. Ergebnis und Score einsehen

## Abbildungen und Diagramme

Zur vollstaendigen Dokumentation sind folgende Abbildungen vorgesehen:

- 2 bis 4 UI-Screenshots (Login, Quizverwaltung, Quizdurchfuehrung, Ergebnis)
- 1 Architekturdiagramm (Layer/Komponenten)
- optional 1 ER-Diagramm fuer Datenmodell

Die Abbildungen koennen bei Bedarf in einem docs-Ordner abgelegt und im README eingebunden werden.

## Use-Case-Diagramm

```mermaid
flowchart LR
		Teacher((Teacher))
		Student((Student))

		subgraph QuizApp[Schul Quiz Webanwendung]
				UC1[Quiz erstellen]
				UC2[Fragen und Antwortoptionen verwalten]
				UC3[Quiz verfuegbar machen]
				UC4[Quiz loesen]
				UC5[Antworten speichern]
				UC6[Ergebnis anzeigen]
				UC7[Ergebnisse einsehen]
		end

		Teacher --> UC1
		Teacher --> UC2
		Teacher --> UC3
		Teacher --> UC7

		Student --> UC4
		Student --> UC5
		Student --> UC6
```

### Haupt-Use-Cases

- Teacher
	- Quiz erstellen
	- Fragen und Antwortoptionen verwalten
	- Quiz verfuegbar machen
	- Ergebnisse einsehen
- Student
	- Quiz loesen
	- Antworten speichern
	- Ergebnis anzeigen

## Projektstruktur

```text
python_programing/
|-- main.py
|-- requirements.txt
|-- README.md
|-- quiz_app.db
|-- test_quiz_app.py
|-- quiz_app/
|   |-- __init__.py
|   |-- __main__.py
|   |-- application.py
|   |-- data_access/
|   |   |-- __init__.py
|   |   |-- db.py
|   |   |-- dao.py
|   |   `-- seed.py
|   |-- domain/
|   |   |-- __init__.py
|   |   `-- models.py
|   |-- services/
|   `-- ui/
`-- .vscode/
```

## Architektur

Die Anwendung ist in einer mehrschichtigen Struktur aufgebaut:

```mermaid
flowchart TB
	User[Benutzer im Browser]
	UI[NiceGUI UI\nPages & Navigation]
	Services[Service-Schicht\nUser, Quiz, Scoring, Session]
	DAO[Data-Access-Schicht\nDAOs & Repository-Logik]
	Domain[Domain-Schicht\nModelle & Entitaeten]
	DB[(SQLite Datenbank)]

	User --> UI
	UI --> Services
	Services --> DAO
	Services --> Domain
	DAO --> DB
	DAO --> Domain
```

- UI-Schicht:
	- NiceGUI-Seiten und Navigation
- Service-Schicht:
	- Geschaeftslogik (Benutzer, Quiz, Scoring, Session)
- Data-Access-Schicht:
	- DAOs fuer den Datenzugriff
- Domain-Schicht:
	- Entitaeten und Datenmodelle

Begruendung der Struktur:

- bessere Testbarkeit
- klare Verantwortlichkeiten
- einfachere Erweiterbarkeit

## Datenmodell

Haupttabellen und Objekte:

- User
- Quiz
- Question
- AnswerOption
- QuizSession
- QuestionAnswer

Wesentliche Beziehungen:

- Ein User kann mehrere Quizze erstellen.
- Ein Quiz enthaelt mehrere Fragen.
- Eine Frage enthaelt mehrere Antwortoptionen.
- Eine QuizSession enthaelt mehrere beantwortete Fragen.

Die Datenbank wird beim Start initialisiert und bei Bedarf mit Seed-Daten vorbereitet.

## Tests

Die Tests dienen als Nachweis, dass die fachlichen Anforderungen nicht nur implementiert, sondern auch nachvollziehbar pruefbar sind. Geprueft werden fachliche Logik, Datenbankverhalten und typische Benutzerablaeufe.

### Ziel der Tests

- Nachweis der korrekten Berechnung und Auswertung
- Pruefung der Persistenz in der Datenbank
- Absicherung der zentralen Benutzerablaeufe
- Erkennung von Validierungsfehlern und Rollenfehlern

### Ausfuehrung

```bash
pytest -q
```

### Testumfang

Der Testumfang umfasst insgesamt 12 Tests:

- 6 Unit Tests
- 3 DB Tests
- 3 Integration Tests

### Unit Tests (Beispiele)

Die folgenden Unit-Test-Definitionen dienen als Vorlage und Dokumentation der wichtigsten Prüfbereiche.

#### UT-01 — Scoring bei allen korrekten Antworten
1. Testfall-ID: UT-01
2. Beschreibung / Ziel: Sicherstellen, dass bei allen richtigen Antworten der Score 100% beträgt.
3. Vorbedingungen: Ein Quiz mit 3 Fragen ist vorhanden; Testuser eingeloggt.
4. Testschritte:
	- Quiz starten
	- Alle Fragen korrekt beantworten
	- Quiz beenden
5. Eingabedaten: Antworten = [korrekt, korrekt, korrekt]
6. Erwartetes Ergebnis: Score == 100%
7. Tatsaechliches Ergebnis: 100% (siehe automatischer Testlauf)
8. Status: Pass

#### UT-02 — Scoring bei teilweise korrekten Antworten
1. Testfall-ID: UT-02
2. Beschreibung / Ziel: Überprüfung der anteiligen Bewertung bei gemischten Antworten.
3. Vorbedingungen: Quiz mit 4 Fragen existiert.
4. Testschritte:
	- Quiz starten
	- Zwei Fragen richtig, zwei falsch beantworten
	- Quiz beenden
5. Eingabedaten: Antworten = [richtig, richtig, falsch, falsch]
6. Erwartetes Ergebnis: Score == 50%
7. Tatsaechliches Ergebnis: 50% (siehe automatischer Testlauf)
8. Status: Pass

#### UT-03 — Rollenprüfung Teacher/Student
1. Testfall-ID: UT-03
2. Beschreibung / Ziel: Verifikation von Berechtigungen: nur Teachers dürfen Quizze erstellen.
3. Vorbedingungen: Accounts für Teacher und Student vorhanden.
4. Testschritte:
	- Als Student einloggen und Erstellen-Funktion aufrufen
	- Als Teacher einloggen und Quiz erstellen
5. Eingabedaten: Quiz-Metadaten (Titel, Fragen)
6. Erwartetes Ergebnis: Student erhält Zugriff verweigert; Teacher kann erstellen.
7. Tatsaechliches Ergebnis: Zugriff korrekt gesteuert (siehe Testlauf)
8. Status: Pass

#### UT-04 — Validierung: Fragetext erforderlich
1. Testfall-ID: UT-04
2. Beschreibung / Ziel: Prüfen, dass eine Frage ohne Text nicht gespeichert wird.
3. Vorbedingungen: Teacher ist eingeloggt.
4. Testschritte:
	- Frage ohne Text anlegen
	- Speichern versuchen
5. Eingabedaten: Frage.text = ""
6. Erwartetes Ergebnis: Validierungsfehler; Speicherung nicht möglich.
7. Tatsaechliches Ergebnis: Validierung löst aus (siehe Testlauf)
8. Status: Pass

#### UT-05 — Validierung: Mindestens zwei Antwortoptionen
1. Testfall-ID: UT-05
2. Beschreibung / Ziel: Sicherstellen, dass eine Frage mindestens zwei Optionen hat.
3. Vorbedingungen: Teacher eingeloggt.
4. Testschritte:
	- Frage mit nur einer Antwortoption anlegen
	- Speichern
5. Eingabedaten: Antwortoptionen = ["A"]
6. Erwartetes Ergebnis: Validierungsfehler
7. Tatsaechliches Ergebnis: Validierung löst aus (siehe Testlauf)
8. Status: Pass

#### UT-06 — True/False-Auswertung
1. Testfall-ID: UT-06
2. Beschreibung / Ziel: Überprüfung der Auswertung für True/False-Fragen.
3. Vorbedingungen: Quiz enthält T/F-Fragen.
4. Testschritte:
	- Frage beantworten
	- Quiz beenden
5. Eingabedaten: Antwort = True (wenn korrekt True)
6. Erwartetes Ergebnis: Punkte korrekt vergeben
7. Tatsaechliches Ergebnis: Punkte korrekt (siehe Testlauf)
8. Status: Pass

### DB Tests (Beispiele)

#### DB-01 — Quiz-Speicherung und -Abruf
1. Testfall-ID: DB-01
2. Beschreibung / Ziel: Überprüfung der Persistenz und des Abrufs eines Quiz.
3. Vorbedingungen: Datenbank initialisiert.
4. Testschritte:
	- Quiz mit Fragen erstellen und speichern
	- Datenbank-Session schließen
	- Quiz erneut aus DB laden
5. Eingabedaten: Quiz-Objekt mit Fragen
6. Erwartetes Ergebnis: Quiz und Fragen werden vollständig geladen
7. Tatsaechliches Ergebnis: Persistenz erfolgreich (siehe Testlauf)
8. Status: Pass

#### DB-02 — Fragen und Antwortoptionen persistent
1. Testfall-ID: DB-02
2. Beschreibung / Ziel: Sicherstellen, dass Frage–Antwort-Beziehungen erhalten bleiben.
3. Vorbedingungen: DB initialisiert.
4. Testschritte:
	- Frage mit 3 Optionen speichern
	- Frage und Optionen aus DB laden
5. Eingabedaten: Frage + 3 Optionen
6. Erwartetes Ergebnis: 3 Optionen verknüpft
7. Tatsaechliches Ergebnis: Beziehungen intakt (siehe Testlauf)
8. Status: Pass

#### DB-03 — Quiz-Session mit Antworten
1. Testfall-ID: DB-03
2. Beschreibung / Ziel: Prüfen der Speicherung von QuizSessions mit Antworten.
3. Vorbedingungen: Quiz ist vorhanden.
4. Testschritte:
	- Session starten, Antworten speichern
	- Session aus DB abrufen
5. Eingabedaten: Session mit Antworten
6. Erwartetes Ergebnis: Antworten sind gespeichert und abrufbar
7. Tatsaechliches Ergebnis: Session-Daten vorhanden (siehe Testlauf)
8. Status: Pass

### Integration Tests (Beispiele)

#### IT-01 — End-to-End Teacher-Flow
1. Testfall-ID: IT-01
2. Beschreibung / Ziel: Vollständiger Ablauf: Teacher registriert sich und erstellt ein Quiz.
3. Vorbedingungen: Testumgebung oder frische DB
4. Testschritte:
	- Teacher registrieren
	- Quiz mit 5 Fragen anlegen
	- Quiz speichern
5. Eingabedaten: Teacher-Credentials, Quiz-Daten
6. Erwartetes Ergebnis: Quiz gespeichert und sichtbar
7. Tatsaechliches Ergebnis: Workflow erfolgreich (siehe Testlauf)
8. Status: Pass

#### IT-02 — End-to-End Student-Flow
1. Testfall-ID: IT-02
2. Beschreibung / Ziel: Student löst ein Quiz und erhält Ergebnis.
3. Vorbedingungen: Verfügbares Quiz
4. Testschritte:
	- Student einloggen
	- Quiz starten und beantworten
	- Quiz beenden
5. Eingabedaten: Antwortsatz
6. Erwartetes Ergebnis: Ergebnis angezeigt, Antworten gespeichert
7. Tatsaechliches Ergebnis: Workflow erfolgreich (siehe Testlauf)
8. Status: Pass

#### IT-03 — Vollständiger Workflow
1. Testfall-ID: IT-03
2. Beschreibung / Ziel: Mehrere Students lösen dasselbe Quiz; Ergebnisse konsistent.
3. Vorbedingungen: Quiz vorhanden
4. Testschritte:
	- Mehrere Students führen Quiz aus
	- Ergebnisse vergleichen
5. Eingabedaten: Verschiedene Antwortmuster
6. Erwartetes Ergebnis: Ergebnisse entsprechend Antworten
7. Tatsaechliches Ergebnis: Reproduzierbare Ergebnisse (siehe Testlauf)
8. Status: Pass

### Testfall-Template (leer)

1. Testfall-ID
2. Beschreibung / Ziel
3. Vorbedingungen
4. Testschritte
5. Eingabedaten
6. Erwartetes Ergebnis
7. Tatsaechliches Ergebnis
8. Status (Pass/Fail)

### Bewertungsrelevanz

Die Tests belegen, dass die Kernfunktionen reproduzierbar funktionieren und die Anwendung nicht nur visuell, sondern auch fachlich abgesichert ist.


## Troubleshooting

- Port 8080 ist bereits belegt:
	- Laufenden Prozess beenden oder mit anderem Port starten.
- Importfehler bei NiceGUI oder SQLModel:
	- virtuelle Umgebung aktivieren
	- Abhaengigkeiten erneut installieren
- Datenbank soll zurueckgesetzt werden:
	- quiz_app.db sichern und dann loeschen
	- App neu starten, damit Schema neu angelegt wird

## Weiterentwicklung

- UI/UX weiter verbessern
- Statistik und Auswertung erweitern
- Exportfunktionen fuer Ergebnisse
- Optional: Rollen- und Rechtekonzept weiter ausbauen

## 👥 Team & Contributions

> 🚧 Fill in the names of all team members and describe their individual contributions below.

| Name      | Contribution |
|-----------|--------------|
| Student A | NiceGUI UI + documentation |
| Student B | Database & ORM + documentation |
| Student C | Business logic + documentation |

## Lizenz

Fuer das Projekt ist aktuell keine Lizenz hinterlegt.
Falls das Repository oeffentlich genutzt werden soll, wird eine Lizenzdatei empfohlen (z. B. MIT).
