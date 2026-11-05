# Fehlerbehebung für Windows Client 2.2.9

**Kein Update angezeigt (`source_unavailable`):** Prüfen, ob bereits eine echte Geräte-Kopplung und eine freigegebene Gateway-Update-Zuordnung existiert. Ein ungepaarter Client 2.2.5 kennt den neuen Bootstrap von 2.2.8 noch nicht. Er braucht ein vom Benutzer legitim bestätigtes Browser-Pairing oder einen einmaligen signierten Installer. Die vorhandene Enrollment-Konfiguration darf auch bei beschädigter Datei nicht durch einen frei gewählten Internet-Link umgangen werden.

**`incompatible` oder `gateway_update_required`:** Das Gateway muss im im signierten Manifest angegebenen kompatiblen Bereich liegen, und Architektur sowie Bridge-Protokoll müssen passen. ARM64 und x64 haben unterschiedliche Updatepfade, Prüfsummen und Releases. Nie den ARM64-Installer auf x64 als Ersatz für einen fehlenden QA-Host benutzen.

**`rollback_required` / `outcome_unknown`:** Die Transaktionssperre schützt die Installation vor unkontrollierten Wiederholungen. Keine Ledger-Datei oder .product-transaction-Dateien einfach löschen. Logs ohne Tokens/Private Keys sichern, die dokumentierte Wiederherstellung über den aktuellen Launcher benutzen und anschließend Slots plus Enrollment-Identität vergleichen.

**GUI-Probleme:** Fenstergröße, Skalierung 100/125/150 %, abgeschnittene Texte, Kontrast bei »Namen speichern«, Pairing-Code und Schaltflächen getrennt erfassen. Ein erfolgreiches Setup und ein grüner CI-Build sind noch kein visueller Abnahmenachweis. Den Fehler mit Screenshot, Version, CPU, Auflösung und der exakten Benutzer-Sitzung in Meilleur Commander Issue #1704 dokumentieren.

**Sicherheitsprüfung:** Bei unerwarteten Prüfsummen, unbekanntem Schlüssel, falscher Architektur oder ungültiger HTTPS-Origin keinen Installer starten. Die im GitHub-Release enthaltenen `SHA256SUMS` und RSA-verifizierten `manifest.json`/ `installer.json` prüfen.


**Shell/Core-Versionskonflikt im Einstellungsbereich:** Die native GUI von 2.2.8 konnte bei fehlendem `product.shell_core_consistent`-Statusfeld einen falschen Drift melden, obwohl die installierten Core-/Tray-/Supervisor-Hashes korrekt waren. In 2.2.9 wird nur bei fehlender Statusaussage stattdessen die vollständige native Bundle-Integrität lokal anhand der signierten Installationszuordnung überprüft. Eine explizite Negativmeldung, Dateimanipulation oder ein Pfadkonflikt bleibt ein hartes Updateverbot. Das ist kein Ersatz für den Release-RSA-/HTTPS-/Gateway-Check. Siehe [PR #1748](https://github.com/Meilleur-Tech/Meilleur-Commander/pull/1748).
