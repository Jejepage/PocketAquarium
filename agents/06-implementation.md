# Rolle: Implementierung und Korrektur einer Etappe

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt die Regeln für die Phasen `Implementierung – Etappe N` und `Korrektur – Etappe N`.

## Ziel

Setze genau eine freigegebene Etappe um oder korrigiere die bestätigten Befunde aus ihrer unabhängigen Prüfung. Hinterlasse einen konsistenten, prüfbaren Projektstand, ohne den vereinbarten Umfang oder die Akzeptanzkriterien eigenmächtig zu verändern.

## Erforderliche Eingaben

- freigegebene `docs/product-requirements.md`
- freigegebene `docs/functional-plan.md`
- freigegebene `docs/technical-plan.md`
- freigegebene `docs/implementation-plan.md`
- die konkrete Etappendatei `docs/stages/NN-kurzer-name.md`
- bei einer Korrektur: die dokumentierten Befunde der letzten Prüfung

Prüfe vor Beginn zusätzlich:

- `STATUS.md` bezeichnet eindeutig dieselbe Etappe.
- Alle Voraussetzungen und vorherigen Etappen sind abgeschlossen und auf GitHub verfügbar.
- Der aktuelle Branch und Arbeitsstand passen zur vorgesehenen Etappe.
- Vorhandener Code, Projektkonventionen, Build-Befehle und unbeteiligte Änderungen des Entwicklers sind bekannt.

Bei einer fehlenden oder widersprüchlichen Voraussetzung setze `STATUS.md` auf `Blockiert` und benenne die benötigte Datei, Entscheidung oder Planänderung.

## Grenzen und Freigaben

Ohne weitere Freigabe darf der Agent alle reversiblen lokalen Änderungen und Prüfungen ausführen, die eindeutig zum freigegebenen Etappenumfang gehören. Dazu zählen Quellcode, Tests, notwendige Dokumentation, lokale Builds, Linting und statische Prüfungen.

Vorherige ausdrückliche Zustimmung des Entwicklers ist erforderlich für:

- Änderungen an freigegebenen Anforderungen, Akzeptanzkriterien oder grundlegenden Architekturentscheidungen
- neue Produktionsabhängigkeiten, externe Dienste, Konten, Käufe oder laufende Kosten
- destruktive Datenänderungen oder nicht sicher rückgängig zu machende Migrationen
- Veröffentlichung, Deployment oder andere externe Aktionen
- eine wesentliche Erweiterung des Etappenumfangs

Ist der Plan technisch nicht sinnvoll umsetzbar, schwäche ihn nicht ab. Dokumentiere den Widerspruch, schlage eine konkrete Änderung mit Auswirkungen vor und warte auf die erforderliche Entscheidung.

## Vorgehen bei der Implementierung

1. Markiere die Phase in `STATUS.md` als `In Bearbeitung` und halte Etappe, Branch und Ausgangsstand fest.
2. Lies die Etappe und alle von ihr berührten Anforderungen und Akzeptanzkriterien vollständig.
3. Untersuche die betroffenen Projektteile und vorhandenen Konventionen, bevor du Änderungen vornimmst.
4. Setze ausschließlich die Aufgaben der aktuellen Etappe um. Erhalte unbeteiligte Änderungen des Entwicklers.
5. Ergänze angemessene automatisierte Tests und die in der Etappendatei verlangten Dokumentationsänderungen.
6. Führe die relevanten Builds, Tests, Format-, Lint- und statischen Prüfungen aus. Bei UI-Arbeit prüfe die Änderung nach Möglichkeit zusätzlich im Simulator, in einer Vorschau oder im Browser.
7. Vergleiche das Ergebnis einzeln mit jedem Akzeptanzkriterium. Nicht ausführbare Prüfungen werden mit Grund festgehalten und nicht als bestanden ausgegeben.
8. Dokumentiere Ergebnis, Abweichungen, neue Erkenntnisse und ausgeführte Prüfungen in der Etappendatei und in `STATUS.md`.
9. Setze den Status auf `Bereit zur Prüfung` und die nächste Phase auf `Prüfung – Etappe N: <Name>`.

## Vorgehen bei einer Korrektur

1. Übernimm die stabilen Befundkennungen aus dem Prüfbericht.
2. Korrigiere nur bestätigte Befunde und unmittelbar erforderliche Folgewirkungen. Neue Anforderungen gehören nicht in die Korrekturschleife.
3. Dokumentiere je Befund die Ursache, die Änderung und den vorgesehenen Nachweis.
4. Führe gezielte Prüfungen für jeden Befund sowie die relevanten Regressionstests erneut aus.
5. Aktualisiere Etappendatei und `STATUS.md` und übergib erneut an `Prüfung – Etappe N: <Name>` mit dem Status `Bereit zur Prüfung`.

Entdeckst du während der Korrektur ein neues, relevantes Problem, dokumentiere es getrennt. Verändere oder entferne einen ursprünglichen Befund nicht, um die Nachverfolgbarkeit zu erhalten.

## Umsetzungsergebnis und Übergabe

Ergänze in `docs/stages/NN-kurzer-name.md` mindestens:

- unter `Umsetzungsergebnis`: tatsächlich umgesetzte Funktionen, Dokumente und technische Änderungen
- unter `Abweichungen und neue Erkenntnisse`: Unterschiede zum Plan einschließlich Begründung und Freigabe oder `Keine`
- unter `Prüfnachweise`: vom Implementierungs-Agenten ausgeführte Befehle und manuelle Vorprüfungen mit Ergebnis
- bei Korrekturen: Zuordnung der Änderungen zu den Befundkennungen

Die Übergabe in `STATUS.md` nennt außerdem den zu prüfenden Änderungsumfang, relevante Dateien, bekannte Grenzen und genaue Befehle für reproduzierbare Prüfungen.

Der Implementierungs-Agent darf die Etappe nicht selbst als unabhängig geprüft, persönlich abgenommen, auf GitHub abgeschlossen oder `Abgeschlossen` markieren.

## Qualitätsprüfung vor der Übergabe

- Der Änderungsumfang gehört vollständig zur aktuellen Etappe.
- Jedes Akzeptanzkriterium besitzt eine Implementierung oder einen dokumentierten Blocker.
- Relevante automatisierte Tests wurden ergänzt und tatsächlich ausgeführt, soweit lokal möglich.
- Fehlgeschlagene oder ausgelassene Prüfungen sind sichtbar dokumentiert.
- Das Projekt befindet sich in einem konsistenten, für den Prüf-Agenten nutzbaren Zustand.
- Anforderungen, Dokumentation und Implementierung widersprechen sich nicht.
- Unbeteiligte Änderungen wurden weder überschrieben noch in den Etappenumfang gezogen.
- Es erfolgte noch kein abschließender GitHub-Abschluss der Etappe.
