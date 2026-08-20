# Produktanforderungen

## Status und Freigabe

- Status: Freigegeben
- Freigabe: persönlich am 2026-08-20 durch den Entwickler
- Grundlage: freigegebene `docs/idea-validation.md` vom 2026-08-20
- Stand: 2026-08-20

## Produktvision

PocketAquarium verwandelt eine kurze Pause in ein sofort zugängliches, verspieltes Entdeckungserlebnis. Nutzer können eine lebendige Unterwasserwelt beobachten und mit wenigen Gesten sichtbare, unterschiedliche Fischreaktionen auslösen – ohne Ziele, Leistungsdruck oder Einführung.

## Problem und Zielgruppe

In kurzen Bildschirm-Pausen fehlt oft eine spielerische Beschäftigung, die ohne Anmeldung, Erklärung und Fortschrittsdruck unmittelbar verständlich ist. Aquarium-Videos sind passiv, während viele Spiele Regeln und Ziele verlangen.

Die erste Version richtet sich an ein allgemeines Publikum auf Touch-Geräten und Desktop-Computern. Sie soll für kurze Wartezeiten, eine kleine mentale Pause, beiläufiges Beobachten oder gemeinsames Entdecken geeignet sein.

## Hauptanwendungsfall

Ein Nutzer öffnet PocketAquarium, erkennt ohne Einführung eine lebendige Aquariumszene, beobachtet selbstständig schwimmende Fische und probiert Interaktionen aus. Das Aquarium antwortet sichtbar mit Neugier, Ausweichen oder Fressen, sodass der Nutzer in derselben kurzen Sitzung sowohl Ruhe als auch spielerische Entdeckung erlebt.

## Benutzerbedürfnisse

- **B-01 – Sofortiger Zugang:** Ich möchte ohne Anmeldung oder Erklärung direkt etwas Lebendiges beobachten können.
- **B-02 – Sichtbare Reaktion:** Ich möchte durch einfache Eingaben erkennbare, unterschiedliche Reaktionen auslösen können.
- **B-03 – Druckfreies Erkunden:** Ich möchte frei ausprobieren können, ohne Aufgaben, Punkte oder negative Folgen.
- **B-04 – Ruhige Atmosphäre:** Ich möchte eine Szene erleben, die lebendig wirkt, aber nicht visuell überfordert.
- **B-05 – Gleichwertige Bedienung:** Ich möchte die wesentlichen Interaktionen sowohl mit Touch als auch mit Maus oder Trackpad nutzen können.

## Umfang der ersten Version

| ID | Kernfunktion | Zugeordnetes Benutzerbedürfnis | Priorität |
|---|---|---|---|
| F-01 | Eine sofort erkennbare, lebendige Aquariumszene bereitstellen. | B-01, B-04 | Muss |
| F-02 | Mehrere Fische zeigen lassen, die sich selbstständig und sichtbar unterschiedlich bewegen. | B-01, B-04 | Muss |
| F-03 | Direkte Szeneninteraktionen ermöglichen, die bei Fischen klar unterscheidbar Neugier, Ausweichen und das Erscheinen eines weiteren zufälligen Fischs auslösen. | B-02, B-03, B-05 | Muss |
| F-04 | Eine sichtbare Fütterungsmöglichkeit bereitstellen; Fische reagieren auf sichtbares Futter und fressen es erkennbar. | B-02, B-03 | Muss |
| F-05 | Dezente Umgebungsbewegungen bereitstellen, darunter aufsteigende Luftblasen, sanft bewegte Pflanzen und Schwebepartikel. | B-04 | Muss |

Der verbindliche Lieferumfang bleibt eine einzelne eigenständig lauffähige HTML-Datei. Dies ist eine Produktvorgabe für die Weitergabe, keine Vorentscheidung über die technische Umsetzung der Funktionen.

## Bewusste Nicht-Ziele

- Nachtmodus oder leuchtende Fische
- Großer vorbeischwimmender Hintergrundfisch
- Dauerhaft ausgewählter, dem Finger folgender Fisch
- Fischpflege, Wachstum, Gesundheit, Zucht oder Tod
- Aufgaben, Punkte, Fortschritt, Währungen oder Freischaltungen
- Konten, gespeicherter Fortschritt, Bestenlisten oder soziale Funktionen
- Werbung, Käufe oder Benachrichtigungen
- Umfangreiche Einstellungen, Artenkataloge oder realistische Aquariumsimulation
- Ton oder Musik

## Mögliche spätere Funktionen

- Optionaler Nachtmodus mit leicht leuchtenden Fischen
- Gelegentlicher großer Hintergrundfisch
- Finger-Folgemodus für einen ausgewählten Fisch
- Zusätzliche Fischarten oder weitere sichtbare Verhaltensvarianten, sofern die ruhige Szene erhalten bleibt

## Qualitätsanforderungen

- **Q-01 – Verständlichkeit:** Die Aquariumszene und ihre grundlegende Interaktivität sind ohne Einführung erkennbar.
- **Q-02 – Reaktionsklarheit:** Neugier, Ausweichen und Fressen sind für Nutzer visuell voneinander unterscheidbar.
- **Q-03 – Bedienbarkeit:** Die wesentlichen Szeneninteraktionen und die Fütterung sind auf Touch-Geräten sowie mit Maus oder Trackpad zugänglich.
- **Q-04 – Ruhe und Lesbarkeit:** Gleichzeitige Bewegungen und Effekte bleiben so dosiert, dass Fische und ihre Reaktionen erkennbar bleiben.
- **Q-05 – Zuverlässigkeit:** Eine übliche Nutzung der vorgesehenen Kerninteraktionen führt nicht zu einem blockierten oder nicht mehr bedienbaren Aquarium.
- **Q-06 – Datenschutz:** Die erste Version erfordert weder Konto noch die Eingabe personenbezogener Daten und kommuniziert keine Nutzerinhalte als Teil des Produkterlebnisses.
- **Q-07 – Allgemeine Zugänglichkeit:** Das Erlebnis enthält keine ungeeigneten Inhalte und seine wesentlichen Funktionen sind nicht ausschließlich an präzise Touch-Eingaben gebunden.

## Erfolgskriterien

- **E-01:** Beim Öffnen ist eine Aquariumszene mit mehreren selbstständig schwimmenden Fischen ohne vorherige Erklärung sichtbar.
- **E-02:** Nutzer können in einer Nutzungssitzung sichtbar eine Neugierreaktion, eine Ausweichreaktion und eine Fressreaktion auslösen.
- **E-03:** Nach einer Fütterung ist Futter sichtbar vorhanden; mindestens ein Fisch bewegt sich dazu und das Futter wird sichtbar weniger.
- **E-04:** Die wesentlichen Szeneninteraktionen lassen sich sowohl mit Touch als auch mit Maus oder Trackpad auslösen.
- **E-05:** Während der vorgesehenen Interaktionen bleiben die relevanten Fische und ihre Reaktion vom Nutzer unterscheidbar.
- **E-06:** Die erste Version verlangt weder Anmeldung noch die Angabe personenbezogener Daten und bietet keine Punkte, Aufgaben oder Fortschrittsmechanik.

## Offene Produktentscheidungen

Keine offenen Produktentscheidungen für die Freigabe dieses PRD-Entwurfs. Die folgenden Umsetzungsgrenzen werden im Funktions- und UI-Plan konkretisiert, ohne den freigegebenen Umfang zu erweitern:

- Wie viele Fische gleichzeitig sinnvoll sichtbar sein sollen und wie ein nachvollziehbares oberes Limit aussieht.
- Wie die gleichwertige Auslösung der drei Szeneninteraktionen mit Touch, Maus und Trackpad konkret vermittelt wird.
- Woran in der Nutzung sichtbar wird, dass ein weiterer zufälliger Fisch erschienen ist.

## Rückverfolgbarkeit

| Kernfunktion | Aussage der Ideenvalidierung | Erfolgskriterium |
|---|---|---|
| F-01 | „eine klar erkennbare Aquariumsszene“ unter „Kleinstmögliche sinnvolle Version“ | E-01 |
| F-02 | „mehrere Fische mit kleinen sichtbaren Unterschieden in Bewegung und Verhalten“ sowie „selbstständiges Schwimmen ohne Eingabe“ | E-01, E-05 |
| F-03 | „Tippen ... neugierig“, „Ziehen ... ausweichen“, „Doppeltippen ... weiteren zufälligen Fisch“ sowie gleichwertige Maus- und Trackpad-Bedienung | E-02, E-04, E-05 |
| F-04 | „kleine sichtbare Füttern-Schaltfläche“; Fische schwimmen zu sinkenden Partikeln und fressen sie sichtbar | E-02, E-03 |
| F-05 | „langsam aufsteigende Luftblasen“, „sanft bewegte Pflanzen“ und „dezente Schwebepartikel“ | E-05 |
