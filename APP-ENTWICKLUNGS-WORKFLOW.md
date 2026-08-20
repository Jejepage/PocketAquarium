# Workflow zur Entwicklung kleiner Apps mit Coding-Agenten

## Zweck

Dieser Workflow begleitet einen Solo-Entwickler von der ersten Idee bis zur fertigen App. Er ist für kleinere iOS-Apps, macOS-Anwendungen und Webapplikationen gedacht.

Der Prozess soll ausreichend Struktur und Qualität schaffen, ohne die Entwicklung durch unnötige Dokumentation oder komplexe Unternehmensprozesse zu verlangsamen.

## Grundprinzipien

- Jede Phase hat ein klares Ergebnis in Form einer Markdown-Datei.
- Der folgende Agent arbeitet mit dem freigegebenen Ergebnis der vorherigen Phase.
- `STATUS.md` ist die zentrale Übergabedatei und wird von jedem Agenten gelesen und aktualisiert.
- Jeder Agent prüft vor Arbeitsbeginn, ob die erforderlichen Ausgangsdokumente der vorherigen Phase vorhanden und freigegeben sind.
- Der Umfang der ersten Version bleibt bewusst klein.
- Implementierung und Prüfung werden voneinander getrennt.
- Nach jeder Etappe entscheidet der Entwickler selbst, ob das Ergebnis akzeptiert wird.
- Dokumentation wird nur erstellt, wenn sie für Planung, Umsetzung oder spätere Wartung nützlich ist.
- Erkenntnisse aus späteren Phasen dürfen frühere Pläne verändern. Änderungen werden jedoch ausdrücklich dokumentiert.
- Jede abgeschlossene Phase und jede Implementierungsetappe eines App-Projekts wird auf GitHub gesichert, auch wenn ausschließlich Dokumente oder Entscheidungen entstanden sind.

## Verbindlicher GitHub-Abschluss für zukünftige App-Projekte

Dieser Abschnitt gilt für App-Projekte, die mit diesem Workflow entwickelt werden. Der wiederverwendbare Workflow selbst kann zunächst vollständig lokal ausgearbeitet und nach seiner Fertigstellung einmalig auf GitHub veröffentlicht werden.

Die Phasen 1 bis 5, jede vollständige Umsetzungsetappe sowie die Release-Phase erhalten einen eigenen nachvollziehbaren GitHub-Abschluss. Eine Umsetzungsetappe umfasst Implementierung, unabhängige Prüfung, notwendige Korrekturen und persönliche Abnahme. Eine Phase oder Etappe ohne Code ist von der GitHub-Pflicht nicht ausgenommen. Ihr Ergebnis besteht beispielsweise aus einem freigegebenen Plan, einer dokumentierten Entscheidung, einem Prüfbericht oder einer aktualisierten Statusdatei.

Innerhalb einer Umsetzungsetappe dürfen beliebig viele sinnvolle Zwischenstände committed und gepusht werden. Der verbindliche Etappenabschluss erfolgt jedoch einmal nach Abschluss des gesamten Prüf- und Korrekturzyklus.

Für den GitHub-Abschluss sind mindestens erforderlich:

1. Das fachliche Ergebnis liegt in der vorgesehenen Markdown-Datei beziehungsweise im Quellcode vor.
2. `STATUS.md` enthält Ergebnis, wichtige Entscheidungen, ausgeführte Prüfungen, bekannte Probleme und den nächsten Schritt.
3. Die zusammengehörigen Änderungen werden mit einer aussagekräftigen Commit-Nachricht committed.
4. Der Commit wird zu GitHub gepusht.
5. Branch und aktueller GitHub-Stand werden in `STATUS.md` dokumentiert.

Für jede Phase oder Etappe sollte ein eigener, kurz benannter Branch verwendet werden, beispielsweise `phase/01-idea-validation`, `stage/02-main-flow` oder `release/1.0.0`. Ein Pull Request mit Zusammenfassung, Prüfnachweisen und offenen Punkten ist empfohlen, aber für ein allein entwickeltes kleines Projekt nicht zwingend. Wird ein Pull Request verwendet, wird seine URL ebenfalls in `STATUS.md` vermerkt.

Der GitHub-Abschluss erfolgt nach der fachlichen Prüfung und Freigabe durch den Entwickler. Eine Phase oder Etappe darf erst als `Abgeschlossen` gelten, wenn der zugehörige Commit erfolgreich auf GitHub verfügbar ist. Schlägt der Push fehl, wird der Abschnitt nicht abgeschlossen; der Grund wird in `STATUS.md` als Blocker festgehalten.

Der genaue, für Agenten ausführbare Ablauf steht in `GITHUB-ABSCHLUSSPROTOKOLL.md`. Er trennt den fachlichen Ergebnis-Commit von der abschließenden Status- und Übergabedokumentation, prüft den Remote-Stand und verhindert dadurch eine nicht auflösbare Selbstreferenz auf die Commit-ID der eigenen Statusänderung.

## Verbindliches Startprotokoll für jeden Agenten

`AGENTS.md` dient als automatischer Router. Da Codex diese Datei beim Start einliest, muss der Startprompt keine Rollendatei nennen. Jeder neu gestartete Agent führt vor seiner eigentlichen Aufgabe diese Schritte in der angegebenen Reihenfolge aus:

1. `STATUS.md` lesen.
2. Die dort angegebene aktuelle Phase, den Status, die nächste Aufgabe und offene Probleme erfassen.
3. Anhand der Zuordnungstabelle in `AGENTS.md` automatisch die passende Rollendatei unter `agents/` bestimmen.
4. Diese Rollendatei vollständig lesen.
5. Prüfen, ob die dort genannten Eingangsdokumente vorhanden sind.
6. Prüfen, ob diese Dokumente als freigegeben beziehungsweise abgeschlossen gekennzeichnet sind.
7. Die Dokumente vollständig lesen und auf offensichtliche Widersprüche oder fehlende Angaben prüfen.
8. In `STATUS.md` vermerken, dass die Arbeit begonnen wurde.
9. Erst danach mit der eigentlichen Aufgabe beginnen.

Fehlt ein notwendiges Dokument, ist es nicht freigegeben oder widerspricht es einem anderen verbindlichen Dokument, darf der Agent nicht stillschweigend Annahmen treffen und weiterarbeiten. Er hält den Blocker in `STATUS.md` fest und meldet konkret, welches Dokument oder welche Entscheidung benötigt wird.

Nach Abschluss seiner Arbeit muss jeder Agent:

1. sein Ergebnis und die ausgeführten Prüfungen in `STATUS.md` eintragen,
2. neu entstandene Probleme oder Planänderungen dokumentieren,
3. den Status der bearbeiteten Phase aktualisieren,
4. die nächste Aufgabe und deren benötigte Eingangsdokumente benennen und
5. das Übergabedatum aktualisieren und
6. festhalten, ob der aktuelle Arbeitsabschnitt für den GitHub-Abschluss bereit ist; nach der abschließenden Freigabe führt der zuständige Agent den GitHub-Abschluss durch oder dokumentiert einen dabei entstandenen Blocker.

## Erforderliche Eingangsdokumente

| Phase | Erforderliche Eingaben |
|---|---|
| Idee und Problemvalidierung | ursprüngliche Idee oder Aufgabenbeschreibung |
| Produktbeschreibung / PRD | freigegebene `docs/idea-validation.md` |
| Funktions- und UI-Plan | freigegebene `docs/product-requirements.md` |
| Technischer Plan | freigegebene `docs/product-requirements.md` und `docs/functional-plan.md` |
| Implementierungsplan | freigegebene `docs/product-requirements.md`, `docs/functional-plan.md` und `docs/technical-plan.md` |
| Implementierung einer Etappe | freigegebene Planungsdokumente und Beschreibung der betreffenden Etappe |
| Prüfung einer Etappe | freigegebene Etappenbeschreibung, Akzeptanzkriterien und abgeschlossene Implementierungsübergabe |
| Release | abgeschlossene Etappen, bestandene Prüfungen und aktuelle Release-Anforderungen |

`STATUS.md` zeigt den Arbeitsstand an, ersetzt aber keines dieser fachlichen Ausgangsdokumente.

## Automatische Auswahl der Agentenrolle

Die aktuelle Phase in `STATUS.md` muss einem festgelegten Wert folgen. `AGENTS.md` ordnet diesen Wert einer Rollendatei zu:

| Aktuelle Phase | Rollendatei |
|---|---|
| Nicht initialisiert | keine; Initialisierung gemäß `AGENTS.md` |
| Idee und Problemvalidierung | `agents/01-idea-validation.md` |
| Produktbeschreibung / PRD | `agents/02-product-requirements.md` |
| Funktions- und UI-Plan | `agents/03-functional-ui-plan.md` |
| Technischer Plan | `agents/04-technical-plan.md` |
| Implementierungsplan | `agents/05-implementation-plan.md` |
| Implementierung – Etappe N | `agents/06-implementation.md` |
| Prüfung – Etappe N | `agents/07-review-and-testing.md` |
| Korrektur – Etappe N | `agents/06-implementation.md` |
| Release | `agents/08-release.md` |

Der vorherige Agent trägt beim Abschluss bereits die nächste Phase in `STATUS.md` ein. Dadurch findet der nachfolgende Agent ohne zusätzlichen Rollenhinweis die richtige Anweisung.

Ein normaler Startprompt kann deshalb kurz bleiben:

```text
Arbeite gemäß AGENTS.md und dem aktuellen Projektstatus weiter.
```

## Gesamtprozess

```text
Idee
  ↓
1. Idee und Problemvalidierung
  ↓
Freigabe durch den Entwickler
  ↓
2. Produktbeschreibung / PRD
  ↓
3. Funktions- und UI-Plan
  ↓
4. Technischer Plan
  ↓
5. Implementierungsplan mit 3–6 Etappen
  ↓
┌────────────────────────────────────┐
│ 6. Etappe implementieren           │
│              ↓                     │
│ 7. Unabhängig prüfen               │
│              ↓                     │
│ Fehler korrigieren und neu prüfen  │
│              ↓                     │
│ Persönliche Abnahme                │
└────────────────────────────────────┘
  ↓ nächste Etappe
8. Release und Veröffentlichung
```

Der zur besseren Lesbarkeit nicht wiederholt dargestellte GitHub-Abschluss findet nach jeder freigegebenen Planungsphase und nach jeder vollständig geprüften, korrigierten und persönlich abgenommenen Umsetzungsetappe statt.

## 1. Agent für Idee und Problemvalidierung

### Aufgabe

Der Agent entwickelt eine zunächst grobe Idee gemeinsam mit dem Entwickler weiter und prüft sie kritisch. Eine Validierung durch externe Personen ist nicht erforderlich. Es handelt sich um eine strukturierte Selbstprüfung.

Der Agent klärt:

- Welches konkrete Problem soll die App lösen?
- Wer soll die App verwenden?
- In welcher Situation wird sie verwendet?
- Welchen wesentlichen Nutzen bietet sie?
- Wie wird das Problem bisher gelöst?
- Ist eine eigene App dafür sinnvoll?
- Ist die Idee als kleines Projekt realistisch?
- Was ist die kleinstmögliche nützliche Version?
- Welche Annahmen und offenen Fragen bestehen?
- Welche Funktionen sind wahrscheinlich unnötig?

### Ergebnis

`docs/idea-validation.md`

Das Dokument enthält mindestens:

- Ausgangsidee
- Problem
- Zielgruppe
- Nutzungssituation
- zentraler Nutzen
- kleinstmögliche sinnvolle Version
- Annahmen und offene Fragen
- Risiken oder technische Unsicherheiten
- Empfehlung: weiterführen, verändern oder verwerfen

### Freigabe

Der Entwickler entscheidet, ob die Idee weitergeführt, verändert oder verworfen wird. Erst nach dieser Entscheidung beginnt die Produktbeschreibung.

## 2. Agent für Produktbeschreibung / PRD

### Aufgabe

Dieser Agent verwandelt die freigegebene Idee in eine verbindliche, kompakte Produktbeschreibung. Er entscheidet noch nicht über die technische Umsetzung.

Der Agent beschreibt:

- Produktvision
- Zielgruppe
- Hauptanwendungsfall
- wichtigste Benutzerbedürfnisse
- Funktionen der ersten Version
- optionale spätere Funktionen
- bewusste Nicht-Ziele
- grundlegende Qualitätsanforderungen
- Erfolgskriterien
- noch offene Produktentscheidungen

Die erste Version sollte möglichst nur drei bis fünf Kernfunktionen enthalten. Das PRD soll für kleine Apps kompakt bleiben.

### Ergebnis

`docs/product-requirements.md`

### Freigabe

Der Entwickler bestätigt insbesondere:

- Die erste Version löst das beschriebene Kernproblem.
- Der Umfang ist klein und realistisch.
- Die Nicht-Ziele sind eindeutig.
- Es fehlen keine unverzichtbaren Funktionen.

## 3. Agent für Funktions- und UI-Plan

### Aufgabe

Der Agent übersetzt die Produktbeschreibung in konkretes, beobachtbares Verhalten der App. Funktionsplanung und einfache UI-Planung werden für kleine Projekte in einem Dokument zusammengefasst.

Der Plan beschreibt:

- Ansichten oder Seiten
- Navigation
- wichtigste Benutzerabläufe
- Funktionen jeder Ansicht
- Eingaben und Ausgaben
- Daten, die angezeigt oder verändert werden
- Lade-, Leer-, Fehler- und Erfolgszustände
- benötigte Berechtigungen
- grundlegende Bedienbarkeit und Barrierefreiheit
- Akzeptanzkriterien für jede Kernfunktion

Einfache Text-Wireframes können ergänzt werden, wenn sie das Verhalten verständlicher machen.

### Ergebnis

`docs/functional-plan.md`

### Freigabe

Der Entwickler prüft, ob alle wichtigen Abläufe verständlich, vollständig und möglichst einfach sind.

## 4. Agent für den technischen Plan

### Aufgabe

Der Agent bestimmt die notwendige technische Grundlage. Er soll die einfachste Architektur wählen, die die Anforderungen zuverlässig erfüllt.

Der Plan umfasst nur relevante Punkte:

- Zielplattform: iOS, macOS oder Web
- Programmiersprache, Framework und minimale Systemversion
- grundlegende Projekt- und Modulstruktur
- Datenmodell
- lokale oder entfernte Speicherung
- externe APIs und Dienste
- Anmeldung, Synchronisation oder Käufe, sofern erforderlich
- Berechtigungen
- Fehlerbehandlung
- Datenschutz und grundlegende Sicherheit
- Teststrategie
- Build- und Veröffentlichungsweg

Nicht benötigte Abstraktionen, Dienste und Infrastruktur sollen ausdrücklich vermieden werden.

### Ergebnis

`docs/technical-plan.md`

### Freigabe

Der Entwickler bestätigt Technologieauswahl, externe Abhängigkeiten, laufende Kosten und wesentliche technische Einschränkungen.

## 5. Agent für den Implementierungsplan

### Aufgabe

Der Agent zerlegt das Projekt in drei bis sechs überschaubare Etappen. Jede Etappe soll ein sichtbares, überprüfbares Ergebnis liefern.

Beispiel:

1. Projektgrundlage und Navigation
2. wichtigster vollständiger Benutzerablauf
3. Speicherung und Bearbeitung
4. ergänzende Funktionen und Einstellungen
5. Feinschliff und Veröffentlichung

Eine Etappe enthält:

- Ziel und sichtbares Ergebnis
- enthaltene Anforderungen
- konkrete Aufgaben
- Akzeptanzkriterien
- erforderliche automatisierte und manuelle Tests
- Abhängigkeiten
- klare Abschlussbedingungen

Technische Schichten sollen nicht unnötig getrennt werden. Ein kleiner vollständiger Benutzerablauf ist meist besser als getrennte Etappen für die gesamte Datenbank, das gesamte Backend und die gesamte Oberfläche.

### Ergebnisse

- `docs/implementation-plan.md`
- eine Datei pro Implementierungsetappe unter `docs/stages/`

Die jeweilige Etappendatei enthält zunächst Ziel, Umfang, Akzeptanzkriterien und Tests. Nach dem vollständigen Implementierungs-, Prüfungs- und Korrekturzyklus wird sie um Ergebnis, Abweichungen, Prüfnachweise und den GitHub-Abschluss ergänzt. Dadurch bleibt auch eine Etappe ohne Code als eigenständiger Projektstand nachvollziehbar.

### Freigabe

Der Entwickler bestätigt Reihenfolge, Umfang, Abhängigkeiten, Akzeptanzkriterien und vorgesehenen Prüfumfang aller Etappen. Erst nach dieser Freigabe und dem GitHub-Abschluss der Planungsphase beginnt die erste Umsetzungsetappe.

## 6. Implementierungs-Agent für eine Etappe

### Aufgabe

Der Implementierungs-Agent setzt genau eine freigegebene Etappe um.

Er muss:

- die relevanten Projekt- und Planungsdateien lesen
- vorhandenen Code und bestehende Konventionen berücksichtigen
- nur den vereinbarten Umfang implementieren
- angemessene automatisierte Tests ergänzen
- Build, Tests und statische Prüfungen ausführen
- unnötige Komplexität vermeiden
- Abweichungen oder neue Erkenntnisse dokumentieren
- `STATUS.md` bei Beginn und Abschluss der Arbeit aktualisieren

Der Agent darf Akzeptanzkriterien nicht eigenmächtig abschwächen. Falls der Plan technisch problematisch oder widersprüchlich ist, meldet er dies und schlägt eine konkrete Planänderung vor.

### Ergebnis

- funktionierender Code für die Etappe
- passende Tests
- erfolgreicher Build, soweit lokal möglich
- aktualisierter Projektstatus
- überschaubare, nachvollziehbare Änderungen

## 7. Unabhängiger Prüf-Agent

### Aufgabe

Ein anderer Agent prüft die abgeschlossene Etappe. Er arbeitet möglichst aus den Anforderungen, Akzeptanzkriterien und tatsächlichen Änderungen heraus und übernimmt nicht ungeprüft die Begründungen des Implementierungs-Agenten.

Er prüft:

- Lässt sich das Projekt bauen?
- Bestehen die automatisierten Tests?
- Sind alle Akzeptanzkriterien erfüllt?
- Funktioniert der tatsächliche Benutzerablauf?
- Wurden wichtige Fehler- und Randfälle berücksichtigt?
- Entstanden Regressionen?
- Wurde unnötige Komplexität eingebaut?
- Stimmen Implementierung und Dokumentation überein?
- Gibt es offensichtliche Datenschutz- oder Sicherheitsprobleme?

Bei UI-Änderungen soll der Agent die App nach Möglichkeit im Simulator, in einer Vorschau oder im Browser prüfen.

### Ergebnis

Der Prüf-Agent liefert entweder:

- **Bestanden**, mit kurzer Begründung und ausgeführten Prüfungen, oder
- **Nicht bestanden**, mit einer priorisierten Liste konkreter Probleme und nachvollziehbaren Schritten zur Reproduktion.

### Korrekturschleife

1. Der Implementierungs-Agent korrigiert bestätigte Probleme.
2. Der Prüf-Agent prüft die Korrekturen und die betroffenen Regressionen erneut.
3. Die Schleife endet, wenn keine relevanten Probleme mehr offen sind.

### Persönliche Abnahme

Nach bestandener technischer Prüfung testet der Entwickler den wichtigsten Ablauf selbst. Dabei stehen Bediengefühl, Verständlichkeit und Übereinstimmung mit der ursprünglichen Idee im Mittelpunkt.

Erst danach gilt die Etappe als abgeschlossen.

## 8. Release und Veröffentlichung

Nach Abschluss aller Etappen folgt eine kurze Release-Prüfung:

- vollständiger Build und Testlauf
- Prüfung auf relevanten Geräten, Simulatoren, Browsern oder Fenstergrößen
- App-Name, Icon, Texte und Versionsnummer
- Datenschutzangaben und benötigte Berechtigungen
- Produktionskonfiguration und Geheimnisse
- bekannte Einschränkungen
- Release-Build
- Veröffentlichung oder Deployment
- kurze Prüfung der veröffentlichten Version

### Ergebnis

Für jede Version entsteht eine Release-Datei unter `docs/releases/`, beispielsweise `docs/releases/1.0.0.md`. Sie dokumentiert Release-Bereitschaft, Build- und Testnachweise, persönliche Freigabe, Veröffentlichung, Prüfung der veröffentlichten Version und den abschließenden GitHub-Stand. Auch ein nicht veröffentlichter oder blockierter Release bleibt dadurch nachvollziehbar.

## Empfohlene Projektstruktur

```text
AGENTS.md
README.md
STATUS.md
GITHUB-ABSCHLUSSPROTOKOLL.md
agents/
  01-idea-validation.md
  02-product-requirements.md
  03-functional-ui-plan.md
  04-technical-plan.md
  05-implementation-plan.md
  06-implementation.md
  07-review-and-testing.md
  08-release.md
docs/
  idea-validation.md
  product-requirements.md
  functional-plan.md
  technical-plan.md
  implementation-plan.md
  stages/                 # eine Datei pro Implementierungsetappe
  releases/               # eine Datei pro vorbereiteter oder veröffentlichter Version
templates/
  README.md
  docs/                   # Ausgangsstrukturen für alle Projektdokumente
```

## Inhalt von `STATUS.md`

Die Statusdatei liegt im Projektstamm, ist die erste Anlaufstelle für jeden neuen Agenten und wird bei jedem relevanten Arbeitsübergang aktualisiert:

```markdown
# Projektstatus

## Betriebsmodus

App-Projekt

## Aktuelle Phase

Implementierung – Etappe 2: Hauptfunktion

## Status

In Bearbeitung

## Zuletzt aktualisiert

YYYY-MM-DD HH:MM – Implementierungs-Agent

## Aktueller Auftrag

Eingabeformular und lokale Speicherung umsetzen.

## Erforderliche Eingangsdokumente

- [x] docs/product-requirements.md
- [x] docs/functional-plan.md
- [x] docs/technical-plan.md
- [x] docs/implementation-plan.md
- [x] Beschreibung und Akzeptanzkriterien für Etappe 2

## Erledigt

- Navigation
- Eingabeformular
- lokale Speicherung

## Offen

- Fehlermeldung bei ungültiger Eingabe

## Bekannte Probleme

- Layout auf kleinen Displays prüfen

## Wichtige Entscheidungen oder Planänderungen

- Keine

## Ausgeführte Prüfungen

- Build erfolgreich
- automatisierte Tests erfolgreich

## GitHub-Stand

- Branch: stage/02-main-flow
- Letzter Push: Noch nicht erfolgt
- Etappenabschluss auf GitHub: Noch ausstehend
- Pull Request: Nicht verwendet

## Nächster Schritt

Prüf-Agent prüft Etappe 2 anhand der Akzeptanzkriterien.

## Übergabehinweise für den nächsten Agenten

- Besonders den Fehlerzustand bei ungültiger Eingabe prüfen.
```

Zulässige Statuswerte sind möglichst eindeutig zu verwenden:

- `Nicht begonnen`
- `In Bearbeitung`
- `Blockiert`
- `Bereit zur Prüfung`
- `In Prüfung`
- `Korrektur erforderlich`
- `Bereit zur persönlichen Abnahme`
- `Bereit zum GitHub-Abschluss`
- `Abgeschlossen`

## Definition of Done für eine Phase oder Etappe

Eine Phase oder Etappe ist abgeschlossen, wenn:

- alle vereinbarten Aufgaben erledigt und alle anwendbaren Akzeptanzkriterien erfüllt sind
- das vorgesehene fachliche Ergebnis dokumentiert ist, auch wenn kein Code entstanden ist
- alle für den Abschnitt relevanten Prüfungen bestanden oder nicht anwendbare Prüfungen begründet wurden
- bei Codeänderungen das Projekt erfolgreich gebaut werden kann und relevante automatisierte Tests bestehen
- bei Implementierungsetappen der Prüf-Agent keine relevanten offenen Probleme meldet
- Dokumentation, Etappendatei und `STATUS.md` aktuell sind
- der Entwickler das Ergebnis beziehungsweise den sichtbaren Ablauf akzeptiert hat
- die zusammengehörigen Änderungen committed und erfolgreich zu GitHub gepusht wurden
- ein verwendeter Pull Request und sein Ergebnis in `STATUS.md` vermerkt sind

## Bewusst nicht Teil dieses Workflows

Für kleine, allein entwickelte Apps sind normalerweise nicht erforderlich:

- externe Marktvalidierung
- Projektmanagement-Agent
- umfangreiche Architekturhandbücher
- formelle Risiko-Workshops
- getrennte Security-, UX- und QA-Abteilungen
- aufwendige Freigabeprozesse
- komplexe Unternehmens-CI/CD-Infrastruktur

Wenn ein konkretes Projekt höhere Anforderungen hat, können zusätzliche Prüfungen gezielt ergänzt werden. Der Workflow soll jedoch standardmäßig einfach bleiben.
