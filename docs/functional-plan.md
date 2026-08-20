# Funktions- und UI-Plan

## Status und Freigabe

- Status: Freigegeben
- Freigabe: persönlich am 2026-08-20 durch den Entwickler
- Grundlage: freigegebene `docs/product-requirements.md` vom 2026-08-20
- Stand: 2026-08-20

## Geltungsbereich und Grundlagen

Dieser Plan beschreibt ausschließlich die fünf PRD-Kernfunktionen F-01 bis F-05 für eine einzelne, direkt geöffnete Aquariumszene. Er ergänzt keine Konten, Fortschrittsmechaniken, Audiofunktionen oder späteren Optionen.

## Informations- und Navigationsstruktur

PocketAquarium hat eine einzige Hauptansicht. Es gibt keine Startseite, Navigation, Dialoge oder Einstellungen. Beim Öffnen ist die Aquariumszene sofort nutzbar; die sichtbare Fütterungsaktion ist Teil derselben Ansicht.

## Wichtigste Benutzerabläufe

| Ablauf | Start | Nutzeraktion | Sichtbares Ergebnis |
|---|---|---|---|
| A-01 Beobachten | Aquarium wird geöffnet | Keine Eingabe | Mehrere Fische schwimmen selbstständig in einer lebendigen Szene. |
| A-02 Neugier auslösen | Aquarium ist sichtbar | Eine Position in der Szene kurz aktivieren | Fische reagieren erkennbar neugierig auf diese Position. |
| A-03 Ausweichen auslösen | Aquarium ist sichtbar | Über einen Bereich der Szene ziehen | Nahe Fische weichen sichtbar aus. |
| A-04 Weiteren Fisch entdecken | Aquarium ist sichtbar | Eine Position in der Szene doppelt kurz aktivieren | Ein weiterer zufälliger Fisch erscheint sichtbar in der Szene. |
| A-05 Füttern | Aquarium ist sichtbar | Die beschriftete Fütterungsaktion aktivieren | Futter erscheint, sinkt sichtbar und mindestens ein Fisch frisst es erkennbar. |

Die Szenenabläufe A-02 bis A-04 stehen auf Touch-Geräten ebenso zur Verfügung wie mit Maus oder Trackpad. Bei überlappenden Eingaben hat eine laufende Fütterungsreaktion Vorrang vor Neugier; Ausweichen bleibt für unmittelbar nahe Fische sichtbar. Diese Regel vermeidet widersprüchliche Reaktionen, ohne neue Funktionen einzuführen.

## Ansichten und Verhalten

| Ansicht | Zweck und dargestellte Inhalte | Aktionen | Erwartete Reaktion |
|---|---|---|---|
| V-01 Aquarium | Unterwasserumgebung mit mehreren Fischen, Pflanzen, Luftblasen, Schwebepartikeln und sichtbarer Fütterungsaktion | Beobachten, Szene aktivieren, über die Szene ziehen, doppelt aktivieren, Fütterungsaktion auslösen | Die Szene bleibt sichtbar lebendig; die jeweilige Fischreaktion ist vom Nutzer erkennbar. |

## Zustände und Fehlersituationen

| Zustand | Sichtbares Verhalten | Fortsetzung |
|---|---|---|
| Initial | Beim Öffnen ist die Aquariumszene mit mehreren Fischen sichtbar. | Beobachten oder direkt interagieren. |
| Ruhig | Fische schwimmen selbstständig; Umgebungsbewegung bleibt dezent. | Jede Kerninteraktion ist möglich. |
| Neugier | Nach A-02 bewegen sich reagierende Fische erkennbar zur aktivierten Position. | Anschließend Rückkehr zum ruhigen Schwimmen; Füttern oder Ausweichen ist weiterhin möglich. |
| Ausweichen | Nach A-03 bewegen sich nahe Fische sichtbar vom gezogenen Bereich weg. | Nach dem Ausweichen Rückkehr zum ruhigen Schwimmen. |
| Fütterung | Sichtbares Futter sinkt; reagierende Fische bewegen sich dorthin und Futter wird weniger. | Nach Verbrauch oder Ende der Reaktion Rückkehr zum ruhigen Schwimmen. |
| Zusätzlicher Fisch | Nach A-04 ist ein weiterer zufälliger Fisch sichtbar. | Die Szene bleibt bedienbar; die Zahl sichtbarer Fische bleibt innerhalb eines später festgelegten, nachvollziehbaren Limits. |
| Nicht unterstützte oder abgebrochene Eingabe | Keine irreführende Teilreaktion; die Szene bleibt sichtbar und bedienbar. | Nutzer kann eine Kerninteraktion erneut ausführen. |
| Sichtbare Fütterungsreaktion läuft | Erneutes Auslösen erzeugt kein unverständliches Übermaß an gleichzeitigem Futter. | Nach Abschluss ist Füttern erneut möglich. |

Ein separater Lade-, Leer-, Offline- oder Berechtigungszustand ist für den freigegebenen Umfang nicht anwendbar: Die Anwendung benötigt keine Nutzerkonten, externen Inhalte oder Geräteberechtigungen.

## Berechtigungen

Keine Berechtigungen erforderlich. Die Anwendung fragt weder Standort, Kamera, Mikrofon noch Benachrichtigungen an. Bei verweigerter oder nicht verfügbarer Eingabe bleibt die Aquariumszene beobachtbar und die jeweils verfügbaren alternativen Eingabewege bleiben nutzbar.

## Bedienbarkeit und Barrierefreiheit

- Die Fütterungsaktion hat eine eindeutige sichtbare Textbeschriftung und eine programmatisch erkennbare Bezeichnung.
- Die einzige interaktive Bedieneinheit ist per Tastatur erreichbar und in einer logischen Fokusreihenfolge vor der Szeneninteraktion verfügbar.
- Wesentliche Reaktionen werden nicht nur über Farbe unterschieden: Bewegung, Richtung und sichtbares Futter machen sie erkennbar.
- Textliche Bedienelemente bleiben bei vergrößerter Darstellung lesbar und nutzbar.
- Touch, Maus und Trackpad erhalten gleichwertige Wege für Neugier, Ausweichen und das Hinzufügen eines Fischs.
- Sofern die Szeneninteraktion nicht mit Tastatur direkt abbildbar ist, bleibt die Fütterungsaktion als erreichbare Kerninteraktion verfügbar; eine spätere Ausweitung der Tastaturbedienung wird nicht vorausgesetzt.

## Akzeptanzkriterien

| ID | Kriterium |
|---|---|
| AC-F01-01 | Beim Öffnen ist ohne vorherige Auswahl eine eindeutig als Aquarium erkennbare Unterwasseransicht sichtbar. |
| AC-F01-02 | Die Ansicht enthält zugleich Fische und Umgebungsbestandteile, ohne dass eine zusätzliche Ansicht geöffnet werden muss. |
| AC-F02-01 | Beim Beobachten ohne Eingabe bewegen sich mehrere Fische selbstständig. |
| AC-F02-02 | Mindestens zwei sichtbare Fische unterscheiden sich für Nutzer erkennbar in ihrer Bewegung oder ihrem Verhalten. |
| AC-F03-01 | Eine kurze Aktivierung einer Szenenposition löst bei mindestens einem Fisch eine sichtbare Neugierreaktion aus. |
| AC-F03-02 | Ein Ziehen über die Szene löst bei einem nahegelegenen Fisch eine sichtbare Ausweichreaktion aus. |
| AC-F03-03 | Eine doppelte kurze Aktivierung lässt einen weiteren zufälligen Fisch sichtbar erscheinen, solange das festgelegte Szenenlimit nicht erreicht ist. |
| AC-F03-04 | Die drei Szeneninteraktionen sind mit Touch sowie mit Maus oder Trackpad auslösbar. |
| AC-F04-01 | Eine eindeutig beschriftete Fütterungsaktion ist in der Aquariumansicht sichtbar und erreichbar. |
| AC-F04-02 | Nach ihrer Aktivierung ist sinkendes Futter sichtbar; mindestens ein Fisch bewegt sich dazu und das Futter wird sichtbar weniger. |
| AC-F05-01 | In der ruhigen Szene sind langsam aufsteigende Luftblasen, sanft bewegte Pflanzen und dezente Schwebepartikel sichtbar. |
| AC-F05-02 | Die Umgebungsbewegungen verhindern nicht, dass Fische und ihre aktuelle Reaktion unterscheidbar bleiben. |

## Rückverfolgbarkeit zum PRD

| PRD-Funktion | Benutzerabläufe | Ansicht | Akzeptanzkriterien |
|---|---|---|---|
| F-01 | A-01 | V-01 | AC-F01-01, AC-F01-02 |
| F-02 | A-01 | V-01 | AC-F02-01, AC-F02-02 |
| F-03 | A-02, A-03, A-04 | V-01 | AC-F03-01 bis AC-F03-04 |
| F-04 | A-05 | V-01 | AC-F04-01, AC-F04-02 |
| F-05 | A-01 | V-01 | AC-F05-01, AC-F05-02 |

## Offene UX-Entscheidungen

- Das konkrete sichtbare Limit für gleichzeitig vorhandene Fische wird im technischen Plan oder bei der Umsetzung festgelegt; es muss das ruhige, lesbare Erlebnis bewahren.
- Die visuelle Vermittlung der drei Gesten bleibt offen, solange keine Einführung, zusätzliche Ansicht oder nicht im PRD begründete Hilfe entsteht.
- Die genaue Position und Gestaltung der Fütterungsaktion bleibt offen, solange sie dauerhaft sichtbar, eindeutig beschriftet und erreichbar ist.

## Optionale Text-Wireframes

```text
┌──────────────────────────────────────┐
│             Aquarium                 │
│  Blasen      Fisch      Pflanzen     │
│        Schwebepartikel               │
│                                      │
│                 [Füttern]            │
└──────────────────────────────────────┘
```
