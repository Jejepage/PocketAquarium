# Agentenanweisungen für App-Projekte

Diese Datei steuert sowohl die Pflege der Workflow-Vorlage als auch App-Projekte, die den in `APP-ENTWICKLUNGS-WORKFLOW.md` beschriebenen Prozess verwenden. Im Modus `App-Projekt` ist sie der zentrale Router. Sie enthält nur gemeinsame Regeln und verweist für die konkrete Aufgabe auf genau eine Rollendatei unter `agents/`.

## Verbindlicher Start

Führe vor jeder fachlichen Arbeit diese Schritte aus:

1. Lies `STATUS.md` vollständig.
2. Erfasse Betriebsmodus, aktuelle Phase, Status, Auftrag, Eingangsdokumente, Blocker und nächsten Schritt.
3. Im Betriebsmodus `Workflow-Vorlage` bearbeitest du ausschließlich die Vorlage gemäß dem konkreten Auftrag des Entwicklers. Starte keine App-Phase und wende die GitHub-Abschlusspflicht für zukünftige App-Etappen nicht auf einzelne Schritte der Vorlagenentwicklung an.
4. Im Betriebsmodus `App-Projekt` und mit der aktuellen Phase `Nicht initialisiert` beginnst du keine Planung oder Implementierung. Bitte den Entwickler um die ursprüngliche Idee beziehungsweise Aufgabenbeschreibung und initialisiere anschließend `STATUS.md` mit der Phase `Idee und Problemvalidierung`.
5. Bestimme im Betriebsmodus `App-Projekt` für jede andere Phase anhand der Routingtabelle genau eine Rollendatei.
6. Lies die gewählte Rollendatei vollständig.
7. Prüfe, ob alle dort verlangten Eingangsdokumente vorhanden und freigegeben sind.
8. Lies die erforderlichen Eingangsdokumente vollständig und prüfe sie auf offensichtliche Lücken oder Widersprüche.
9. Aktualisiere `STATUS.md` auf `In Bearbeitung`, bevor du mit der Aufgabe beginnst.

Die Schritte 5 bis 9 und das nachfolgende Routing gelten nur im Betriebsmodus `App-Projekt`. Fehlt dort eine Rollendatei oder eine notwendige, freigegebene Eingabe, arbeite nicht mit stillschweigenden Annahmen weiter. Setze den Status auf `Blockiert`, dokumentiere den konkreten Grund und benenne die benötigte Entscheidung oder Datei.

## Routing

| Aktuelle Phase in `STATUS.md` | Rollendatei |
|---|---|
| Idee und Problemvalidierung | `agents/01-idea-validation.md` |
| Produktbeschreibung / PRD | `agents/02-product-requirements.md` |
| Funktions- und UI-Plan | `agents/03-functional-ui-plan.md` |
| Technischer Plan | `agents/04-technical-plan.md` |
| Implementierungsplan | `agents/05-implementation-plan.md` |
| Implementierung – Etappe N | `agents/06-implementation.md` |
| Prüfung – Etappe N | `agents/07-review-and-testing.md` |
| Korrektur – Etappe N | `agents/06-implementation.md` |
| Release | `agents/08-release.md` |

`N` und eine optionale Kurzbezeichnung werden in `STATUS.md` durch die konkrete Etappe ersetzt. Die Zuordnung richtet sich weiterhin nach dem Präfix der Phase.

## Gemeinsame Arbeitsregeln

- Bearbeite nur die aktuelle Phase beziehungsweise genau eine Umsetzungsetappe.
- Halte den Umfang der freigegebenen ersten Version klein.
- Schwäche Akzeptanzkriterien nicht eigenmächtig ab.
- Trenne Implementierung und unabhängige Prüfung entsprechend dem Workflow.
- Bevorzuge die einfachste Lösung, die die freigegebenen Anforderungen zuverlässig erfüllt.
- Dokumentiere neue Erkenntnisse, Abweichungen, Risiken und Planänderungen ausdrücklich.
- Erfinde keine erfolgreich ausgeführten Builds, Tests, Prüfungen oder GitHub-Aktionen.
- Beachte Datenschutz, Sicherheit, Barrierefreiheit und Plattformvorgaben nur soweit sie für das konkrete Projekt relevant sind.
- Hole die vorgesehene persönliche Freigabe des Entwicklers ein, bevor du zur nächsten Phase oder Etappe wechselst.
- Verwende beim erstmaligen Erstellen einer Ergebnisdatei die passende Struktur unter `templates/docs/`, sofern vorhanden. Die Rollendatei bleibt maßgeblich; Vorlagen ersetzen keine Prüfung oder Freigabe.

## Abschluss und Übergabe

Nach der Arbeit:

1. Aktualisiere Ergebnis, offene Punkte, Entscheidungen, Prüfungen und Übergabehinweise in `STATUS.md`.
2. Setze einen eindeutigen Status aus der dort aufgeführten Liste.
3. Benenne die nächste Phase oder Aufgabe und ihre erforderlichen Eingaben.
4. Führe nach der abschließenden Freigabe den in `GITHUB-ABSCHLUSSPROTOKOLL.md` konkretisierten GitHub-Abschluss durch.
5. Markiere eine Phase oder Etappe erst als `Abgeschlossen`, wenn ihr verpflichtender GitHub-Stand erfolgreich verfügbar ist.

Die Rollendatei darf diese gemeinsamen Regeln konkretisieren, aber nicht abschwächen.
