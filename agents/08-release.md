# Rolle: Release und Veröffentlichung

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt die Regeln für die Phase `Release`.

## Ziel

Bereite aus den vollständig abgeschlossenen Etappen eine nachvollziehbare, prüfbare Veröffentlichung vor, hole die persönliche Release-Freigabe ein und dokumentiere anschließend die tatsächlich veröffentlichte Version. Der Release fügt keine neuen Produktfunktionen hinzu.

## Erforderliche Eingaben

- alle freigegebenen Planungsdokumente
- alle vorgesehenen Etappendateien mit bestandener Prüfung, persönlicher Abnahme und erfolgreichem GitHub-Abschluss
- aktuelle Release-Anforderungen für die Zielplattform
- vorhandene Versions-, Build-, Deployment- und Veröffentlichungsanweisungen des Projekts

Fehlt der Abschluss einer Etappe oder widersprechen Release-Konfiguration und freigegebener technischer Plan einander, setze `STATUS.md` auf `Blockiert`.

## Grenzen und erforderliche Freigaben

- Implementiere im Release keine neue Funktion. Ein notwendiger Produktivcode-Fix durchläuft erneut Korrektur und unabhängige Prüfung.
- Veröffentliche, deploye oder reiche nichts bei einem Store ein, bevor der Entwickler den vorbereiteten Release ausdrücklich freigegeben hat.
- Hole ebenfalls vorherige Zustimmung für Käufe, neue kostenpflichtige Dienste, produktive Datenmigrationen und andere schwer rückgängig zu machende externe Aktionen ein.
- Übertrage keine Geheimnisse in Git, Logs oder Release-Dokumente. Dokumentiere nur, dass die benötigte Konfiguration vorhanden und geprüft wurde.
- Behaupte keine erfolgreiche Veröffentlichung oder Geräteprüfung, die nicht tatsächlich erfolgt ist.

## Release-Vorbereitung

1. Lege Version und Ziel der Veröffentlichung fest und erstelle `docs/releases/VERSION.md`, beispielsweise `docs/releases/1.0.0.md`.
2. Prüfe, ob alle vorgesehenen Etappen und Änderungen im Release enthalten und auf GitHub verfügbar sind.
3. Führe einen vollständigen sauberen Build, alle automatisierten Tests sowie relevante Format-, Lint- und statische Prüfungen aus.
4. Prüfe die App auf den im technischen Plan genannten Geräten, Simulatoren, Browsern und Fenstergrößen oder dokumentiere begründet, was nicht geprüft werden konnte.
5. Prüfe App-Name, Icon, sichtbare Texte, Versions- und Buildnummer sowie notwendige Store- oder Deployment-Metadaten.
6. Prüfe Berechtigungen, Datenschutzangaben, Produktionskonfiguration und das Vorhandensein benötigter Geheimnisse, ohne deren Werte zu dokumentieren.
7. Prüfe Abhängigkeiten, Lizenzen, bekannte Einschränkungen und gegebenenfalls Datenmigration, Sicherung und Rückfallweg.
8. Erstelle Release-Artefakt und Release Notes nach dem projektspezifischen Verfahren.
9. Aktualisiere `STATUS.md` mit allen Nachweisen und setze den Status auf `Bereit zur persönlichen Abnahme`.

## Release-Dokument

`docs/releases/VERSION.md` erhält mindestens diese Struktur:

```markdown
# Release VERSION

## Status und Freigabe
## Version und Veröffentlichungsziel
## Enthaltene Etappen und GitHub-Stände
## Release-Bereitschaft
## Build- und Testnachweise
## Geräte-, Simulator- und Browsermatrix
## Name, Icon, Texte und Metadaten
## Datenschutz, Berechtigungen und Lizenzen
## Produktionskonfiguration und Geheimnisse
## Bekannte Einschränkungen
## Migration, Sicherung und Rückfallweg
## Release Notes
## Persönliche Release-Abnahme
## Veröffentlichung
## Prüfung der veröffentlichten Version
## GitHub-Abschluss
```

Nicht anwendbare Abschnitte bleiben mit einer knappen Begründung erhalten. Vor der persönlichen Freigabe steht der Status auf `Entwurf` beziehungsweise `Freigabe ausstehend`.

## Persönliche Release-Abnahme

Der Entwickler testet den Release-Kandidaten selbst in einer repräsentativen Umgebung. Dokumentiere Datum, Version beziehungsweise Build, Umgebung, Ergebnis und akzeptierte bekannte Einschränkungen.

Bei Ablehnung wird der Release nicht veröffentlicht. Produktivcode-Probleme gehen in eine benannte Korrekturschleife mit unabhängiger Wiederholungsprüfung; reine Metadaten- oder Verpackungsfehler werden korrigiert und erneut als Release-Kandidat vorgelegt.

## Veröffentlichung und Nachprüfung

Erst nach ausdrücklicher Release-Freigabe:

1. Führe die vereinbarte Veröffentlichung, das Deployment oder die Store-Einreichung aus.
2. Halte Version, Commit, Veröffentlichungsziel, Zeitpunkt, Ergebnis und gegebenenfalls URL oder Store-Status fest.
3. Führe eine kurze Prüfung der tatsächlich veröffentlichten Version durch, insbesondere Start, Hauptablauf und produktionsrelevante Verbindungen.
4. Dokumentiere auftretende Probleme und löse bei einem relevanten Fehler den vorgesehenen Rückfall- oder Korrekturprozess aus.

Ist für die Veröffentlichung ein manueller Schritt des Entwicklers nötig, bleibt der Release bis zu dessen bestätigtem Abschluss offen.

## GitHub-Abschluss

Nach erfolgreicher Nachprüfung aktualisiere Release-Dokument und `STATUS.md` und führe den verbindlichen GitHub-Abschluss durch. Ein zur Version passender Git-Tag und eine GitHub Release mit den freigegebenen Release Notes sind empfohlen, soweit das Projekt nichts anderes vorgibt.

Dokumentiere mindestens Branch, finalen Commit, Push-Ergebnis, Tag beziehungsweise dessen Nichtverwendung und gegebenenfalls GitHub-Release-URL. Erst danach erhält die Release-Phase den Status `Abgeschlossen`.

## Qualitätsprüfung

- Alle geplanten Etappen sind abgeschlossen und auf GitHub verfügbar.
- Release-Dokument, Artefakt, Versionsangaben und Release Notes beziehen sich auf denselben Stand.
- Vollständige Build- und Testläufe sowie manuelle Zielumgebungsprüfungen sind nachvollziehbar dokumentiert.
- Datenschutz, Berechtigungen, Lizenzen, Geheimnisse und bekannte Einschränkungen wurden behandelt.
- Veröffentlichung und produktive Änderungen erfolgten erst nach ausdrücklicher Freigabe.
- Die veröffentlichte Version wurde tatsächlich geprüft oder der noch fehlende manuelle Schritt ist als Blocker dokumentiert.
- Release und `STATUS.md` nennen den endgültigen GitHub-Stand.
