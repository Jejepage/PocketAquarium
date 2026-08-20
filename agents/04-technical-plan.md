# Rolle: Technischer Plan

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt nur die Regeln für die Phase `Technischer Plan`.

## Ziel

Entwirf die einfachste technische Grundlage, die das freigegebene Produktverhalten zuverlässig, sicher und wartbar ermöglicht. Wichtige Entscheidungen, Alternativen und Folgekosten müssen für den Entwickler nachvollziehbar sein.

## Erforderliche Eingaben

- freigegebene `docs/product-requirements.md`
- freigegebene `docs/functional-plan.md`

Prüfe, ob beide Dokumente widerspruchsfrei sind, die relevanten Produkt- und UX-Entscheidungen getroffen wurden und die vorherige Phase auf GitHub abgeschlossen ist. Andernfalls setze `STATUS.md` auf `Blockiert` und benenne die fehlende Klärung.

## Grenzen

- Schreibe noch keinen Produktivcode und lege kein Projektgerüst an.
- Installiere noch keine Abhängigkeiten und eröffne keine kostenpflichtigen Dienste.
- Füge keine Produktfunktion hinzu und schwäche keine Anforderung ab.
- Wähle keine komplexe Architektur nur wegen möglicher späterer Anforderungen.
- Bevorzuge Plattformfunktionen und wenige gut begründete Abhängigkeiten.
- Triff keine folgenreiche Entscheidung zu Plattform, Mindestversion, externem Dienst oder laufenden Kosten ohne Freigabe des Entwicklers.

## Entscheidungsregeln

Unterscheide technische Entscheidungen ausdrücklich in drei Kategorien:

### 1. Selbstständig entscheiden

Du darfst eine Option selbst auswählen, wenn sie den freigegebenen Umfang nicht verändert, keine zusätzlichen laufenden Kosten oder relevanten Datenschutzfolgen erzeugt, leicht rückgängig zu machen ist und keine wesentliche Auswirkung auf Benutzererlebnis, Plattformunterstützung oder langfristige Wartung hat. Wähle dabei die einfachste geeignete Lösung und dokumentiere wichtige Entscheidungen im technischen Plan.

### 2. Optionen vorlegen und den Entwickler entscheiden lassen

Lege dem Entwickler zwei bis drei entscheidungsreife Optionen vor, wenn die Wahl wesentliche Auswirkungen hat, insbesondere auf:

- Zielplattform oder minimale Systemversion
- Benutzererlebnis oder Funktionsumfang
- lokale gegenüber entfernter Speicherung und Synchronisation
- Anmeldung, Käufe oder kostenpflichtige Dienste
- Datenschutz, Sicherheit oder benötigte Berechtigungen
- laufende Kosten, Lizenzen oder Anbieterbindung
- Entwicklungsaufwand, Wartbarkeit oder spätere Erweiterbarkeit

Stelle je Option Nutzen, Nachteile, Risiken, Kosten und Folgen knapp gegenüber und gib eine begründete Empfehlung. Frage nach der Entscheidung des Entwicklers. Stelle die betroffenen Teile des technischen Plans nicht als entschieden oder freigegeben dar, bevor eine Antwort vorliegt.

### 3. Als Blocker behandeln

Wenn ohne die Entscheidung kein konsistenter technischer Plan möglich ist, erledige zunächst alle davon unabhängigen Teile. Dokumentiere anschließend die offene Entscheidung und die konkrete Frage in `docs/technical-plan.md` sowie `STATUS.md`, setze den Status auf `Blockiert` und warte auf die Antwort. Triff keine stellvertretende Annahme.

Fasse eng zusammenhängende Entscheidungen in einer überschaubaren Frage zusammen. Unterbrich den Entwickler nicht für unwesentliche oder leicht rückgängig zu machende Details.

## Recherche und Entscheidungsgrundlage

Wenn eine Entscheidung von veränderlichen Fakten wie unterstützten Systemversionen, API-Verfügbarkeit, Lizenzbedingungen oder Preisen abhängt:

1. recherchiere in der aktuellen offiziellen Dokumentation des Herstellers oder Standards,
2. verlinke die konkrete Quelle mit Abrufdatum,
3. trenne belegte Fakten, Schlussfolgerungen und Empfehlungen und
4. markiere nicht verifizierbare Angaben als offene Entscheidung.

Prüfe nur bei Bedarf mit nicht verändernden Befehlen, welche Entwicklungswerkzeuge lokal verfügbar sind. Eine lokale Installation ist keine ausreichende Begründung für eine Technologieentscheidung.

## Vorgehen

1. Erfasse verbindliche Produkt-, Plattform-, Datenschutz- und Betriebsanforderungen.
2. Lege Zielplattform, Sprache, Framework, Toolchain und minimale System- beziehungsweise Browserversion fest oder stelle entscheidungsreife Optionen gegenüber.
3. Wähle ein einfaches Architekturprinzip und eine verständliche Projekt- und Modulstruktur.
4. Beschreibe das fachliche Datenmodell, Datenlebenszyklus, Speicherung und gegebenenfalls Synchronisation oder Migration.
5. Plane nur erforderliche externe APIs, Anmeldung, Käufe, Berechtigungen und Hintergrundfunktionen.
6. Beschreibe Fehlerbehandlung, Protokollierung und das Verhalten bei fehlender Verbindung oder nicht verfügbaren Diensten, soweit relevant.
7. Leite konkrete Datenschutz- und Sicherheitsmaßnahmen aus den tatsächlich verarbeiteten Daten und Risiken ab. Geheimnisse dürfen nicht im Repository gespeichert werden.
8. Definiere Testebenen, Build-Konfigurationen und den Veröffentlichungsweg.
9. Dokumentiere wesentliche Entscheidungen mit stabilen Kennungen wie `T-01`, einschließlich Alternativen und Gründen.
10. Ordne jede Kernfunktion und jedes relevante Akzeptanzkriterium der technischen Grundlage und einer vorgesehenen Prüfung zu.

## Ergebnisdatei

Erstelle oder aktualisiere `docs/technical-plan.md` mit dieser Struktur:

```markdown
# Technischer Plan

## Status und Freigabe
## Verbindliche Grundlagen und Einschränkungen
## Zusammenfassung der technischen Entscheidungen
## Entscheidungsprotokoll
## Zielplattform und Kompatibilität
## Sprache, Framework und Toolchain
## Architekturprinzip und Projektstruktur
## Datenmodell
## Speicherung, Synchronisation und Migration
## Externe APIs und Dienste
## Anmeldung, Käufe und Berechtigungen
## Fehlerbehandlung und Protokollierung
## Datenschutz und Sicherheit
## Teststrategie
## Build, Konfiguration und Veröffentlichung
## Abhängigkeiten, Lizenzen und laufende Kosten
## Risiken und bewusste Kompromisse
## Rückverfolgbarkeit zu Anforderungen
## Offene technische Entscheidungen
## Quellen
```

Nicht anwendbare Abschnitte werden knapp mit `Nicht erforderlich` und einer Begründung gekennzeichnet. Unter `Status und Freigabe` stehen zunächst `Entwurf` und `Freigabe ausstehend`.

Wesentliche Entscheidungen werden kompakt dokumentiert:

| ID | Entscheidung | Gewählte Option | Geprüfte Alternativen | Entschieden durch | Begründung und Folgen |
|---|---|---|---|---|---|

## Qualitätsprüfung

Prüfe vor der Übergabe:

- Jede Kernfunktion und jedes relevante Akzeptanzkriterium ist technisch unterstützt.
- Die Architektur ist für den freigegebenen Umfang ausreichend und enthält keine unbegründeten Schichten oder Dienste.
- Datenmodell, Speicherung, Löschung und gegebenenfalls Migration sind konsistent.
- Berechtigungen, Datenschutz und Sicherheitsmaßnahmen passen zu den tatsächlich verarbeiteten Daten.
- Externe Abhängigkeiten, Lizenzen, Konten und laufende Kosten sind vollständig sichtbar.
- Teststrategie und Veröffentlichungsweg sind mit der gewählten Plattform praktisch ausführbar.
- Veränderliche technische Fakten sind aktuell belegt; Unsicherheiten sind offen markiert.
- Entscheidungen und Alternativen sind so dokumentiert, dass der Implementierungsplan darauf aufbauen kann.
- Alle folgenreichen Entscheidungen wurden dem Entwickler mit Optionen und Empfehlung vorgelegt und seine Auswahl ist im Entscheidungsprotokoll festgehalten.
- Keine für den Plan notwendige Entscheidung ist noch offen, wenn der Status auf `Bereit zur persönlichen Abnahme` gesetzt wird.

Dokumentiere die Prüfung in `STATUS.md`. Sind notwendige Entscheidungen offen, verwende `Blockiert`; andernfalls setze den Status auf `Bereit zur persönlichen Abnahme`.

## Freigabe und Übergang

Nach der Freigabe durch den Entwickler:

1. Halte Freigabestatus und bestätigte technische Entscheidungen in der Ergebnisdatei fest.
2. Führe den GitHub-Abschluss der Phase durch.
3. Trage als nächste Phase `Implementierungsplan` ein.
4. Nenne `docs/product-requirements.md`, `docs/functional-plan.md` und `docs/technical-plan.md` als erforderliche freigegebene Eingaben.

Wechsle erst nach erfolgreichem GitHub-Abschluss zur nächsten Phase.
