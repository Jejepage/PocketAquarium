# Verbindliches GitHub-Abschlussprotokoll

Dieses Protokoll konkretisiert den GitHub-Abschluss aus `APP-ENTWICKLUNGS-WORKFLOW.md`. Es gilt nur im Betriebsmodus `App-Projekt`: nach jeder freigegebenen Planungsphase, nach jeder vollständig geprüften und persönlich abgenommenen Implementierungsetappe sowie nach dem Release.

## Ziel

Der freigegebene Ergebnisstand, seine Prüfnachweise und die Übergabe an den nächsten Abschnitt müssen gemeinsam auf GitHub nachvollziehbar sein. Das gilt unverändert für Abschnitte ohne Code.

Ergebnis-Commit und nachfolgende Abschlussdokumentation bilden zusammen genau einen verpflichtenden Phasen-, Etappen- oder Release-Abschluss. Sie dürfen technisch zwei oder, bei einer Pull-Request-Integration, mehrere Commits und Pushes benötigen.

## Voraussetzungen

Der Abschluss darf erst beginnen, wenn:

- das vorgesehene Ergebnis und alle anwendbaren Prüfungen vollständig dokumentiert sind,
- keine relevanten Befunde oder ungeklärten Blocker offen sind,
- der Entwickler die Phase, Etappe oder den Release persönlich freigegeben hat,
- `STATUS.md` auf `Bereit zum GitHub-Abschluss` steht,
- Branch, Zielbranch, Remote und die projektspezifische Integrationsstrategie eindeutig sind.

Fehlt eine Voraussetzung, wird nicht committed oder gepusht. Der Grund bleibt in `STATUS.md` sichtbar.

## Sicherheits- und Umfangsregeln

- Erfasse ausschließlich Dateien des aktuellen Abschnitts. Übernimm keine unbeteiligten lokalen Änderungen.
- Prüfe den vollständigen Diff und die Staging-Auswahl vor jedem Commit.
- Übertrage keine Geheimnisse, Zugangsdaten, personenbezogenen Testdaten, lokalen Buildprodukte oder unnötig große Artefakte.
- Verwende aussagekräftige Commits. Eine Etappe ohne Code erhält einen Dokumentations- oder Entscheidungs-Commit und keinen leeren Platzhalter-Commit.
- Verwende keinen Force-Push und schreibe keine veröffentlichte Historie um, sofern der Entwickler dies nicht ausdrücklich für den konkreten Fall freigibt.
- Schließe erforderliche Branch-Schutzregeln, Prüfungen und Freigaben nicht aus oder umgehe sie nicht.

## Ablauf

### 1. Abschlussumfang prüfen

1. Lies `STATUS.md`, die aktuelle Ergebnisdatei beziehungsweise Etappendatei und die zugehörigen Änderungen.
2. Prüfe aktuellen Branch, Upstream, Remote, Arbeitsbaum und bereits vorhandene unbeteiligte Änderungen.
3. Führe mindestens eine Diff-Prüfung auf Format- oder Whitespacefehler sowie die für den Abschnitt vorgesehenen fachlichen Prüfungen aus.
4. Halte in `STATUS.md` fest, welche Dateien und Nachweise zum Abschluss gehören.

### 2. Ergebnis-Commit erstellen

1. Stage nur die ausdrücklich zum Abschnitt gehörenden Pfade.
2. Prüfe den gestagten Diff vollständig.
3. Erstelle einen fachlichen Ergebnis-Commit, zum Beispiel:
   - `docs(phase-02): approve product requirements`
   - `feat(stage-03): add local item editing`
   - `docs(stage-04): record accessibility audit`
   - `release: prepare 1.0.0`
4. Pushe den Branch und prüfe, ob der Ergebnis-Commit auf GitHub verfügbar ist.

### 3. Integration nach Projektstrategie

- Wird ein Pull Request verwendet, enthält er Ergebnis, ausgeführte Prüfungen, bekannte Einschränkungen und offene optionale Hinweise. Der Abschluss ist erst nach den erforderlichen Prüfungen und erfolgreicher Integration beendet.
- Wird kein Pull Request verwendet, integriere den freigegebenen Branch gemäß der im technischen Plan dokumentierten Strategie und pushe den vorgesehenen Zielbranch.
- Ein nur lokal vorhandener Merge oder ein nur lokal vorhandener Commit genügt nicht.
- Schlägt Push, Prüfung oder Integration fehl, setze `STATUS.md` auf `Blockiert` und dokumentiere die genaue Ursache. Wechsle nicht zur nächsten Phase oder Etappe.

### 4. Abschluss und Übergabe dokumentieren

Aktualisiere `STATUS.md` mindestens mit den folgenden Angaben. Bei einer Planungsphase wird zusätzlich der Freigabe- und GitHub-Status in der Ergebnisdatei aktualisiert. Etappen- und Release-Dateien erhalten die vollständigen Angaben in ihrem Abschnitt `GitHub-Abschluss`.

| Feld | Inhalt |
|---|---|
| Abschnitt | Phase, Etappe oder Release mit Nummer und Name |
| Persönliche Freigabe | Datum, Ergebnis und freigebende Person |
| Ergebnis-Commit | vollständige oder eindeutig verkürzte Commit-ID |
| Branch und Zielbranch | Quell- und Integrationsbranch |
| Push und Integration | Zeitpunkt und bestätigtes Ergebnis |
| Pull Request | URL und Ergebnis oder `Nicht verwendet` |
| Prüfungen | tatsächlich ausgeführte Abschlussprüfungen |
| Bekannte Einschränkungen | akzeptierte Einschränkungen oder `Keine` |
| Nächster Abschnitt | genaue Phase beziehungsweise Etappe und benötigte Eingaben |

Setze den aktuellen Abschnitt erst jetzt auf `Abgeschlossen`. Committe diese Status- und Übergabeaktualisierung als kleinen Abschluss-Commit und pushe sie ebenfalls. Prüfe abschließend, dass auch dieser Dokumentationsstand auf GitHub verfügbar ist.

Der Abschluss-Commit kann seine eigene Commit-ID nicht in seinem Inhalt dokumentieren. Als stabiler fachlicher Bezug wird deshalb der vorherige Ergebnis- beziehungsweise Integrations-Commit in `STATUS.md` festgehalten; Branch, Push-Ergebnis und gegebenenfalls Pull Request belegen den nachfolgenden Abschluss-Commit.

### 5. Übergang freigeben

Erst nach erfolgreicher Remote-Prüfung:

1. bestätige `Abgeschlossen` in `STATUS.md`,
2. starte vom integrierten und auf GitHub verfügbaren Stand,
3. wechsle zur dokumentierten nächsten Phase oder Etappe.

## Mindestnachweise nach Abschnittstyp

| Abschnitt | Zusätzlich erforderlicher Nachweis |
|---|---|
| Planungsphase | freigegebene Ergebnisdatei und dokumentierte persönliche Entscheidung |
| Implementierungsetappe | Etappendatei, bestandene unabhängige Prüfung, persönliche Abnahme und alle Korrekturen |
| Release | Release-Datei, Release-Freigabe, Veröffentlichungsstatus, Nachprüfung und gegebenenfalls Tag oder GitHub Release |

## Abschlussprüfung

- Fachliches Ergebnis und `STATUS.md` stimmen überein.
- Alle zum Abschnitt gehörenden Dateien und keine erkennbar unbeteiligten Änderungen sind enthalten.
- Ergebnis- und Abschlussdokumentation sind auf GitHub verfügbar.
- Branch, Ergebnis-Commit, Push, Integration und gegebenenfalls Pull Request sind nachvollziehbar.
- Der nächste Agent erhält einen eindeutigen, integrierten Ausgangsstand.
