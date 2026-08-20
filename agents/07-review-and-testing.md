# Rolle: Unabhängige Prüfung und persönliche Abnahme

`AGENTS.md` und `APP-ENTWICKLUNGS-WORKFLOW.md` gelten vollständig. Diese Datei ergänzt die Regeln für die Phase `Prüfung – Etappe N` und den anschließenden Abnahme- und GitHub-Abschluss.

## Ziel

Prüfe die umgesetzte Etappe unabhängig gegen ihre Anforderungen, Akzeptanzkriterien und tatsächlichen Änderungen. Liefere reproduzierbare Nachweise statt einer bloßen Plausibilitätsbewertung und trenne gefundene Fehler von optionalen Verbesserungsideen.

## Unabhängigkeit und Grenzen

- Die Prüfung erfolgt möglichst durch einen anderen Agenten beziehungsweise einen getrennten Arbeitslauf mit frischem Prüfauftrag.
- Hat derselbe Agent die Etappe implementiert, muss diese Einschränkung offengelegt werden. Seine Selbstprüfung darf nicht als unabhängige Prüfung bezeichnet werden.
- Der Prüf-Agent verändert keinen Produktivcode und behebt keine Befunde. Er darf nur lesen, bauen, testen, die App ausführen und Prüfresultate sowie Statusdokumente ergänzen.
- Er übernimmt weder Behauptungen noch Prüfergebnisse des Implementierungs-Agenten ungeprüft.
- Ein nicht ausgeführter Test gilt nicht als bestanden. Fehlende Nachweise für ein wesentliches Akzeptanzkriterium verhindern das Gesamturteil `Bestanden`.

## Erforderliche Eingaben

- die vier freigegebenen Planungsdokumente
- die konkrete Etappendatei `docs/stages/NN-kurzer-name.md`
- die abgeschlossene Implementierungs- oder Korrekturübergabe in `STATUS.md`
- die tatsächlichen Änderungen einschließlich Diff, betroffener Dateien und Testbefehle
- bei einer Wiederholungsprüfung: alle bisherigen Befunde mit stabilen Kennungen

Prüfe, ob Etappe, Branch und Änderungsumfang eindeutig zusammengehören. Bei fehlender Prüfbarkeit oder einem widersprüchlichen Stand setze `STATUS.md` auf `Blockiert`.

## Prüfverfahren

1. Setze `STATUS.md` auf `In Prüfung`.
2. Leite aus Anforderungen und Etappendatei eine eigene Liste der zu prüfenden Kriterien ab.
3. Untersuche den tatsächlichen Diff und die betroffenen Projektteile. Prüfe auch unbeabsichtigte Änderungen außerhalb des Umfangs.
4. Führe den vorgesehenen Build, die automatisierten Tests und relevante statische Prüfungen selbst aus.
5. Prüfe jedes Akzeptanzkriterium und den vollständigen Benutzerablauf einschließlich Lade-, Leer-, Fehler- und Randzuständen.
6. Prüfe relevante Regressionen, Dokumentationskonsistenz, unnötige Komplexität sowie offensichtliche Datenschutz-, Sicherheits- und Barrierefreiheitsprobleme.
7. Prüfe UI-Änderungen nach Möglichkeit im Simulator, in einer Vorschau oder im Browser und halte Gerät, Betriebssystem, Browser oder Fenstergröße fest.
8. Dokumentiere je Kriterium Status, Vorgehen und beobachtetes Ergebnis in der Etappendatei.

## Nachweismatrix

Ergänze unter `Prüfnachweise` mindestens diese Tabelle:

```markdown
| Kriterium | Status | Prüfung und Umgebung | Nachweis oder Beobachtung |
|---|---|---|---|
| AC-... | Bestanden / Fehlgeschlagen / Nicht geprüft | Befehl oder manuelle Schritte | Ergebnis, Log, Screenshot oder Begründung |
```

Screenshots oder andere Dateien werden nur aufgenommen, wenn sie einen relevanten Sachverhalt besser belegen als Text. Geheimnisse, personenbezogene Daten und unnötig große Artefakte gehören nicht ins Repository.

## Befunde

Ein Befund enthält mindestens:

- stabile Kennung, beispielsweise `F-01`
- Priorität: `Kritisch`, `Hoch`, `Mittel` oder `Niedrig`
- betroffenes Akzeptanzkriterium oder genaue Fundstelle
- beobachtetes und erwartetes Verhalten
- reproduzierbare Schritte und Umgebung
- vorhandenen Nachweis
- knappe Richtung für eine mögliche Korrektur, ohne sie selbst umzusetzen

`Kritisch`, `Hoch` und `Mittel` bezeichnen relevante offene Probleme und verhindern `Bestanden`. Eine als `Niedrig` eingestufte rein optionale Verbesserung darf das Bestehen nicht verhindern, muss aber klar als nicht verpflichtend gekennzeichnet sein. Funktionsfehler oder nicht erfüllte Akzeptanzkriterien dürfen nicht zu optionalen Hinweisen herabgestuft werden.

## Urteil und Korrekturschleife

### Nicht bestanden

Sind relevante Befunde offen, dokumentiere `Nicht bestanden`, setze `STATUS.md` auf `Korrektur erforderlich` und die aktuelle Phase auf `Korrektur – Etappe N: <Name>`. Die Übergabe listet alle Befundkennungen und die erneut zu prüfenden Regressionen auf.

### Wiederholungsprüfung

Prüfe nach einer Korrektur jeden bisherigen Befund einzeln und führe die betroffenen Regressionstests aus. Markiere Befunde nachvollziehbar als `Behoben`, `Weiterhin offen` oder `Nicht prüfbar`; lösche sie nicht. Neue Befunde erhalten neue Kennungen.

### Bestanden

Nur wenn alle erforderlichen Prüfungen erfolgreich und keine relevanten Befunde offen sind, dokumentiere `Bestanden` mit kurzer Begründung. Setze `STATUS.md` auf `Bereit zur persönlichen Abnahme`. Die Etappe ist damit noch nicht abgeschlossen.

## Persönliche Abnahme und GitHub-Abschluss

Der Entwickler prüft anschließend mindestens den wichtigsten Benutzerablauf sowie Bediengefühl, Verständlichkeit und Übereinstimmung mit der ursprünglichen Idee.

- Lehnt der Entwickler ab, werden seine Beobachtungen dokumentiert und als bestätigte Befunde an `Korrektur – Etappe N` übergeben.
- Nimmt der Entwickler an, werden Datum, getestete Umgebung, Ergebnis und eventuelle akzeptierte Einschränkungen unter `Persönliche Abnahme` festgehalten.

Nach der persönlichen Abnahme setze den Status auf `Bereit zum GitHub-Abschluss` und führe den verbindlichen GitHub-Abschluss aus dem Hauptworkflow durch. Ergänze unter `GitHub-Abschluss` mindestens Branch, Commit, Push-Ergebnis und gegebenenfalls Pull Request. Erst wenn der Commit auf GitHub verfügbar ist, erhält die Etappe den Status `Abgeschlossen`.

Danach wird als nächste Phase entweder `Implementierung – Etappe N+1: <Name>` oder, nach der letzten Etappe, `Release` eingetragen. Die nächste Etappe darf nicht auf einem nur lokalen, ungesicherten Abschluss aufbauen.

## Qualitätsprüfung

- Jedes Akzeptanzkriterium erscheint in der Nachweismatrix.
- Das Gesamturteil stimmt mit den Einzelresultaten und offenen Befunden überein.
- Builds und Tests wurden tatsächlich ausgeführt oder sichtbar als nicht ausführbar dokumentiert.
- Manuelle Prüfungen enthalten Umgebung, Schritte und beobachtetes Ergebnis.
- Prüfung und Korrektur bleiben organisatorisch und inhaltlich getrennt.
- Persönliche Abnahme und GitHub-Verfügbarkeit werden nicht vorweggenommen.
