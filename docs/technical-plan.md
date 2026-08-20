# Technischer Plan

## Status und Freigabe

- Status: Freigegeben.
- Freigabe: persönlich am 2026-08-20 durch den Entwickler; OD-01 mit Option A bestätigt.
- Grundlage: die freigegebenen `docs/product-requirements.md` und `docs/functional-plan.md`, jeweils vom 2026-08-20.
- Abruf technischer Quellen: 2026-08-20.

## Verbindliche Grundlagen und Einschränkungen

- Lieferumfang ist genau eine direkt ausführbare HTML-Datei; keine Build-Ausgabe, kein Projektgerüst und keine Produktfunktion gehören zu dieser Planungsphase.
- Eine sofort nutzbare einzelne Aquariumansicht muss F-01 bis F-05 erfüllen. Sie arbeitet ohne Konto, personenbezogene Eingaben, Netzwerkanfrage, Berechtigung, Audio, Speicherung oder externe Dienste.
- Touch sowie Maus und Trackpad lösen die drei Szenengesten gleichwertig aus. Die sichtbare, per Tastatur erreichbare Schaltfläche **Füttern** bleibt die einzige notwendige fokussierbare Bedienung.
- Der Startbestand besteht aus drei Fischen; höchstens sechs Fische sind zugleich sichtbar. Das Limit hält A-04 nachvollziehbar und die Szene lesbar. Es ist eine reversible Umsetzungsdetailentscheidung.

## Zusammenfassung der technischen Entscheidungen

Eine einzige HTML-Datei enthält semantisches HTML für die Fütterung, CSS für Layout und ruhige Effekte sowie eingebettetes, natives JavaScript. Ein Canvas-2D-Element zeichnet die Aquariumwelt; `requestAnimationFrame` treibt eine zeitdelta-basierte Simulation an. Pointer Events vereinheitlichen Touch-, Maus- und Trackpad-Eingaben. Alle Laufzeitdaten liegen nur im Arbeitsspeicher und werden beim Neuladen verworfen. Externe Abhängigkeiten, APIs, Dienste, Rechte und laufende Kosten gibt es nicht.

## Entscheidungsprotokoll

| ID | Entscheidung | Gewählte Option | Geprüfte Alternativen | Entschieden durch | Begründung und Folgen |
|---|---|---|---|---|---|
| T-01 | Auslieferungsform | Eine eigenständige HTML-Datei mit eingebettetem CSS und JavaScript | Mehrdateien-Projekt, Framework-Bundle | Produktvorgabe | Erfüllt die verbindliche Lieferform, ist ohne Installation startbar und minimiert Betrieb und Wartung. |
| T-02 | Szenendarstellung | Canvas 2D plus HTML-`button` für Füttern | Reines DOM/CSS, SVG | Technischer Plan | Canvas ist für wenige, kontinuierlich bewegte Objekte und Zeicheneffekte ausreichend; der native Button liefert sichtbaren Text, Fokus und programmatische Bezeichnung. |
| T-03 | Eingabemodell | Pointer Events mit `pointerdown`, `pointermove`, `pointerup` und `pointercancel` | Getrennte Touch- und Mausbehandlung | Technischer Plan | Ein Hardware-unabhängiges Modell unterstützt die geforderten Eingabearten. Ziehen verwendet Pointer Capture; abgebrochene Eingaben setzen den Gestenzustand ohne Teilreaktion zurück. |
| T-04 | Bewegungssteuerung | Zeitdelta-basierte Simulationsschleife mit `requestAnimationFrame` | CSS-Animationen je Fisch, Timer-Intervalle | Technischer Plan | Zustände, Futter und Reaktionen bleiben in einer einfachen Schleife synchron und mit unterschiedlichen Geschwindigkeiten darstellbar. |
| T-05 | Laufzeitdaten | Ausschließlich flüchtiger Arbeitsspeicher | `localStorage`, Server/Cloud-Synchronisation | Technischer Plan | Der freigegebene Umfang hat keinen Fortschritt oder Einstellungsbedarf; damit fallen Datenspeicherung, Migration, Konto und Netzwerk weg. |
| T-06 | Fischlimit | Drei Startfische, maximal sechs sichtbare Fische | Kein Limit, höheres Limit | Technischer Plan | Ermöglicht A-04 mehrfach, begrenzt aber gleichzeitige Bewegung und sichert Q-04 sowie AC-F05-02. |
| T-07 | Browser-Kompatibilität | Aktuelle stabile Evergreen-Versionen von Safari, Chrome, Edge und Firefox (Option A) | Aktuelle plus vorherige Hauptversion, feste Mindestversionen | Entwickler, 2026-08-20 | Begrenzt den wiederkehrenden Prüfaufwand der kleinen V1; ältere Browser erhalten keine Kompatibilitätszusage. |

## Zielplattform und Kompatibilität

Ziel sind Touch-Geräte und Desktop-Computer in den jeweils aktuellen stabilen Evergreen-Versionen von Safari, Chrome, Edge und Firefox (OD-01, Option A). Erforderlich sind Canvas 2D, ECMAScript-Module sind **nicht** erforderlich, Pointer Events und `requestAnimationFrame`. Bei fehlender Fähigkeit zeigt die Datei eine kurze, sichtbare Hinweisnachricht statt einer unbedienbaren leeren Szene. Ältere Browser und Systemversionen sind nicht zugesichert.

## Sprache, Framework und Toolchain

HTML5, CSS und modernes browsernatives JavaScript (ES2015+-Syntax, ohne Transpilierung), kein Framework und keine Produktionsabhängigkeit. Für die lokale Prüfung genügt ein moderner Browser; optional dient ein statischer lokaler Webserver nur der Testausführung. Eine Toolchain, Paketverwaltung oder Installation ist nicht erforderlich.

## Architekturprinzip und Projektstruktur

Die Ein-Datei-Struktur trennt die Abschnitte logisch, nicht in zusätzliche Dateien:

| Bereich | Verantwortung |
|---|---|
| HTML | Canvas, beschriftete Fütterungsschaltfläche, kurze Fallback-Meldung. |
| CSS | Vollflächiges responsives Layout, Kontrast/Fokus der Schaltfläche, `touch-action` für die Szenenfläche. |
| Konfiguration | Konstante Größen, Fischlimit, Bewegungs- und Effektgrenzen. |
| Simulationszustand | Fische, Futterpartikel, Umweltpartikel, aktuelle Reaktionsziele und Gestenzustand. |
| Eingabe | Positionsumrechnung und Erkennung von kurzer, doppelter und ziehender Aktivierung. |
| Simulation und Rendern | Zustandsübergänge, Begrenzung der Bewegungsmenge und Zeichnung je Animationsbild. |

Keine Klassenhierarchie, kein globaler Ereignisbus und kein Backend: wenige Datenobjekte und klar abgegrenzte Funktionen sind für den Umfang wartbar genug.

## Datenmodell

Alle Werte sind rein fachlich-visuelle Laufzeitdaten:

| Objekt | Wesentliche Felder | Lebenszyklus |
|---|---|---|
| `Fish` | ID, Typ/Palette, Position, Geschwindigkeit, Ziel, Verhalten (`idle`, `curious`, `fleeing`, `feeding`) | Drei beim Start; durch Doppeltaktivierung bis sechs; nur während der Sitzung. |
| `Food` | Position, Sinkgeschwindigkeit, verbleibende Menge | Durch Füttern erzeugt; sinkt und wird beim Fressen reduziert; danach entfernt. |
| `AmbientParticle` / `Bubble` / `Plant` | Position und Phasen-/Bewegungswert | Beim Start erzeugt; am Rand erneut verwendet bzw. zeitlich fortgeschrieben. |
| `Gesture` | Startpunkt, letzte Position, Dauer, Doppelaktivierungszeitpunkt | Pro Pointer-Eingabe; bei `pointerup` ausgewertet oder bei `pointercancel` verworfen. |

Die Fütterung ist exklusiv, solange sichtbares Futter vorhanden ist. In dieser Zeit erhält ein Futterziel Vorrang vor Neugier; ein naher Ziehimpuls darf weiterhin ein sichtbares Ausweichen auslösen, danach kehrt der Fisch zu seinem Futterziel zurück.

## Speicherung, Synchronisation und Migration

Nicht erforderlich. Alle Daten werden ausschließlich im Arbeitsspeicher gehalten und beim Schließen oder Neuladen verworfen. Damit existieren keine zu löschenden persistenten Daten, keine Synchronisation und keine Migration. `localStorage` wird nicht verwendet.

## Externe APIs und Dienste

Nicht erforderlich. Die Anwendung lädt keine Bilder, Schriftarten, Skripte, Analysewerkzeuge oder sonstigen Inhalte aus dem Netz und ruft keine API auf. Sämtliche Szenenelemente werden programmatisch gezeichnet.

## Anmeldung, Käufe und Berechtigungen

Nicht erforderlich: keine Anmeldung, Käufe, Benachrichtigungen oder Geräteberechtigungen. Die Datei fragt weder Standort noch Kamera oder Mikrofon ab.

## Fehlerbehandlung und Protokollierung

- Kann Canvas oder Pointer Events nicht genutzt werden, bleibt die Fütterungsschaltfläche sichtbar und eine kurze Hinweisnachricht benennt die fehlende Browserunterstützung.
- `pointercancel`, Fokusverlust und Größenänderungen löschen unvollständige Gesten sicher; bereits existierende Szeneobjekte bleiben intakt.
- Ein deaktiviertes Füttern während einer laufenden Fütterung verhindert konkurrierendes Futter; nach Ende wird die Schaltfläche wieder aktiviert.
- Es gibt keine Produktprotokollierung und keine Telemetrie. Lokale Entwicklungsdiagnosen dürfen nur in einer bewussten Entwicklungsvariante erscheinen und nicht in der ausgelieferten Datei verbleiben.

## Datenschutz und Sicherheit

Die erste Version verarbeitet keine personenbezogenen Daten, setzt keine Cookies, speichert nichts und überträgt nichts. Dadurch sind keine Geheimnisse, Tokens oder fremden Inhalte im Repository nötig. Der Verzicht auf externe Ressourcen verringert Lieferketten- und Trackingrisiken. Eingabekoordinaten werden nur für die aktuelle Interaktion genutzt und nicht aufgezeichnet.

## Teststrategie

| Ebene | Prüfung | Abgedeckte Anforderungen |
|---|---|---|
| Statisch | HTML-Struktur, keine externen URLs/Abhängigkeiten, keine Geheimnisse, manuelle Codeprüfung der Zustandsgrenzen | T-01, T-05, Q-06 |
| Verhalten im Browser | Öffnen, Beobachten, Klick/Tippen, Ziehen, Doppelklick/-tippen, Füttern, Wiederholung bis Fischlimit | F-01 bis F-05, E-01 bis E-06, AC-F01-01 bis AC-F05-02 |
| Eingabe/Barrierefreiheit | Touch und Maus/Trackpad; Tastaturfokus, sichtbarer Fokus, Buttonname und Zoom | Q-03, Q-07, AC-F03-04, AC-F04-01 |
| Robustheit | Abgebrochene Geste, rasche Wiederholungen, Füttern während Fütterung, Größenwechsel, längere Beobachtung | Q-04, Q-05 und Zustände des UI-Plans |
| Manuelle visuelle Prüfung | Auf kleinem Touch-Viewport und Desktop: Lesbarkeit, unterscheidbare Reaktionen, ruhige Effekte | Q-01, Q-02, Q-04, E-05 |

Automatisierte Browser-Tests sind für die einzelne statische Datei optional; der spätere Implementierungsplan muss einen tatsächlich lokal verfügbaren Prüfweg festlegen, ohne eine neue Abhängigkeit vorauszusetzen.

## Build, Konfiguration und Veröffentlichung

Kein Build-Schritt: die HTML-Datei ist das Artefakt. Vor Veröffentlichung wird sie über einen statischen HTTPS-Host oder als direkte Datei gemäß der gewählten Browsergrenze geprüft. Ein Hostinganbieter ist noch nicht ausgewählt und für die technische Planung nicht nötig; die Veröffentlichung darf keine Drittanbieter-Skripte ergänzen. Die finale Datei wird versionskontrolliert ausgeliefert, mit Browser-Smoke-Tests vor dem Release.

## Abhängigkeiten, Lizenzen und laufende Kosten

Keine Laufzeit- oder Build-Abhängigkeiten, daher keine zusätzlichen Lizenzen oder laufenden Kosten. Hosting ist für die lokale, direkt ausführbare Lieferform nicht erforderlich; falls später öffentlich gehostet wird, ist Anbieter, Preis und Datenschutzeinfluss vorab separat zu entscheiden.

## Risiken und bewusste Kompromisse

- Eine einzelne Datei wird bei späteren großen Erweiterungen unübersichtlicher; für die freigegebene V1 überwiegt ihre einfache Verteilung.
- Canvas bietet keine semantische Einzelbeschreibung der Fische. Die erforderliche Interaktion bleibt deshalb über den nativen Fütterungsbutton zugänglich; Szenengesten werden nicht als vollständige Tastaturfunktion versprochen.
- Die präzise Erkennung von Doppeltipp und Ziehen benötigt konservative Zeit- und Wegeschwellen. Diese Werte werden in der Implementierung getestet und dürfen nicht die beobachtbaren Akzeptanzkriterien ändern.
- Animationen werden bei inaktiver Browser-Registerkarte nicht als Echtzeitgarantie behandelt; die delta-basierte Simulation begrenzt große Zeitsprünge beim Wiederkehren.

## Rückverfolgbarkeit zu Anforderungen

| Anforderung | Technische Grundlage | Vorgesehene Prüfung |
|---|---|---|
| F-01 / AC-F01-01 bis -02 | Canvas-Szene, programmgenerierte Umweltobjekte, keine Startnavigation | Browser-Startprüfung |
| F-02 / AC-F02-01 bis -02 | `Fish`-Objekte mit unterschiedlichen Parametern und Idle-Bewegung | Beobachtung ohne Eingabe |
| F-03 / AC-F03-01 bis -04 | Pointer-Event-Gestenerkennung, Reaktionsziele, Limit sechs | Touch- und Desktop-Gestenprüfung |
| F-04 / AC-F04-01 bis -02 | Nativer Button, `Food`-Objekte, exklusiver Fütterungszustand | Fokus- und Fütterungsprüfung |
| F-05 / AC-F05-01 bis -02 | Begrenzte Umgebungsobjekte und zentrales Renderbudget | Visuelle Prüfung auf kleinen und großen Viewports |
| Q-05 / nicht unterstützte Eingabe | `pointercancel`-Behandlung, Zustandsbereinigung, keine Netzabhängigkeit | Abbruch- und Wiederholungsprüfung |
| Q-06 / E-06 | Keine Speicherung, keine Anfragen, keine externen Dienste | Statische Prüfung und Netzwerkinspektion |

## Offene technische Entscheidungen

Keine. OD-01 wurde am 2026-08-20 persönlich mit Option A entschieden: aktuelle stabile Evergreen-Versionen von Safari, Chrome, Edge und Firefox.

## Quellen

- [MDN: Pointer Events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events), abgerufen am 2026-08-20: einheitliches Ereignismodell für Maus, Stift und Touch sowie Unterstützung für Pointer Capture.
- [MDN: Canvas API](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API), abgerufen am 2026-08-20: browsernative 2D-Zeichenoberfläche.
- [MDN: `requestAnimationFrame`](https://developer.mozilla.org/en-US/docs/Web/API/Window/requestAnimationFrame), abgerufen am 2026-08-20: browsergesteuerte Animationsrückrufe.
- [MDN: `localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage), abgerufen am 2026-08-20: als geprüfte, aber bewusst nicht verwendete persistente Speicheroption.
