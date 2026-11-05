# Windows x64 Client 2.2.8 | signierter QA-Kandidat (kein Stable/Latest)

**Status:** Signierter, native-build-verifizierter Kandidat für isolierte QA. Ein Draft/Prerelease ist kein produktiver Freigabekanal; die echte In-App-OTA-/Rollback-/GUI-Abnahme für 2.2.8 steht noch aus. Kunden-Gateway und Stable x64 2.2.3 bleiben unverändert.

## Neu und Änderungen gegenüber dem letzten signierten Kandidaten

Der sichere, Windows-exklusive Update-Bootstrap wurde in [PR #1735](https://github.com/Meilleur-Tech/Meilleur-Commander/pull/1735) korrigiert: Ein noch nicht gekoppelter Client kann ab 2.2.8 das exakte, architekturspezifische RSA-signierte Update-Manifest von dem bereits lokal eingestellten HTTPS-Gateway finden, ohne erst über eine Enrollment-Zuordnung zu verfügen. Das verbessert `update --check` und die zugehörige App-Anzeige. Auf Clients mit vorhandener Enrollment-Datei gilt unverändert ausschließlich die vom Gateway zugeordnete Update-Quelle. Es gibt keine neuen Geräteberechtigungen, Tokens oder freien externen URLs. Neue andere GUI-/CLI-/MCP-Funktionen: keine über diesen Fix hinaus.

## Download und Installation

| Windows-CPU | Datei | Verwendungszweck |
|---|---|---|
| x64 (x86_64) | `Meilleur-Commander-Client-Windows-x86_64-2.2.8-Setup.exe` | Native interaktive Setup-Installation bzw. Initial-Upgrade |
| x64 (x86_64) | `Meilleur-Commander-Client-Windows-x86_64-2.2.8.zip` | RSA-signiertes, binary-only Updatepaket für den verifizierenden Client/Gateway-Pfad |

Quelle/Release-Tag: [`windows-client-v2.2.8`](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/releases/tag/windows-client-v2.2.8). Diese Dateien sind erst verfügbar, sobald der Owner den Draft nach bestandenen Pflichtprüfungen als Prerelease veröffentlicht. Anleitung: [Installation](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/INSTALLATION.md).

## Update, Upgrade und Migration

Nach expliziter Gateway-QA-Aktivierung die native App verwenden, Updates prüfen und »Update installieren« wählen. Der gerade getestete Setup-Kaltstart ist **kein** Ersatz für den E2E-In-App-OTA-Nachweis. Ein ungepaarter alter Client 2.2.5 kann diesen neuen Bootstrap nicht nachträglich ausführen: Er benötigt einmaliges legitimes Browser-Pairing oder ein vom Owner signiertes Setup. Keine manuelle Enrollment-Fälschung oder freie Manifest-URL.

## Rollback und Wiederherstellung

Die vorhandene, vollständige Programm-Vorgängergeneration ist über den version-neutralen Launcher/Rollback-Pfad erreichbar. Für ARM64 wurde am 05.11.2026 im echten interaktiven QA-Benutzer ein signiertes **2.2.7 Setup** von 2.2.5 aus sowie ein echter Launcher-Rollback auf 2.2.5 nachgewiesen. Dieses Ergebnis gilt ausdrücklich **nicht** als 2.2.8-OTA- oder GUI-PASS. Für x64 2.2.8 sind native Update, Rückfall, Version, Enrollment-Erhalt, Ready/Restart und GUI noch als Release-Blocker offen.

## Kompatibilität, Sicherheit, Fehlerbehebung

Windows x86_64; Gateway-Version **2.0.5 bis 2.9.9**, Bridge-Protokoll **1** gemäß signiertem Manifest. Release-Signatur **RSA-SHA256**, Key-ID `mc-client-caf94007b07dc90b`, native artifact SHA-256 und Source-/Buildidentität gebunden. Authenticode EXE: `unsigned-owner-authorized`, also keine Behauptung eines Windows-Code-Signing-Zertifikats. Falscher CPU-Kanal, fehlende Daten, unzulässige Herkunft, defektes Enrollment, Downgrade oder Transaction-Fence blockieren statt Sicherheitsprüfungen zu umgehen. Siehe [Sicherheit und Kompatibilität](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SICHERHEIT-UND-KOMPATIBILITAET.md) und [Fehlerbehebung](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/FEHLERBEHEBUNG.md).

## Source, QA und SHA-256 Nachweis

- Exakter eingefrorener Source SHA: `39549d4a188eafd8748dc0f167affc0495c20131`.
- Native Build/Private-R2-Handoff: [GitHub Actions Run #41992099276](https://github.com/Meilleur-Tech/Meilleur-Commander/actions/runs/41992099276), erfolgreich.
- Owner-only Offline-RSA-Signierung mit unabhängig verifiziertem Transfer: bestanden, kein Asset veröffentlicht oder Gateway aktiviert.
- Setup SHA-256: `90b16511824f1b0225191ca75cc05b1198778818788f3cd483693d5e4fd111f1`.
- Für genau diesen CPU-Kanal: [alle sechs Asset-Hashes](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SHA256SUMS-2.2.8.txt) einschließlich ZIP, Setup, signiertem Manifest, signiertem Installer-Descriptor, Herkunft und Metadaten. Die siebte `SHA256SUMS`-Datei enthält keine eigene Prüfsumme.
- Relevanter Fehler- und Abnahme-Tracker: [Meilleur Commander #1704](https://github.com/Meilleur-Tech/Meilleur-Commander/issues/1704); unabhängiger Fix-Review auf PR #1735 und erfolgreiche Main-CI für den Source SHA.
- Status bei Dokumentation: Native Build, RSA, signierte Staging-Identität **PASS**; veröffentlichter Prerelease/Public-Readback, echter in-app OTA und GUI **OFFEN**. Keine Stable/Latest-/PROD-Freigabe vor gesonderter positiver Abnahme.

## Öffentliche Dokumentation

[README / Downloadübersicht](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/README.md) · [Installation](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/INSTALLATION.md) · [Fehlerbehebung](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/FEHLERBEHEBUNG.md) · [Sicherheit und Kompatibilität](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SICHERHEIT-UND-KOMPATIBILITAET.md) · [SHA-256-Assetliste](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SHA256SUMS-2.2.8.txt)
