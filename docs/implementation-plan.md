# Implementierungsplan

## Status und Freigabe

- Status: Freigegeben
- Freigabe: persönlich am 2026-08-20 durch den Entwickler
- GitHub-Status: Ergebnis-Commit `55dfe1f794e5b4e63888248cfe5e55c59a11899b` auf `main` veröffentlicht und am 2026-08-20 remote verifiziert; Abschlussdokumentation folgt im nachgelagerten Status-Commit.
- Grundlage: die freigegebenen Produkt-, Funktions-/UI- und technischen Pläne vom 2026-08-20
- Lieferform: genau eine eigenständig lauffähige `index.html` ohne Abhängigkeiten, Laufzeit-Netzwerk, Speicherung oder Berechtigungen; Veröffentlichung im Release über GitHub Pages aus `main` und `/ (root)`

## Planungsgrundlagen und Einschränkungen

Die vier Etappen liefern jeweils einen direkt im Browser prüfbaren Zwischenstand. Sie folgen dem Wertstrom: zuerst eine ruhige beobachtbare Szene, dann ihre direkten Gesten, anschließend Fütterung und zuletzt Robustheit, Zugänglichkeit und vollständige Regression. Der anfängliche Bestand beträgt drei, das feste Limit sechs Fische. Füttern ist die einzige erforderliche Tastaturbedienung. Es werden weder Frameworks noch Paketinstallationen eingeführt. Der nachfolgende Release veröffentlicht die fertig geprüfte `index.html` über GitHub Pages.

## Etappenübersicht

| Etappe | Ziel und sichtbares Ergebnis | Enthaltene Anforderungen | Abhängigkeiten |
|---|---|---|---|
| 01 – Lebendige Grundszene | Beim Öffnen ist eine ruhige, responsive Aquariumansicht mit drei unterschiedlich schwimmenden Fischen und begrenzter Umgebungsbewegung sichtbar. | F-01, F-02, F-05; AC-F01-01, AC-F01-02, AC-F02-01, AC-F02-02, AC-F05-01, AC-F05-02 | Keine |
| 02 – Szenengesten | Kurze Aktivierung, Ziehen und doppelte Aktivierung lösen sichtbar Neugier, Ausweichen und bis zum Limit neue Fische aus. | F-03; AC-F03-01 bis AC-F03-04 | Etappe 01 |
| 03 – Sichtbares Füttern | Die Schaltfläche **Füttern** erzeugt sinkendes Futter; ein Fisch erreicht es und die Menge nimmt sichtbar ab. | F-04; AC-F04-01, AC-F04-02 | Etappen 01–02 |
| 04 – Robuste Übergabe | Die vollständige Szene bleibt auf Touch und Desktop bei Randfällen bedienbar und alle Kriterien sind als Gesamtfluss nachgewiesen. | Regression und Qualität für F-01 bis F-05, Q-01 bis Q-07, E-01 bis E-06 | Etappen 01–03 |

## Reihenfolge und Abhängigkeiten

Etappe 01 etabliert Canvas, Animationsschleife, Größenanpassung und die lesbare Grunddichte; darauf bauen alle sichtbaren Reaktionen auf. Etappe 02 ergänzt Pointer Events und verändert nur vorhandene Fische. Etappe 03 setzt auf diese Zustandssteuerung auf und gibt Futterzuständen den festgelegten Vorrang. Etappe 04 darf nur Fehlerkorrekturen und die im technischen Plan beschriebenen robusten Fallbehandlungen ergänzen; sie erweitert nicht den Produktumfang. Nach jeder Etappe bleiben die HTML-Datei und ihre Dokumentation direkt prüfbar.

## Anforderungs- und Kriterienabdeckung

| Kennung | Umsetzung | Primärer Prüfweg |
|---|---|---|
| F-01; AC-F01-01, AC-F01-02 | Etappe 01 | Browserstart auf kleinem Touch- und Desktop-Viewport |
| F-02; AC-F02-01, AC-F02-02 | Etappe 01 | Mehrminütige Beobachtung ohne Eingabe |
| F-03; AC-F03-01 bis AC-F03-04 | Etappe 02 | Touch- sowie Maus/Trackpad-Smoke-Test für Tippen/Klicken, Ziehen und Doppeltippen/-klicken |
| F-04; AC-F04-01, AC-F04-02 | Etappe 03 | Tastatur-/Fokusprüfung und sichtbarer Fütterungsablauf |
| F-05; AC-F05-01, AC-F05-02 | Etappe 01 | Visuelle Prüfung der begrenzten Effekte und Lesbarkeit |
| Q-01 bis Q-07; E-01 bis E-06 | Etappe 04 (Regression) | Vollständiger Browser-, Eingabe-, Zugänglichkeits- und statischer Nachweis |

## Übergreifende Teststrategie

Jede Etappe prüft die zugehörigen Kriterien manuell in mindestens einem aktuellen Desktop-Browser; bei Eingabe- und Layoutänderungen zusätzlich in einem Touch-Viewport. Statische Kontrollen prüfen HTML-Syntax, das Fehlen externer URLs, Abhängigkeiten, Speicherung und Geheimnisse. Es gibt keine verpflichtende Testbibliothek: Automatisierung wird nur ergänzt, wenn sie ohne neue Produktions- oder Build-Abhängigkeit lokal verfügbar ist. Die unabhängige Prüfphase testet jede Umsetzungsetappe gegen ihre Etappendatei und dokumentiert das Ergebnis separat.

## Übergreifende Risiken und Aufgaben

- Gestenschwellen für kurz, doppelt und Ziehen müssen auf Touch und Desktop erprobt werden; die Kriterien, nicht die konkreten Millisekundenwerte, sind verbindlich.
- Bei Größenwechsel, `pointercancel`, Fokusverlust und raschen Wiederholungen dürfen keine defekten Zustände verbleiben.
- Die Animationsmenge bleibt begrenzt, damit Effekte keine Reaktion verdecken.
- Die ausgelieferte Datei enthält keine Entwicklungsprotokollierung, keine Netzwerkanfragen und keine persistente Speicherung.
- Für die zugesagte Evergreen-Kompatibilität ist die vollständige manuelle Browserprüfung vor Release erforderlich.

## Bewusste Verschiebungen und Nicht-Ziele

Nachtmodus, leuchtende oder große Hintergrundfische, Finger-Folgemodus, Pflege- und Fortschrittsmechaniken, Audio, Konten, Analyse und externe Inhalte bleiben außerhalb aller Etappen. GitHub Pages ist als Hostingentscheidung getroffen; seine Aktivierung und die abschließende URL-Prüfung erfolgen ausschließlich in der Release-Phase.

## Offene Planungsentscheidungen

Keine. Konkrete konservative Gestenschwellen und Farb-/Bewegungsparameter sind reversible Implementierungsdetails innerhalb der freigegebenen Grenzen.
