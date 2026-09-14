# zShip for Flixnet – Update Channel

## WICHTIG – Hotfix-Kurzablauf

### Wo ist die aktuelle zentrale Hotfix-Regel?

Die aktuell verteilte Regeldatei liegt in diesem Repository im Root:

`hotfix_rules.json`

Diese Datei ist immer die **Basis für die nächste Hotfix-Version**.  
Nicht mit einer alten lokalen Kopie weiterarbeiten.

### Wenn zShip einen Hotfix-Kandidaten meldet

Auf der Testbox:

1. In zShip unter **Erkannte Hotfix-Kandidaten anzeigen** prüfen, was erkannt wurde.
2. Für eine genaue Auswertung bei Bedarf diese beiden lokalen Dateien sichern:

   `special://profile/addon_data/plugin.video.zship/hotfix_candidates.json`

   `special://profile/addon_data/plugin.video.zship/hotfix_state.json`

3. Screenshot oder die beiden JSON-Dateien zur Prüfung verwenden.
4. Erst bestätigte Kandidaten werden in die zentrale `hotfix_rules.json` übernommen.

Bei Auto-Lazy-Resolve gilt derzeit: Ein Kandidat wird erst nach **3 bestätigten erfolgreichen Lazy-Resolve-Durchläufen** als zentraler Hotfix-Kandidat behandelt.

### Neue zentrale Hotfix-Regel veröffentlichen

1. Immer die **aktuelle `hotfix_rules.json` aus diesem Repository** als Ausgangspunkt nehmen.
2. Bestätigten Fix ergänzen.
3. Feld `revision` erhöhen, z. B.:

   `2026091304` -> `2026091305`

4. Die bestehende Datei im Repository durch die neue Datei ersetzen:

   `hotfix_rules.json`

5. Fertig. Für einen reinen Hotfix ist **kein neues zShip-ZIP** erforderlich.
6. Die Boxen laden eine höhere Revision beim nächsten automatischen Hotfix-Check.
7. Zum sofortigen Test auf einer Box:

   **zShip-Einstellungen -> Jetzt Hotfix prüfen**

   Danach muss zShip melden, dass die neue Revision übernommen wurde oder bereits aktuell ist.

### Wann `update_manifest.json` ändern?

`update_manifest.json` nur ändern, wenn eine **neue zShip-Programmversion** veröffentlicht wird.

Beispiele:

- Nur neue Provider-/Resolver-/Lazy-Resolve-Regel -> **nur `hotfix_rules.json` ändern**
- zShip 2026.09.13.33 -> 2026.09.13.34 -> **`update_manifest.json` aktualisieren**

**Merksatz:**  
`hotfix_rules.json` = Regeln ohne neues zShip installieren  
`update_manifest.json` = Hinweis auf eine neue zShip-Version  
`hotfix_candidates.json` + `hotfix_state.json` = lokale Diagnosebasis für neue zentrale Regeln

---

Dieses Repository dient als **Update- und Hotfix-Datenkanal** für zShip for Flixnet.

Es enthält keine Zugangsdaten und führt keinen entfernten Python-Code aus. zShip liest ausschließlich die veröffentlichten JSON-Dateien, um kompatible Hotfix-Regeln und Versionsinformationen abzurufen.

## Dateien

### `hotfix_rules.json`

Enthält deklarative Kompatibilitäts- und Fallback-Regeln für Provider und Hoster, z. B. Resolver-Strategien, Header-/Referer-Varianten, Timeouts und Lazy-Resolve-Regeln.

Änderungen werden über die enthaltene `revision` versioniert. Eine höhere Revision kann von unterstützten zShip-Versionen automatisch übernommen werden.

### `update_manifest.json`

Enthält Informationen zum aktuellen zShip-Release und zur aktuell vorgesehenen Hotfix-Revision.

Das Manifest dient ausschließlich der Versionsprüfung und Update-Benachrichtigung.

## Self-Healing

zShip kann bestimmte Provider- und Hoster-Probleme lokal erkennen und alternative Strategien ausprobieren. Der dabei entstehende Lernzustand bleibt **lokal auf dem jeweiligen Kodi-Gerät**.

Lokale Zustände, Wiedergabedaten, Filmtitel, IDs oder andere Nutzungsdaten werden von diesem Repository **nicht gesammelt oder hochgeladen**.

Wenn Self-Healing eine dauerhaft funktionierende Alternative bestätigt, kann daraus ein lokaler Hotfix-Kandidat entstehen. Dieser wird nicht automatisch zu GitHub hochgeladen. Die zentrale Regel wird erst nach Prüfung bewusst in `hotfix_rules.json` übernommen.

## Sicherheit

- Kein GitHub-Token oder Passwort ist für diesen Hotfix-Kanal erforderlich, solange dieses Repository öffentlich lesbar ist.
- Der Zugriff erfolgt ausschließlich lesend über HTTPS-/Raw-URLs.
- Die Remote-Dateien sind JSON-Daten; sie werden nicht als Python-Code ausgeführt.
- Keine privaten Zugangsdaten oder gerätespezifischen Informationen in dieses Repository eintragen.
- Lokale Dateien wie `hotfix_state.json` und `hotfix_candidates.json` gehören **nicht** in dieses Repository.

## Hinweis

Dieses Repository ist der Datenkanal für die zugehörige zShip-for-Flixnet-Konfiguration. Änderungen an den JSON-Dateien sollten nur vorgenommen werden, wenn Schema, Revisionierung und die erwartete zShip-Version bekannt sind.
