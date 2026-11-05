# Changelog der öffentlichen Windows-Release-Dokumentation

## Unreleased | 2.2.9 QA-Kandidaten

- Windows x64 und ARM64: Quellcommit `300cfd6501323aa04fd15d247ecef56a70cf59f7` und separate native QA-Releases.
- Präzise, fail-closed SHA-256-Prüfung des installierten Pakets bei fehlendem nativen `shell_core_consistent`-Statusfeld (PR #1748).
- Bisherige 2.2.8-Assets bleiben unveränderlich. Stable/Latest x64 weiterhin 2.2.3.
- Nativer signierter Release und echte Windows GUI-/OTA-/Rollback-Abnahme bleiben getrennte Freigabegates.

## 2.2.8 QA-Kandidaten

- Dokumentation der getrennten signierten Windows x64- und ARM64-2.2.8-Handoffs und ihrer unterschiedlichen SHA256-Listen.
- Sicherer Windows-only Update-Bootstrap aus dem bereits konfigurierten HTTPS-Gateway für noch ungepaarte Geräte, ohne Enrollment-/RSA-Umgehung (Source PR #1735).
- Offene Native-OTA-, GUI-, Rollback- und Production-Feldtests als Release-Blocker sichtbar gemacht.
- Vorhandenen stabilen x64-2.2.3-Kanal ausdrücklich nicht umgestellt.

## Historisch

Die unveränderlichen älteren GitHub-Releases und der maschinenlesbare stabile Kanal bleiben als Nachweis verfügbar.
