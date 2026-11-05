# Meilleur Commander Windows Client | Downloads und Versionsnachweise

Meilleur Commander Windows hat getrennte native Pakete für **x86_64 (x64)** und **ARM64**. Beide besitzen eine native Windows-Oberfläche, den installierten Core und den lokalen Supervisor; es handelt sich um Binärpakete, nicht um Quellcode-Archive. Ausgegebene Update-Kanäle und eine neue GitHub-Version ersetzen niemals eine explizite Gateway-Freigabe.

## Aktueller Freigabestatus

- **Stabile Kundenfassung x64: 2.2.3**, siehe [stabiler Release](https://github.com/Meilleur-Tech/Meilleur-Commander-Windows-Releases/releases/tag/windows-client-v2.2.3) und [channels/stable.json](channels/stable.json). Der stabile Kanal bleibt während der QA von 2.2.8 unverändert.
- **Testkandidaten 2.2.8 x64 und ARM64:** signierte native Binaries aus Source `39549d4a188eafd8748dc0f167affc0495c20131`, jedoch **nicht Stable/Latest/Produktivfreigabe**. Zurzeit sind die Versionen im QA-Abnahmeprozess; ein bloßer Release-Tag oder Draft ist keine zugesagte Verfügbarkeit.
- **Vorherige QA: 2.2.7** jeweils als getrennte signierte Prereleases. Ihre signierten Artefakte dürfen nicht umgepackt oder ersetzt werden.

| CPU | Version | Dateiname Setup | Dokumentation |
|---|---|---|---|
| Windows x64 | 2.2.8 | `Meilleur-Commander-Client-Windows-x86_64-2.2.8-Setup.exe` | [Release Notes x64](docs/RELEASE-NOTES-2.2.8.md) |
| Windows ARM64 | 2.2.8 | `Meilleur-Commander-Client-Windows-arm64-2.2.8-Setup.exe` | [Release Notes ARM64](docs/RELEASE-NOTES-2.2.8-arm64.md) |

## Anleitungen und Prüfsummen

[Installation 2.2.8](docs/INSTALLATION.md) | [Fehlerbehebung 2.2.8](docs/FEHLERBEHEBUNG.md) | [Sicherheit und Kompatibilität 2.2.8](docs/SICHERHEIT-UND-KOMPATIBILITAET.md)

Die x64-Dateiliste [docs/SHA256SUMS-2.2.8.txt](docs/SHA256SUMS-2.2.8.txt) und die eigenständige ARM64-Dateiliste [docs/SHA256SUMS-2.2.8-arm64.txt](docs/SHA256SUMS-2.2.8-arm64.txt) dürfen nicht verwechselt werden. Die Dateien `manifest.json`, `installer.json` und `artifact-source.json` in jedem Release beziehen sich nur auf dessen CPU-Architektur.

**Sicherheit:** Das Gateway verifiziert die RSA-SHA256-Release-Signatur mit dem Key `mc-client-caf94007b07dc90b`, exakte SHA-256-Digests, Architektur, Source und Bridge-/Gateway-Kompatibilität. Weder GitHub »Latest« noch die Sichtbarkeit eines Prerelease installiert automatisch Updates. Der private Signierschlüssel liegt nicht in diesem Repository oder bei GitHub Actions. Die veröffentlichten ZIP-Dateien sind binary-only; die Windows Setup-EXE ist nicht Authenticode-codesigniert (Owner-Freigabevertrag), sondern wird durch den getrennten RSA-Release- und Hash-Vertrauenspfad abgesichert.

Source, CLI und Tests: [Meilleur-Tech/Meilleur-Commander](https://github.com/Meilleur-Tech/Meilleur-Commander), [Issue #1704](https://github.com/Meilleur-Tech/Meilleur-Commander/issues/1704). Keine privaten Keys, Enrollment-Tokens, Kundendaten oder ungeschützten CI-Artefakte im Release-Repository.
