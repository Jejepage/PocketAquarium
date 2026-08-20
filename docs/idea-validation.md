# Ideen- und Problemvalidierung

## Status und Freigabe

- Status: Freigegeben
- Freigabe: `Weiterführen`
- Persönlich freigegeben: 2026-08-20 durch den Entwickler
- GitHub-Status: Ergebnis-Commit `11f24b7c076bfde30aa0f75a54bbe31ef64e9dc2` auf `main` veröffentlicht und am 2026-08-20 remote verifiziert
- Integration: direkt auf `main`; Pull Request nicht verwendet
- Stand: 2026-08-20

## Ausgangsidee

PocketAquarium ist ein kleines interaktives Aquarium, das vollständig als eine einzige HTML-Datei bereitgestellt wird. Verschiedene Fische bewegen sich eigenständig durch eine lebendige Unterwasserumgebung und reagieren auf Tippen, Ziehen und Füttern. Ergänzende Animationen wie Luftblasen, Pflanzenbewegungen und Schwebepartikel sollen Ruhe und räumliche Tiefe erzeugen. Weitere spielerische Elemente sind ein dem Finger folgender Fisch, das Erzeugen neuer Fische per Doppeltipp, ein gelegentlich vorbeischwimmender großer Hintergrundfisch und optional ein dunkler Nachtmodus mit leicht leuchtenden Fischen.

## Problem

Kurze Pausen am Bildschirm bieten oft wenig Raum für spielerisches Entdecken ohne Leistungsdruck: Viele digitale Angebote verlangen Ziele, Fortschritt oder fortlaufende Entscheidungen. Gesucht wird eine sofort verständliche, lebendige Beschäftigung, die ohne Anmeldung oder Erklärung funktioniert und durch überraschende Reaktionen zum Ausprobieren einlädt.

## Zielgruppe und Nutzungssituation

Die Zielgruppe ist ein allgemeines Publikum, das auf Smartphone, Tablet oder Computer für wenige Minuten ein zugängliches, verspieltes Entdeckungserlebnis sucht. Kinder werden nicht als eigene Hauptzielgruppe behandelt; die Anwendung bleibt dennoch ohne ungeeignete Inhalte allgemein zugänglich.

Typische Nutzungssituationen sind kurze Wartezeiten, eine kleine mentale Pause, das beiläufige Beobachten des Aquariums oder das gemeinsame Entdecken der Fischreaktionen. Die Anwendung soll ohne Einführung direkt verständlich sein.

## Bisheriger Lösungsweg

Nutzer greifen heute vermutlich auf Aquarium-Videos, Bildschirmschoner, einfache Webspielzeuge oder kleine Gelegenheitsspiele zurück. Videos und Bildschirmschoner sind zwar ruhig, reagieren aber nicht auf den Nutzer. Spiele bieten Interaktion, bringen jedoch häufig Ziele, Regeln, Werbung oder Fortschrittsdruck mit sich.

Diese Einschätzung ist nicht durch Nutzerbefragungen oder Marktdaten bestätigt.

## Zentraler Nutzen

PocketAquarium bietet innerhalb weniger Sekunden ein verspieltes Entdeckungserlebnis: Der Nutzer kann beobachten, Gesten ausprobieren und sichtbare, überraschende Reaktionen in einer lebendigen Unterwasserwelt auslösen. Der erkennbare Vorteil liegt in der Verbindung aus beiläufigem Beobachten und unmittelbarer, druckfreier Interaktion.

Die einzelne HTML-Datei unterstützt zusätzlich einen unkomplizierten Zugang und eine einfache Weitergabe. Dieser Lieferaspekt ist jedoch kein Ersatz für einen überzeugenden Nutzungseffekt.

## Kleinstmögliche sinnvolle Version

Die kleinste eigenständig nützliche Version umfasst:

- eine klar erkennbare Aquariumsszene;
- mehrere Fische mit kleinen sichtbaren Unterschieden in Bewegung und Verhalten;
- selbstständiges Schwimmen ohne Eingabe;
- Tippen auf eine Stelle, worauf Fische neugierig dorthin schwimmen;
- Ziehen über die Szene, worauf nahe Fische ausweichen;
- eine kleine sichtbare Füttern-Schaltfläche, die sinkende Partikel erzeugt, zu denen Fische schwimmen und die sie sichtbar fressen;
- langsam aufsteigende Luftblasen;
- sanft bewegte Pflanzen und dezente Schwebepartikel;
- Doppeltippen, um einen weiteren zufälligen Fisch erscheinen zu lassen;
- verständliches Verhalten auf Touch-Geräten sowie eine gleichwertige Bedienmöglichkeit mit Maus oder Trackpad.

Diese Version trägt den zentralen Nutzen bereits: Sie ist sowohl beobachtbar als auch unmittelbar interaktiv und besitzt mit Neugier, Flucht und Fressen drei klar unterscheidbare Fischreaktionen.

## Bewusste Nicht-Ziele

Für die erste sinnvolle Version werden nicht benötigt:

- Nachtmodus und leuchtende Fische;
- gelegentlich vorbeischwimmender großer Hintergrundfisch;
- ein dauerhaft ausgewählter Fisch, der dem Finger folgt;
- Fischpflege, Wachstum, Gesundheit, Zucht oder Tod;
- Aufgaben, Punkte, Fortschritt, Währungen oder Freischaltungen;
- Konten, Speicherung, Bestenlisten oder soziale Funktionen;
- Werbung, Käufe oder Benachrichtigungen;
- umfangreiche Einstellungen, Artenkataloge oder realistische Aquariumsimulation;
- Ton oder Musik.

Der Finger-Folgemodus kann später ergänzt werden. Für den Mindestumfang überschneidet er sich mit der bereits vorgesehenen Neugierreaktion auf Tippen und würde die Gestenlogik unnötig erweitern.

## Annahmen

- Eine verspielte, druckfreie Interaktion ist der wichtigste Nutzen.
- Kurze Nutzungssitzungen von wenigen Sekunden bis einigen Minuten reichen aus.
- Sichtbar unterschiedliche Verhaltensreaktionen sind wichtiger als eine große Zahl an Fischarten.
- Nutzer verstehen Tippen, Ziehen und Doppeltippen ohne längere Anleitung oder entdecken sie spielerisch.
- Die Beschränkung auf eine einzelne HTML-Datei ist verbindlich und mit dem gewünschten Kernerlebnis vereinbar.
- Maus- und Trackpad-Nutzer sollen die wesentlichen Touch-Interaktionen ebenfalls auslösen können.
- Das Erlebnis benötigt für die erste Version weder Ton noch gespeicherten Fortschritt.

## Offene Fragen

Keine offenen Fragen, die die Empfehlung oder den Mindestumfang dieser Phase wesentlich verändern.

Entscheidungen des Entwicklers vom 2026-08-20:

- Schwerpunkt ist ein verspieltes Entdeckungserlebnis.
- Zielgruppe ist ein allgemeines Publikum.
- Für das Füttern ist eine sichtbare Schaltfläche erlaubt.

## Risiken und technische Unsicherheiten

- Zu viele Fische, Partikel und gleichzeitige Reaktionen können die gewünschte Ruhe in visuelle Unordnung verwandeln.
- Neugier, Flucht, Fressen und Fingerfolgen können sich gegenseitig widersprechen; ohne klare Prioritäten wirkt das Verhalten sprunghaft statt lebendig.
- Doppeltippen kann mit Vergrößerungsgesten oder anderen Browserinteraktionen kollidieren und muss in der vorgesehenen Nutzungssituation verständlich bleiben.
- Eine unbegrenzte Erzeugung neuer Fische kann Darstellung und Reaktionsfähigkeit verschlechtern; ein nachvollziehbares Limit dürfte erforderlich sein.
- Touch-, Maus- und Trackpad-Eingaben unterscheiden sich. Gleichwertige Bedienbarkeit ist eine wesentliche, noch zu prüfende Produktanforderung.
- Die Einzeldatei-Vorgabe begrenzt Umfang und Medienvielfalt. Das ist für eine kleine erste Version voraussichtlich akzeptabel, muss aber später praktisch bestätigt werden.
- Ohne echte Nutzerbeobachtung bleibt offen, ob das Erlebnis länger als einen kurzen Neuheitseffekt trägt.

## Empfehlung

**Weiterführen — vom Entwickler am 2026-08-20 persönlich bestätigt.** Die Idee verbindet einen klar verständlichen spielerischen Nutzen mit wenigen direkt erlebbaren Interaktionen und lässt sich sinnvoll auf einen kleinen ersten Umfang reduzieren. Eine eigene Anwendung hat gegenüber einem passiven Aquarium-Video einen erkennbaren Vorteil, weil Fische auf Berührung reagieren, ohne daraus ein leistungsorientiertes Spiel zu machen.

Die Empfehlung gilt unter der Bedingung, dass die erste Version auf Ruhe, Lesbarkeit und drei Kernreaktionen beschränkt bleibt. Optionale Atmosphäre und zusätzliche Verhaltensmodi sollten erst nach einem überzeugenden Kern ergänzt werden.

## Quellen

Keine externe Recherche erforderlich.
