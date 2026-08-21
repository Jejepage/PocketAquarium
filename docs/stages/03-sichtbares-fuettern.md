# Etappe 03: Sichtbares Füttern

## Status und Freigabe

- Status: Bestanden; persönlich abgenommen
- Freigabe: ausstehend

## Ziel und sichtbares Ergebnis

Die dauerhaft sichtbare Schaltfläche **Füttern** kann per Zeiger und Tastatur aktiviert werden. Sichtbares Futter sinkt; mindestens ein Fisch schwimmt hin und die Futtermenge wird sichtbar weniger.

## Enthaltene Anforderungen und Akzeptanzkriterien

- F-04
- AC-F04-01 und AC-F04-02

## Bewusst ausgeschlossen

Mehrere gleichzeitige Fütterungen, Pflege- oder Inventarmechaniken, Audio sowie dauerhafte Speicherung.

## Voraussetzungen und Abhängigkeiten

Abgeschlossene Etappen 01 und 02 mit stabiler Szene, Fischzuständen und Eingabebehandlung.

## Konkrete Aufgaben

- Beschrifteten nativen Button mit sichtbarem Fokus, sinnvoller Position und programmatischem Namen fertigstellen.
- Futterpartikel und exklusiven Fütterungszustand implementieren; den Button bis zum Ende der sichtbaren Reaktion deaktivieren.
- Mindestens einen geeigneten Fisch auf Futter zielen und beim Erreichen Partikel sichtbar reduzieren lassen.
- Vorrang der Fütterung vor Neugier und die Rückkehr eines geflohenen Fisches zum Futterziel wie geplant behandeln.

## Automatisierte Prüfungen

Statische Prüfung auf nativen Button, sichtbare Textbeschriftung, fehlende externen Ressourcen und die Sperre gegen paralleles Futter. Soweit ohne neue Abhängigkeit verfügbar: HTML-/JavaScript-Syntaxprüfung.

## Manuelle Prüfungen

Button mit Maus/Touch aktivieren und per Tabulator fokussieren sowie per Tastatur auslösen. Futter, Zielbewegung und sichtbare Verringerung beobachten; erneutes Füttern während der Reaktion, Szenengesten während Fütterung und erneutes Füttern nach Abschluss prüfen.

## Risiken und Hinweise

Der Button darf Canvas-Gesten nicht verdecken; Futter und Fischbewegung müssen sich deutlich von Neugier unterscheiden.

## Erforderliche Dokumentationsänderungen

Etappenstatus, Zugänglichkeits- und Prüfnachweise sowie `STATUS.md` aktualisieren.

## Abschlussbedingungen

Beide Kriterien sind auf Touch und Desktop nachgewiesen, Fokus und Bezeichnung sind sichtbar und sinnvoll, konkurrierendes Futter ist verhindert, die unabhängige Prüfung ist bestanden und der Entwickler hat persönlich abgenommen; erst danach erfolgt der GitHub-Abschluss.

## Umsetzungsergebnis

- `index.html` enthält nun einen nativen, dauerhaft sichtbaren Button **Füttern** mit sichtbarem Fokus und programmatischem Namen.
- Die Aktivierung erzeugt zwölf sichtbare Futterpartikel. Sie sinken langsam und werden durch einen gewählten Fisch in einem deutlich getrennten Rhythmus gefressen.
- Während sichtbares Futter vorhanden ist, ist die Fütterung exklusiv: Der Button ist deaktiviert und wird erst nach dem letzten Bissen wieder aktiviert.
- Der Futterfisch hat Vorrang vor Neugier. Ein unmittelbar ausgelöstes Ausweichen bleibt bestehen; danach übernimmt der Futterpfad wieder das Ziel des Fisches.

## Abweichungen und neue Erkenntnisse

Keine. Der Fressrhythmus von 220 ms pro Partikel ist ein reversibles Umsetzungsdetail, damit die sichtbare Verringerung eindeutig beobachtbar bleibt.

## Prüfnachweise

| Kriterium | Status | Prüfung und Umgebung | Nachweis oder Beobachtung |
|---|---|---|---|
| AC-F04-01 | Bestanden | Entwickler-Test auf iPhone, 2026-08-21; Desktop-Wiederholungsnachweis liegt vor | Der Entwickler meldet den vollständig erfolgreichen iPhone-Test: Die sichtbare Schaltfläche **Füttern** war erreichbar und auslösbar. Der Desktop-Nachweis bestätigt zusätzlich Beschriftung, Tabulatorfokus und 3-px-Fokuskontur. |
| AC-F04-02 | Bestanden | Entwickler-Test auf iPhone, 2026-08-21; Desktop-Wiederholungsnachweis liegt vor | Der Entwickler meldet den vollständig erfolgreichen iPhone-Ablauf: sichtbares sinkendes Futter, zielgerichtete Fischbewegung, schrittweise Verringerung, Sperre während der Fütterung und Reaktivierung danach. Der Desktop-Nachweis bestätigt denselben Ablauf ohne Konsolenwarnungen oder -fehler. |

Zusätzliche unabhängige Prüfungen: Die Ansicht blieb bei 390 × 844 CSS-Pixeln lesbar; Button, Fische und Umgebungsbewegung waren sichtbar. `git diff --check` war erfolgreich. Die statische Prüfung bestätigte Button, Futterzustand, Deaktivierung und Wiederaktivierung sowie das Fehlen von externen URLs, Speicherzugriffen und Netzwerkanfragen. Die Browserkonsole blieb bei allen Desktop-Prüfungen ohne Warnungen oder Fehler. `tidy -qe index.html` kann wegen der lokal verfügbaren, veralteten HTML-Tidy-Version nicht als HTML5-Syntaxprüfung verwendet werden; es erkennt unter anderem `main` und `canvas` nicht.

## Befunde

- **F-03 – Mittel – AC-F04-01 und AC-F04-02 – Behoben:** Der verpflichtende Touch-Nachweis fehlte zunächst. Der Entwickler meldete am 2026-08-21 den vollständigen iPhone-Test ohne Auffälligkeiten: Beschriftung und Aktivierung, sinkendes Futter, zielgerichtete Fischbewegung, schrittweises Fressen, Sperre und Reaktivierung waren erfolgreich. Es war keine Produktcode-Änderung erforderlich.

## Gesamturteil

**Bestanden.** F-03 ist durch den iPhone-Test behoben; der unabhängige Desktop-Regressionstest und die statische Prüfung bestätigen den unveränderten Fütterungsablauf. Keine relevanten Befunde sind offen.

## Persönliche Abnahme

Am 2026-08-21 persönlich durch den Entwickler auf dem iPhone abgenommen; keine Einschränkungen akzeptiert.

## GitHub-Abschluss

- Branch und Zielbranch: `main` nach `main`
- Ergebnis-Commit: `b551198cb2f12b5ab4acd0d4df0e6e7d3429decf` (`feat(stage-03): add visible feeding`)
- Push und Integration: 2026-08-21 per SSH auf `origin/main` gepusht und mit `git ls-remote --heads origin main` bestätigt
- Pull Request: Nicht verwendet
- Bekannte Einschränkungen: Keine
