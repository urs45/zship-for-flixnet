# zShip for Flixnet – Update Channel

Dieses Repository dient als öffentlicher **Update- und Hotfix-Datenkanal** für zShip for Flixnet.

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

## Sicherheit

- Kein GitHub-Token oder Passwort ist in zShip erforderlich.
- Der Zugriff auf dieses Repository erfolgt ausschließlich lesend über öffentliche HTTPS-/Raw-URLs.
- Die Remote-Dateien sind JSON-Daten; sie werden nicht als Python-Code ausgeführt.
- Keine privaten Zugangsdaten oder gerätespezifischen Informationen in dieses Repository eintragen.

## Hinweis

Dieses Repository ist der Datenkanal für die zugehörige zShip-for-Flixnet-Konfiguration. Änderungen an den JSON-Dateien sollten nur vorgenommen werden, wenn Schema, Revisionierung und die erwartete zShip-Version bekannt sind.
