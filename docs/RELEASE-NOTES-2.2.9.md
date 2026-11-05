# Windows x64 Client 2.2.9 | RSA-signierter QA-Kandidat (kein Stable/Latest)

**Release-Status:** In Vorbereitung zur getrennten nativen Build-/Owner-RSA-Abnahme. Keine Produktivfreigabe. Der unterschriebene x64-/ARM64-Releasestand wird ausschließlich nach erfolgreicher SHA-256-/RSA- und öffentlicher Dokumentationsprüfung veröffentlicht.

## Änderungen in Version 2.2.9

- **GUI-Fix `product_drift`:** In signierten 2.2.8-Windows-Installationen fehlte im nativen Status gelegentlich das Feld `product.shell_core_consistent`. Dadurch meldete die Oberfläche fälschlich einen Shell/Core-Versionkonflikt und sperrte die Update-Schaltfläche, obwohl die Programmdateien unverändert waren.
- [Source-PR #1748](https://github.com/Meilleur-Tech/Meilleur-Commander/pull/1748) (ChristopherZender reviewed, CodeGuard/CI PASS, in `main` gemergt): Bei fehlendem Statusfeld validiert die GUI **lokal die gesamte native Paketintegrität** anhand von Manifest, kanonischer Dateiliste, Payload-Digest und SHA-256 sämtlicher Member. Ein ausdrücklich negativer Status oder ungültiger SHA/Pfad bleibt sperrend.
- Die bestehende Windows-only RSA-signierte Manifest-Erkennung des ungepaarten Clients aus Version **2.2.8** bleibt erhalten; kein Enrollment-Bypass, kein freier Manifest-Host, keine Gateway-/TLS-/RSA-Abschwächung.
- Die Windows-Builder führen einen echten C#/.NET-Integritäts-Smoke mit Manipulations-Negativtests aus.

## Native Setups und Updatepakete

| CPU | Datei | Zweck |
|---|---|---|
| x64 (x86_64) | `Meilleur-Commander-Client-Windows-x86_64-2.2.9-Setup.exe` | Native interaktive Setup-Installation / einmaliges Initial-Upgrade |
| x64 (x86_64) | `Meilleur-Commander-Client-Windows-x86_64-2.2.9.zip` | RSA-signiertes binary-only Windows-Updatepaket |

Release-Tag nach freigegebener Veröffentlichung: [`windows-client-v2.2.9`](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/releases/tag/windows-client-v2.2.9). Eine isolierte Gateway-QA-Aktivierung ist **nicht** die produktive Freigabe. Installationsbeschreibung: [Installation](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/INSTALLATION.md).

## Installation, In-App-Update und Migration

Die vorhandene korrekte CPU-Architektur und die lokale HTTPS-Root-Konfiguration müssen erhalten bleiben. Ein bereits gekoppelter Client bezieht Updates ausschließlich über das ihm zugeordnete Gateway. Der 2.2.8-Bootstrap kann auf einem alten ungepaarten 2.2.5-Binary nicht rückwirkend wirken: Dort sind legitimes Browser-Pairing oder einmalige signierte Setup-Installation erforderlich. Authentifiziertes In-App-Upgrade und Verbindungserhalt müssen unter Windows x64 und ARM64 noch separat mit der **fertigen 2.2.9** nachgewiesen werden.

## Rollback und bekannte Einschränkungen

Für die native Windows-ARM64-QA der unveränderten 2.2.8 ist ein echter Launcher-Rollback `2.2.8 → 2.2.5` mit unabhängigem Slot-Readback und anschließender Setup-Wiederherstellung bestanden. Für `2.2.9` selbst fehlen derzeit noch vollständige native UI-/DPI- und In-App-OTA-/Rollback-Feldtests. x64 bleibt mangels isoliertem nativen interaktivem Testhost gesperrt; das produktive XPS wird nicht für QA verändert. Stable/Latest/PROD bleibt 2.2.3, bis alle Release-Gates erfüllt sind.

## Kompatibilität und Sicherheit

Windows x86_64, Gateway-Kompatibilität laut signiertem Release-Manifest voraussichtlich **2.0.5 bis 2.9.9**, Bridge-Protokoll **1** (vor Release direkt gegen die tatsächlich signierten Daten zu bestätigen). Signaturalgorithmus RSA-SHA256, Key-ID `mc-client-caf94007b07dc90b`. Windows Authenticode: `unsigned-owner-authorized`; das ist **kein** Windows Code-Signing-Zertifikat. RSA-Signatur, CPU-Zuordnung, exakte Hashes, Source-/Buildbindung, Gateway und HTTPS bleiben zwingend.

Siehe [Fehlerbehebung](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/FEHLERBEHEBUNG.md) und [Sicherheitsmodell](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SICHERHEIT-UND-KOMPATIBILITAET.md).

## Release-Quelle und SHA-256-Nachweise

- Eingefrorener Source SHA: `300cfd6501323aa04fd15d247ecef56a70cf59f7`.
- Nativer privater GitHub-Workflow: [Run #42096513483](https://github.com/Meilleur-Tech/Meilleur-Commander/actions/runs/42096513483).
- Owner-RSA, vollständiger 7-Asset-SHA256-Public-Readback und echter 2.2.9 GUI-/OTA-Praxistest: **noch nicht als abgeschlossen markiert**.
- Setup SHA-256: `d4e785922d6e1700c1deb75a12f434f7f940448ee0f6434386f645a8628e4bdc` (aus dem echten signierten Owner-Staging verifiziert).
- Vollständige architektureigene [Asset-SHA-256-Liste](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SHA256SUMS-2.2.9.txt). Die Liste umfasst sechs konkrete Release-Dateien; die siebte `SHA256SUMS`-Datei ist nicht selbst gehasht.
- Release- und QA-Tracker: [Meilleur Commander #1704](https://github.com/Meilleur-Tech/Meilleur-Commander/issues/1704); Fix und unabhängiges Review [PR #1748](https://github.com/Meilleur-Tech/Meilleur-Commander/pull/1748).

## Öffentliche Dokumentation

[README](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/README.md) · [Installation](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/INSTALLATION.md) · [Sicherheit](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SICHERHEIT-UND-KOMPATIBILITAET.md) · [SHA-256](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/blob/main/docs/SHA256SUMS-2.2.9.txt)
