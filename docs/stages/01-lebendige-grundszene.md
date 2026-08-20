# Etappe 01: Lebendige Grundszene

## Status und Freigabe

- Status: Persönlich abgenommen – bereit zum GitHub-Abschluss
- Freigabe: persönlich am 2026-08-20 durch den Entwickler

## Ziel und sichtbares Ergebnis

Eine direkt geöffnete, responsive Aquariumansicht zeigt drei selbstständig schwimmende, erkennbar unterschiedliche Fische sowie Blasen, Pflanzen und Schwebepartikel in ruhiger Dichte.

## Enthaltene Anforderungen und Akzeptanzkriterien

- F-01, F-02 und F-05
- AC-F01-01, AC-F01-02, AC-F02-01, AC-F02-02, AC-F05-01 und AC-F05-02

## Bewusst ausgeschlossen

Szenengesten, weitere Fische, Fütterung, Nachtmodus, Audio, Speicherung, externe Ressourcen und Produktfunktionen außerhalb des freigegebenen V1-Umfangs.

## Voraussetzungen und Abhängigkeiten

Freigegebene drei Planungsdokumente; keine frühere Umsetzungsetappe.

## Konkrete Aufgaben

- Die einzige HTML-Datei mit Canvas, sichtbarem Fallback und vorbereitetem nativen Fütterungsbutton anlegen.
- Responsives Canvas, zeitdelta-basierte Animationsschleife und Größenbehandlung umsetzen.
- Drei Fischvarianten, begrenzte Blasen, Pflanzen und Partikel erzeugen und ruhig zeichnen.
- Laufzeitwerte ausschließlich im Speicher halten und die statischen Datenschutzgrenzen prüfen.

## Automatisierte Prüfungen

Statische Prüfung der Einzeldatei, fehlender externer URLs und fehlender Speicher-/Abhängigkeitsnutzung; vorhandene lokale Syntax- oder Lint-Prüfung ausführen. Es ist keine Testumgebung geplant, weil der technische Plan keine Toolchain voraussetzt.

## Manuelle Prüfungen

Datei in einem aktuellen Desktop-Browser und einem kleinen Touch-Viewport öffnen; Aquarium, drei Fische, unterschiedliche Bewegung und alle drei Umgebungsarten beobachten. Prüfen, dass die Szene weder überfüllt noch beim Größenwechsel leer oder unlesbar wird.

## Risiken und Hinweise

Die Zeichendichte konservativ halten; große Zeitdeltas nach inaktiven Tabs begrenzen.

## Erforderliche Dokumentationsänderungen

Etappenstatus, Umsetzungsergebnis, Prüfnachweise und `STATUS.md` aktualisieren.

## Abschlussbedingungen

Alle sechs zugeordneten Akzeptanzkriterien sind nachgewiesen, die Datei bleibt ohne Installation ausführbar, die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

## Umsetzungsergebnis

- `index.html` als einzige eigenständig ausführbare Anwendung angelegt.
- Responsive Canvas-2D-Aquariumansicht mit zeitdelta-basierter `requestAnimationFrame`-Schleife und `ResizeObserver` umgesetzt.
- Drei unterschiedlich große, gefärbte und schnell schwimmende Fische einschließlich eigener Bewegungsparameter angelegt.
- Begrenzte Blasen, Schwebepartikel und drei sanft bewegte Pflanzen programmgeneriert gezeichnet.
- Sichtbaren nativen Button **Füttern** für Etappe 03 vorbereitet; er ist bis zur dortigen Umsetzung deaktiviert, damit die aktuelle Etappe keine folgenlose Produktaktion vortäuscht.
- Keine externen Ressourcen, Netzwerkanfragen, Speicherung oder Abhängigkeiten ergänzt.

## Abweichungen und neue Erkenntnisse

Keine. Die Fütterungsaktion ist gemäß Etappengrenze vorbereitet, aber noch nicht implementiert.

## Prüfnachweise

Die folgende Prüfung wurde in einem getrennten Prüf-Arbeitslauf vorgenommen. Sie ist keine persönliche Abnahme und ersetzt diese nicht.

| Kriterium | Status | Prüfung und Umgebung | Nachweis oder Beobachtung |
|---|---|---|---|
| AC-F01-01 | Bestanden | Lokaler Server `python3 -m http.server 4173 --bind 127.0.0.1`; Codex In-app Browser, 1280 × 720 und 390 × 844 | Beim direkten Aufruf von `http://127.0.0.1:4173/` erscheint ohne Auswahl die visuell eindeutig als Aquarium lesbare Unterwasseransicht. |
| AC-F01-02 | Bestanden | Dieselbe Browserprüfung | In derselben Ansicht sind drei Fische, Pflanzen, Blasen und Partikel sichtbar; es gibt keine weitere Ansicht oder Navigation. |
| AC-F02-01 | Bestanden | Beobachtung ohne Eingabe im Browser, jeweils mindestens 1,2 Sekunden nach Laden | Die drei Fische ändern Position und führen eine eigene vertikale Schwimmbewegung aus; die Animation läuft über `requestAnimationFrame`. |
| AC-F02-02 | Bestanden | Visuelle Prüfung auf Desktop und 390 × 844; Quellprüfung der drei Startobjekte | Fischgröße, Farbe, Geschwindigkeit und Bewegungsparameter unterscheiden sich sichtbar (gelb/klein, rosa/groß, grün/klein). |
| AC-F05-01 | Bestanden | Visuelle Browserprüfung auf Desktop und 390 × 844 | Langsam aufsteigende Blasen, sanft wogende Pflanzen und dezente Schwebepartikel sind sichtbar. |
| AC-F05-02 | Bestanden | Visuelle Browserprüfung auf Desktop und 390 × 844 | Die begrenzten Umgebungsobjekte überlagern die drei Fische nicht; Fische und ihre jeweiligen Bewegungen bleiben unterscheidbar. |

- Größenwechsel: Bei 1280 × 720 misst die sichtbare Canvas-Fläche 1096 × 558 CSS-Pixel; bei 390 × 844 366 × 658 CSS-Pixel. In beiden Größen blieb die Szene sichtbar und lesbar.
- Browserlaufzeit: Seitentitel `PocketAquarium`, Canvas-Rolle mit zugänglicher Bezeichnung und sichtbarer vorbereiteter Button **Füttern** vorhanden; keine Warnungen oder Fehler in der Browser-Konsole.
- Statisch: `git diff --check` erfolgreich; die Suche nach externen URLs, Speicherzugriffen, Netzwerkanfragen sowie Script-/Style-Abhängigkeiten lieferte außer einem Kommentar keine Treffer.
- Eine lokale Node-Syntaxprüfung war nicht möglich, weil `node` nicht installiert ist. Das erfolgreiche Laden und Ausführen im Browser ohne Konsolenfehler dient als Laufzeitnachweis.

## Befunde

Keine. Die in Etappe 01 ausdrücklich vorbereitete, noch deaktivierte Fütterungsaktion ist kein Befund, weil Fütterung ausschließlich zu Etappe 03 gehört.

## Prüfurteil

**Bestanden.** Alle sechs dieser Etappe zugeordneten Akzeptanzkriterien sind nachgewiesen; es gibt keine offenen relevanten Befunde. Die Etappe ist bereit für die persönliche Abnahme.

## Persönliche Abnahme

- Ergebnis: angenommen durch den Entwickler am 2026-08-20.
- Getesteter Hauptablauf: direktes Öffnen und Beobachten der lebendigen Grundszene.
- Akzeptierte Einschränkungen: Keine.

## GitHub-Abschluss

Ausstehend: Der persönliche Abnahmestatus wird mit der Ergebnisdatei und der Abschlussdokumentation auf `main` veröffentlicht.
