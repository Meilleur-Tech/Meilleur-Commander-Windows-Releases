# Meilleur Commander Windows Client | Downloads und Versionsnachweise

Meilleur Commander für Windows besitzt getrennte native **x64**- und **ARM64**-Installationspakete mit Oberfläche, Core, Supervisor und Launcher. GitHub-Assets und QA-Kanal-Freigaben sind separat; kein Prerelease darf als Stable oder Latest ausgegeben werden.

## Aktueller Freigabestatus

- **Stable / GitHub Latest für x64: 2.2.3**, siehe [stable.json](channels/stable.json). Kein produktiver Kanal wurde durch 2.2.9 verändert.
- **Neue isolierte QA-Kandidaten: 2.2.9 für x64 und ARM64**, gemeinsam gebundener Quellcommit `300cfd6501323aa04fd15d247ecef56a70cf59f7`. Private native Build- und Owner-RSA-Freigabe müssen vor Asset-Upload erfolgreich nachgewiesen sein. Die Release-Links werden erst nach bestandener Prüfung als Prerelease veröffentlicht, niemals als Stable/Latest.
- **Bisherige QA: 2.2.8 x64 und ARM64**, bereits als getrennte unveränderliche RSA-signierte Prereleases veröffentlicht. Der isolierte QA-Gateway hatte für beide Architekturen 2.2.8 aktiviert. Diese Releases werden nicht ersetzt oder umgepackt.

| CPU | Kandidat | Native Setup-Datei | Release Notes |
|---|---|---|---|
| Windows x64 (x86_64) | 2.2.9 | `Meilleur-Commander-Client-Windows-x86_64-2.2.9-Setup.exe` | [x64-Release-Notes](docs/RELEASE-NOTES-2.2.9.md) |
| Windows ARM64 | 2.2.9 | `Meilleur-Commander-Client-Windows-arm64-2.2.9-Setup.exe` | [ARM64-Release-Notes](docs/RELEASE-NOTES-2.2.9-arm64.md) |

## Installations- und Sicherheitsdokumentation

[Installation](docs/INSTALLATION.md) · [Fehlerbehebung](docs/FEHLERBEHEBUNG.md) · [Sicherheit & Kompatibilität](docs/SICHERHEIT-UND-KOMPATIBILITAET.md)

Die unterschiedliche x64-[SHA-256-Assetliste](docs/SHA256SUMS-2.2.9.txt) und ARM64-[SHA-256-Assetliste](docs/SHA256SUMS-2.2.9-arm64.txt) gehören ausschließlich zum jeweils zugehörigen, unabhängig signierten CPU-Release. Vor dem Release ist ein öffentliches Main-Readback dieser dokumentierten Digests erforderlich.

Das Gateway überprüft RSA-SHA256 (`mc-client-caf94007b07dc90b`), SHA-256, Version, Architektur, Quell-/Build-Identität, Gateway- und Bridge-Kompatibilität. Die EXE wird in dieser Owner-Releasekette nicht über Windows Authenticode codesigniert (`unsigned-owner-authorized`), sondern nur über den separat geprüften signierten Release-Pfad verteilt. Der private RSA-Schlüssel liegt weder im öffentlichen Repository noch auf einem Windows-Buildrunner. SHA-256-Hashlisten und Release-Dateien sind architekturgetrennt.

Source und ausführliche QA-Nachweise: [Meilleur Commander](https://github.com/Meilleur-Tech/Meilleur-Commander) · [Windows-Abnahme #1704](https://github.com/Meilleur-Tech/Meilleur-Commander/issues/1704). Authentifizierungs-/Enrollment-Daten sowie private Signaturmaterialien gehören niemals in die Release-Assets.
