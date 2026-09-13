# zShip GitHub Update Channel

Dieses Repository ist nur ein **Datenkanal** für zShip. Es werden keine entfernten Python-Dateien ausgeführt.

## Einmalige Einrichtung

1. Auf GitHub ein **öffentliches** Repository erstellen, z. B. `zship-hotfixes`.
2. `hotfix_rules.json` und `update_manifest.json` in den Root des Branches `main` hochladen.
3. In Kodi unter **zShip → Einstellungen → Allgemein → Self-Healing / Hotfix / GitHub** eintragen:
   - GitHub-Updatekanal verwenden: EIN
   - GitHub Benutzer / Organisation: dein GitHub-Name
   - GitHub Repository: `zship-hotfixes`
   - GitHub Branch: `main`
   - Hotfix-Pfad: `hotfix_rules.json`
   - Manifest-Pfad: `update_manifest.json`
4. **Jetzt Hotfix + Version prüfen** ausführen.

## Hotfix aktualisieren

`hotfix_rules.json` bearbeiten und `revision` **immer erhöhen**. Beispiel:

```json
{
  "schema": 1,
  "revision": 2026091302
}
```

zShip prüft standardmäßig alle 30 Minuten. Eine höhere Revision wird atomar übernommen. Der lokale Lernzustand (`hotfix_state.json`) bleibt auf jedem Gerät separat und wird nie zu GitHub hochgeladen.

## Neue zShip-Version ankündigen

In `update_manifest.json` nur `latest_addon_version` und optional `message` ändern:

```json
{
  "schema": 1,
  "channel": "stable",
  "latest_addon_version": "2026.09.13.29",
  "message": "Vixstream/Dood aktualisiert",
  "hotfix_revision": 2026091302,
  "hotfix_file": "hotfix_rules.json",
  "download_url": "",
  "sha256": ""
}
```

Eine Box mit älterer Version zeigt die Meldung nur einmal pro neuer Version. Standardprüfung: alle 6 Stunden sowie beim Kodi/zShip-Service-Start.

## Optional: ZIP über GitHub Releases verteilen

Wenn du später eine Release-ZIP auf GitHub hinterlegst, kann `download_url` auf das Release-Asset zeigen. Besonders praktisch ist ein immer gleich benanntes Asset wie `plugin.video.zship.zip`:

`https://github.com/DEINNAME/zship-hotfixes/releases/latest/download/plugin.video.zship.zip`

13.28 **installiert Updates noch nicht automatisch**. Der Link ist nur Metadaten für den späteren Download-/Installer-Schritt.

## Sicherheit

Keine Passwörter, Tokens oder privaten Daten in dieses öffentliche Repository schreiben. Die Remote-Dateien sind ausschließlich JSON-Daten; zShip führt daraus keinen Python-Code aus.
