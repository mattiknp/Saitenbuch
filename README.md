# Saitenbuch

Bespannungs-Archiv für Tennissaiten — jede Bespannung mit Spieler, Schläger,
Saite und Kilo, dazu Saitenregal mit Rollenbestand und Statistik.

Läuft als reine Website, eine einzelne HTML-Datei ohne Abhängigkeiten.

## Wo die Daten liegen

Die App speichert das Archiv als `saitenbuch.json` über die GitHub-Contents-API
in ein Repo deiner Wahl — standardmäßig ins **private** Repo `routine-tracker`.

**In diesem Repo hier liegen keine Archivdaten.** Es enthält nur die App.
Wer die Seite ohne Token öffnet, sieht ein leeres Archiv.

Der Zugangstoken wird ausschließlich im Browser abgelegt (`localStorage`),
niemals im Quelltext und niemals in der Archivdatei.

## Einrichten

1. Bei GitHub einen **Fine-grained Token** erzeugen
   (Settings → Developer settings → Personal access tokens → Fine-grained)
   - Repository access: nur das Repo, in dem die Daten liegen sollen
   - Permissions → Repository permissions → **Contents: Read and write**
2. Auf der Website den Knopf **GitHub** öffnen, Token einsetzen,
   Benutzer/Repo/Dateiname prüfen, **Verbinden**

Danach wird nach jeder Änderung automatisch hochgeladen und beim Öffnen geladen.
Zusätzlich gibt es **⬇ Sichern** / **⬆ Laden** als JSON-Datei.

## Bauen

`index.html` wird aus der App-Quelle erzeugt:

```bash
./bauen.sh                                   # nimmt ~/Claude/Artifacts/saitenbuch/index.html
./bauen.sh /pfad/zur/quelle/index.html       # oder ausdrücklich
```

Die Quelle trägt bewusst kein `<!DOCTYPE>`, weil sie auch als Claude-Artefakt
veröffentlicht wird und die Hülle dort von der Plattform kommt. `bauen.sh`
ergänzt Doctype, Zeichensatz und Viewport, damit die Website im
Standards-Modus läuft.
