# Sicherheit und Kompatibilität | Windows Client 2.2.9

Windows x64 (x86_64) und Windows ARM64 sind getrennte, native Release-Kanäle. Für Version 2.2.9 stimmen beide veröffentlichten Quell-Identitäten mit `300cfd6501323aa04fd15d247ecef56a70cf59f7` überein, ihre tatsächlichen Binär- und Signatur-Hashes dagegen nicht. Die Pakete dürfen weder untereinander gemischt noch in einen gemeinsamen SHA256SUMS-Namensraum gezwungen werden.

Das RSA-SHA256-Manifest wird mit `mc-client-caf94007b07dc90b` geprüft. Zusätzlich müssen Dateihashes, URL-Quelle, Architektur, Commit, `client_build` und semantische Versionsmonotonie stimmen. Signierte kompatible Gateway-Versionen: mindestens **2.0.5**, höchstens **2.9.9**; Bridge-Protokoll **1**. Das sind Protokollgrenzen, kein Beleg für einen bestandenen Praxistest jeder Version.

Der neue Windows-only Update-Bootstrap von 2.2.8 darf bei vollständig fehlender Enrollment-Konfiguration ausschließlich die genaue native Update-Manifestroute am bereits lokal eingestellten HTTPS-Gateway-Root verwenden. Wenn irgendeine Enrollment-Konfiguration existiert, auch beschädigt oder symlinked, gibt es **keinen** alternativen Fallback. Fremde Hosts, HTTP, URL-Pfade/Query-Injection, Linux/macOS-Clients und fremde CPU-Kanäle bleiben ausgeschlossen. Der Bootstrap verschafft **keine Kopplung, Geräteidentität, Zugangsdaten oder Gateway-Berechtigung**.

Windows Setup-EXE wird in diesem Releasepfad als `unsigned-owner-authorized` für Authenticode ausgewiesen; die getrennten RSA-basierten Release-Verifikationen sind obligatorisch und dürfen nicht als Windows Authenticode-Zertifikat dargestellt werden. Die Signatur-Schlüssel bleiben lokal beim Owner und fehlen in GitHub sowie nativen Build-Runnern.

2.2.9 ist kein produktiver Stable- oder Latest-Client, solange die echten Benutzer-OTA-, GUI- und Rollback-Tests nicht positiv abgeschlossen und dokumentiert sind. Der stabile Windows-x64-Kanal bleibt währenddessen 2.2.3. Isolierte native x64- und ARM64-Tests sind erforderlich, nicht nur der erfolgreiche CI-Build oder ein Setup-Smoke.


## Neue Windows-GUI-Integritätsprüfung ab 2.2.9

Die GUI prüft bei fehlender `product.shell_core_consistent`-Projektion die lokale Paketidentität selbst: erwartetes native binary-only Windows-Manifest, Commit/Version, kanonischer Payload-Hash und SHA-256 über jedes installierte Dateimitglied einschließlich Core, Tray und Supervisor. Unerwartete Reparse-Punkte, fehlende oder manipulierte Dateien und ungültige Manifestwerte blockieren. Wenn der native Core ausdrücklich `shell_core_consistent=false` meldet, bleibt das immer ein hartes Verbot; die Shell muss weiterhin aus dem aktiven Programm-Slot stammen. Die bereits bestehenden Release-RSA-, Gateway- und TLS-Pflichtprüfungen bleiben unverändert.

Diese lokale Sicherheitsprüfung wurde im echten Windows-ARM64-QA mit Positiv- und Negativfällen getestet; das allein beweist noch **keinen** vollständigen 2.2.9 In-App-OTA-/Rollback- und DPI-Feldtest für x64 und ARM64.
