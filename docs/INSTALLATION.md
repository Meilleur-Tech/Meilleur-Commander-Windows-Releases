# Installation und Aktualisierung | Windows 2.2.8

Wähle die korrekte CPU-Architektur aus den jeweils separaten x64- und ARM64-Releases. Für x64 lautet der Setup-Dateiname `Meilleur-Commander-Client-Windows-x86_64-2.2.8-Setup.exe`, für ARM64 `Meilleur-Commander-Client-Windows-arm64-2.2.8-Setup.exe`. Signatur und SHA-256 erst anhand der architekturspezifischen Release-Dateien und des echten Release-Gateways prüfen. Kein EXE/ZIP von fremden Downloadseiten verwenden.

**Neuinstallation:** Den signierten Installer im gewünschten interaktiven Windows-Benutzerprofil starten, Gateway-HTTPS-Root setzen und für echte Kopplung den angezeigten Pairing-Code im authentifizierten Gateway-Browser bestätigen. Ein installierter, aber nicht gekoppelter Client erhält keine Token, Bridge-Berechtigung oder Gerätefreigabe. Die Anmeldung muss durch einen berechtigten Nutzer erfolgen.

**Update für bereits gekoppelte Clients:** In der nativen App Einstellungen → Updates → Auf Updates prüfen und danach »Update installieren« wählen. Der Client bezieht nur das vom zugeordneten Gateway angebotene, RSA-verifizierte Paket des richtigen CPU-Kanals. Geräte sollten das Update erst nach erfolgreicher QA-Freigabe durch ihren Gateway-Administrator angeboten bekommen. Ein GitHub-Draft oder Prerelease allein stellt kein zulässiges OTA dar.

**Wichtige Migration von 2.2.5:** Bei einem noch nicht gekoppelten 2.2.5-Client kann ein korrekt konfiguriertes HTTPS-Gateway trotzdem `source_unavailable` verursachen. Der Fix in 2.2.8 kann nicht rückwirkend im alten Binary wirken. Ein legitimes Browser-Pairing oder einmaliges signiertes Setup als Initial-Upgrade ist nötig. Niemals eine Enrollment-Datei manipulieren, um einen Fallback zu erzwingen.

**Rollback:** Der Windows-Launcher und die GUI bieten die vorherige vollständige, überprüfte Generation als Rollback an. Eine fehlende oder beschädigte vorherige Generation darf nicht blind installiert werden. Das persistente Benutzer-/Enrollment-Profil befindet sich außerhalb der Programm-Slots und darf weder bei Update noch Rollback ausgetauscht werden. Ein echter In-App-OTA-Rollback-Feldtest von 2.2.8 steht bis zur dokumentierten QA-Abnahme aus.
