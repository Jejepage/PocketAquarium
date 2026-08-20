# App-Entwicklungs-Workflow mit Coding-Agenten

Diese Vorlage unterstützt einen Solo-Entwickler dabei, eine kleine iOS-, macOS- oder Web-App schrittweise von der Idee bis zur Veröffentlichung zu entwickeln. Sie ist für Codex ausgelegt und hält Planung, Implementierung, unabhängige Prüfung, persönliche Freigabe und GitHub-Dokumentation nachvollziehbar zusammen.

Die vollständige Prozessbeschreibung steht in `APP-ENTWICKLUNGS-WORKFLOW.md`.

## Arbeitsweise

Der Workflow führt ein Projekt durch diese Abschnitte:

1. Idee und Problemvalidierung
2. Produktbeschreibung / PRD
3. Funktions- und UI-Plan
4. technischer Plan
5. Implementierungsplan mit drei bis sechs Etappen
6. Umsetzung, unabhängige Prüfung, Korrektur und persönliche Abnahme jeder Etappe
7. Release und Veröffentlichung

Es wird immer nur die aktuelle Phase beziehungsweise eine Umsetzungsetappe bearbeitet. `STATUS.md` hält den verbindlichen Arbeitsstand fest. `AGENTS.md` liest diesen Stand und verweist auf die passende Rollendatei unter `agents/`.

## Neues App-Projekt starten

1. Kopiere die Workflow-Dateien in das Stammverzeichnis eines neuen Projektordners oder erstelle daraus ein eigenes Vorlagen-Repository.
2. Richte für das App-Projekt ein GitHub-Repository ein.
3. Setze den Betriebsmodus in `STATUS.md` von `Workflow-Vorlage` auf `App-Projekt`.
4. Trage Projektname, Zielplattform und Repository in `STATUS.md` ein.
5. Beschreibe dem Agenten die ursprüngliche App-Idee oder Aufgabenstellung.
6. Starte Codex aus dem Projektstamm mit einem neuen Lauf, damit die dortige `AGENTS.md` geladen wird.
7. Verwende anschließend als kurzen Folgeauftrag:

   ```text
   Arbeite gemäß AGENTS.md und dem aktuellen Projektstatus weiter.
   ```

Ein App-Projekt bleibt absichtlich in der Phase `Nicht initialisiert`, bis eine echte Idee oder Aufgabenbeschreibung vorliegt. Solange der Betriebsmodus `Workflow-Vorlage` gesetzt ist, pflegt Codex nur die Vorlage und startet keine App-Phase.

## Zentrale Dateien

| Datei oder Ordner | Zweck |
|---|---|
| `APP-ENTWICKLUNGS-WORKFLOW.md` | vollständiger Prozess und gemeinsame Qualitätsregeln |
| `AGENTS.md` | automatisch geladene Startregeln und Phasen-Routing |
| `STATUS.md` | aktueller Auftrag, Entscheidungen, Prüfungen, Blocker und Übergabe |
| `agents/` | phasenspezifische Rollen und Arbeitsanweisungen |
| `docs/` | freigegebene Produkt-, Technik- und Etappendokumente |
| `templates/` | wiederverwendbare Ausgangsstrukturen für Projektdokumente |
| `GITHUB-ABSCHLUSSPROTOKOLL.md` | verbindlicher Commit-, Push-, Integrations- und Übergabeablauf |

## GitHub-Regel

Jede freigegebene Planungsphase, jede vollständig abgenommene Umsetzungsetappe und die Release-Phase erhalten einen eigenen nachvollziehbaren GitHub-Stand. Das gilt auch, wenn nur Dokumentation oder Entscheidungen entstanden sind.

Mindestens erforderlich sind:

- aktuelles fachliches Ergebnis und `STATUS.md`
- aussagekräftiger Commit
- erfolgreicher Push zu GitHub
- dokumentierter Branch und GitHub-Stand

Ein Pull Request ist für kleine Solo-Projekte empfohlen, aber nicht verpflichtend. Eine Phase oder Etappe gilt erst als abgeschlossen, wenn ihr verpflichtender Stand auf GitHub verfügbar ist.

Der genaue Ablauf einschließlich Ergebnis-Commit, Abschlussdokumentation und Remote-Prüfung steht in `GITHUB-ABSCHLUSSPROTOKOLL.md`.

## Persönliche Freigaben

Der Entwickler entscheidet nach jeder Planungsphase und jeder geprüften Umsetzungsetappe, ob das Ergebnis akzeptiert wird. Erst danach erfolgen GitHub-Abschluss und Übergang zum nächsten Abschnitt.

## Lizenz

Dieser Workflow steht unter der MIT-Lizenz. Einzelheiten enthält `LICENSE`.
