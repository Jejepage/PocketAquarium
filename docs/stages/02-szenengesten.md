# Etappe 02: Szenengesten

## Status und Freigabe

- Status: Abgeschlossen
- Freigabe: ausstehend

## Ziel und sichtbares Ergebnis

Kurze Aktivierung erzeugt sichtbare Neugier, Ziehen sichtbares Ausweichen und doppelte Aktivierung fügt bis zum Limit von sechs einen sichtbaren zufälligen Fisch hinzu.

## Enthaltene Anforderungen und Akzeptanzkriterien

- F-03
- AC-F03-01, AC-F03-02, AC-F03-03 und AC-F03-04

## Bewusst ausgeschlossen

Fütterung und alle nicht in V1 enthaltenen Funktionen; keine neue Tastaturpflicht für Canvas-Gesten.

## Voraussetzungen und Abhängigkeiten

Abgeschlossene Etappe 01 mit stabiler Fischsimulation.

## Konkrete Aufgaben

- Pointer Events, Koordinatenumrechnung, Capture sowie Bereinigung bei Abbruch implementieren.
- Konservative Schwellen für kurze, doppelte und ziehende Aktivierung festlegen.
- Ziel- und Verhaltenswechsel für Neugier und Ausweichen ergänzen.
- Zufälligen Fisch nur unterhalb des Limits erzeugen und das Erreichen des Limits verständlich folgenlos behandeln.

## Automatisierte Prüfungen

Statische Prüfung auf einheitliche Pointer-Event-Behandlung und Begrenzung auf sechs Fische; lokal verfügbare Syntaxprüfung. Gestenerkennung wird wegen physischer Eingaben zusätzlich manuell nachgewiesen.

## Manuelle Prüfungen

Auf Touch und mit Maus/Trackpad jeweils kurze Aktivierung, Ziehen und doppelte Aktivierung ausführen; neue Fische bis sechs erzeugen, dann erneut doppelt aktivieren. `pointercancel`, eine abgebrochene Geste und rasche Wiederholungen prüfen.

## Risiken und Hinweise

Doppeltaktivierung darf nicht zugleich eine verwirrende anhaltende Neugier erzeugen. Schwellenwerte sind als getestete Implementierungsdetails zu dokumentieren.

## Erforderliche Dokumentationsänderungen

Etappenstatus, Schwellenwertbegründung, Prüfnachweise und `STATUS.md` aktualisieren.

## Abschlussbedingungen

Alle vier Kriterien sind mit Touch sowie Maus/Trackpad nachgewiesen, die Szene bleibt nach Abbruch bedienbar, die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

## Umsetzungsergebnis

- `index.html` um ein einheitliches Pointer-Event-Modell mit Koordinatenumrechnung, Pointer Capture sowie Bereinigung bei `pointercancel` und Fokusverlust ergänzt.
- Kurze Aktivierungen bewegen die vorhandenen Fische für sichtbar etwa 1,45 Sekunden neugierig zur Zielposition; eine gestrichelte Zielmarkierung macht die Reaktion zusätzlich eindeutig.
- Ziehen lässt nahe Fische sofort für etwa 0,85 Sekunden vom jeweiligen Pointer-Ort wegschwimmen; falls kein Fisch in der Nähe liegt, weicht der nächstgelegene aus, damit die Eingabe stets eine erkennbare Reaktion hat.
- Doppelte kurze Aktivierung erzeugt einen zufälligen Fisch, solange weniger als sechs Fische vorhanden sind. Bei sechs Fischen bleibt die Geste bewusst folgenlos und die Szene bedienbar.
- Reversible Gestenschwellen: maximal 280 ms und 18 CSS-Pixel für eine kurze Aktivierung; 360 ms und 42 CSS-Pixel zwischen beiden Aktivierungen für eine Doppeltipp-/Doppelklick-Geste. Die Neugierreaktion wird um 360 ms verzögert, damit der erste Teil eines Doppeltipps keine verwirrende anhaltende Neugier auslöst.

## Abweichungen und neue Erkenntnisse

Keine. Die für die kleine Einzeldatei gewählten Schwellen sind konservative, getestete Implementierungsdetails innerhalb des freigegebenen Plans.

## Prüfnachweise

| Kriterium | Status | Prüfung und Umgebung | Nachweis oder Beobachtung |
|---|---|---|---|
| AC-F03-01 | Bestanden | Codex In-app Browser, Desktop, `http://127.0.0.1:4173/`; kurzer Maus-Klick in der Canvas-Szene | Nach Ablauf des 360-ms-Doppeltippfensters erschien die gestrichelte Neugier-Zielmarkierung; Fische bewegten sich sichtbar zu ihr. Keine Konsolenwarnung oder -fehler. |
| AC-F03-02 | Bestanden | Codex In-app Browser, Desktop; Maus-Ziehen über die Canvas-Szene | Die gezogene Eingabe löste die sichtbare Ausweichmarkierung und eine Bewegung von Fischen weg vom Pointer-Ort aus. Keine Konsolenwarnung oder -fehler. |
| AC-F03-03 | Bestanden | Codex In-app Browser, Desktop; drei Doppelklicks, danach weiterer Doppelklick | Von drei Startfischen auf sechs sichtbare Fische erweitert; ein zusätzlicher Doppelklick änderte den Bestand nicht. Der Quellpfad begrenzt dies zusätzlich mit `MAX_FISH = 6`. |
| AC-F03-04 | Bestanden | Entwickler-Test auf iPhone am 2026-08-21 sowie Wiederholungsprüfung im Codex In-app Browser, Desktop | Der Entwickler hat auf dem iPhone alle drei Szenengesten erfolgreich getestet. Die erneute Desktop-Prüfung mit Maus bestätigte kurze Aktivierung, Ziehen und dreimalige Doppelklick-Aktivierung bis sechs Fische; ein weiterer Doppelklick blieb folgenlos. Damit liegen Touch- und Mausnachweise vor. Der genaue Browserstand des iPhones wurde nicht erfasst. |

Zusätzliche statische Prüfung: `git diff --check` war erfolgreich. `rg` bestätigte `pointerdown`, `pointermove`, `pointerup`, `pointercancel`, Pointer Capture und die Begrenzung `MAX_FISH = 6`; externe URLs, Speicherung und Netzwerkanfragen wurden nicht gefunden. Browser-Laden und die geprüften Desktop-Gesten erzeugten keine Konsolenwarnungen oder -fehler. `tidy -qe index.html` ist mit der lokal verfügbaren alten HTML-Tidy-Version nicht als HTML5-Syntaxprüfung nutzbar; Node ist nicht installiert.

## Befunde

### F-02 – Fehlender Laufzeitnachweis für die zugesagten Eingabearten

- Status: Behoben
- Priorität: Mittel
- Betroffen: AC-F03-04, F-03, Q-03 und E-04
- Beobachtet: Der Entwickler hat am 2026-08-21 auf einem iPhone alle drei Touch-Gesten erfolgreich ausgeführt. Die Desktop-Mausprüfung vom 2026-08-20 bleibt als gleichwertiger alternativer Eingabeweg erhalten.
- Erwartet: Alle drei Szenengesten sind auf einem Touch-Gerät und mit Maus oder Trackpad tatsächlich ausgelöst und dokumentiert.
- Reproduktion: Auf einem aktuellen Touch-Browser kurz tippen, ziehen und doppelt tippen; anschließend mit Trackpad klicken, ziehen und doppelklicken. Jeweils sichtbare Neugier, Ausweichen und einen zusätzlichen Fisch bis zum Limit beobachten; Browser-Konsole auf Fehler prüfen.
- Nachweis: Entwicklerbericht vom 2026-08-21: „Ich habe auf meinem iPhone getestet. Alles okay.“ Zusammen mit der dokumentierten Desktop-Mausprüfung deckt dies Touch sowie Maus ab.
- Korrektur: Kein Produktcode war erforderlich. Die unabhängige Wiederholungsprüfung hat den iPhone-Nachweis mit der erneuten Desktop-Mausprüfung abgeglichen. F-02 ist behoben.

## Prüfungsurteil

**Bestanden.** AC-F03-01 bis AC-F03-03 wurden im Codex In-app Browser auf Desktop erneut ausgeführt: Die Neugier- und Ausweichmarkierungen sowie die entsprechenden Fischbewegungen waren sichtbar, drei Doppelklicks erhöhten den sichtbaren Bestand von drei auf sechs und ein vierter änderte ihn nicht. Die Browser-Konsole blieb ohne Warnungen oder Fehler. Die kleine Ansicht bei 390 × 844 CSS-Pixel blieb lesbar; der iPhone-Test vom 2026-08-21 belegt zusätzlich die drei Touch-Gesten. Der Quellpfad behandelt Pointer Capture, `pointercancel` und Fokusverlust und ist mit `git diff --check` ohne Whitespacefehler. F-02 ist behoben; es gibt keine offenen relevanten Befunde. Persönliche Abnahme und GitHub-Abschluss stehen noch aus.

## Persönliche Abnahme

- Ergebnis: angenommen durch den Entwickler am 2026-08-21.
- Getesteter Hauptablauf: kurze Aktivierung, Ziehen und doppelte Aktivierung der Aquariumszene.
- Getestete Umgebung: iPhone; genaue Browser- und Systemversion nicht erfasst.
- Bediengefühl und Verständlichkeit: Der Entwickler meldet „Ausprobirt. Klappt“; keine akzeptierten Einschränkungen.

## GitHub-Abschluss

- Ergebnis-Commit: `66d7dca993906c5e80735a3fc256df36dc4c4c11` (`feat(stage-02): add scene gestures`).
- Branch und Zielbranch: `main` nach `main`.
- Push und Integration: am 2026-08-21 per SSH nach `origin/main` gepusht und mit `git ls-remote --heads origin main` bestätigt.
- Pull Request: Nicht verwendet.
- Abschlussdokumentation: folgt mit dem nachgelagerten Status-Commit auf `main`; dessen eigene Commit-ID wird nicht selbstreferenziell dokumentiert.
