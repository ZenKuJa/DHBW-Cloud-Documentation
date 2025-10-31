# DHBW Cloud: Instanz erstellen und per SSH verbinden

> Diese Anleitung beschreibt die Einrichtung in der DHBW Cloud, inkl. Abweichungen zum Video (Netzwerkwahl und Startadresse).

---

## Voraussetzungen

- **Netzwerkzugang:** Verbindung zum DHBW‑Hochschulnetz per Kabel, WLAN oder VPN.
- **Zugangsdaten:** Benutzername und Passwort für die DHBW Cloud.
- **SSH-Client:** Terminal mit installiertem SSH (z. B. unter Linux/macOS standardmäßig, unter Windows via PowerShell oder Windows Terminal).

---

## Schritt-für-Schritt Anleitung

1. **Cloud-Webseite öffnen:** Rufen Sie die Seite `http://dhbw.cloud` auf.
2. **Anmelden:** Geben Sie Ihren Benutzernamen und Ihr Passwort ein.
3. **Schlüsselpaare öffnen:** Links im Menü „Compute → Schlüsselpaare“ auswählen.
4. **Schlüsselpaar erstellen:** „Schlüsselpaar erstellen“ anklicken.
5. **Schlüsseltyp wählen:** Namen vergeben und als Schlüsseltyp „SSH“ auswählen.
6. **Datei speichern:** Die Schlüsseldatei mit der Endung `.pem` speichern.
7. **Datei verschieben:** Die `.pem`-Datei in einen passenden Ordner auf Ihrem System verschieben.
8. **Sicherheitsgruppen öffnen:** Links im Menü „Netzwerk → Sicherheitsgruppen“ auswählen.
9. **Default-Gruppe verwalten:** Bei der Sicherheitsgruppe „default“ auf „Regeln verwalten“ klicken.
10. **SSH-Regel hinzufügen:** „Regel hinzufügen“ wählen und als Regeltyp „SSH“ hinzufügen.
11. **Compute → Instanzen:** Links im Menü „Compute → Instanzen“ öffnen.
12. **Instanz starten:** „Instanz starten“ auswählen.
13. **Instanz benennen:** Einen Namen vergeben und „Weiter“ klicken.
14. **Abbild wählen:** Unter „Verfügbare Abbilder“ ein Image auswählen (z. B. „Ubuntu Server 22.04“ oder „24.04“) und „Weiter“.
15. **Instanzgröße wählen:** Unter „Verfügbare Instanzgrößen“ eine Größe wählen (z. B. `gp1.small`) und „Weiter“.
16. **Netzwerk wählen:** Das Netzwerk „DHBW“ auswählen und „Weiter“.
17. **Optionen prüfen:** Sie können die weiteren Reiter ansehen, jeweils „Weiter“ klicken.
18. **Instanz erzeugen:** Mit „Instanz starten“ die Erstellung auslösen.
19. **Warten:** Einige Minuten warten, bis die Instanz verfügbar ist (prüfen unter „Cloud → Instanzen“).
20. **Terminal öffnen:** Ein lokales Terminal mit SSH-Client starten.
21. **SSH-Verbindung herstellen:** Mit Ihrem Schlüssel und der IP der Instanz verbinden (siehe Beispiel unten).
22. **System aktualisieren:** Betriebssystem aktualisieren und benötigte Software installieren.

---

## SSH-Verbindung herstellen

```bash
ssh -i /Pfad/zum/Schluessel/mein-key.pem ubuntu@<IP-ADRESSE-DER-INSTANZ>
```

## Schlüsselrechte anpassen (falls nötig)

```bash
chmod 600 /Pfad/zum/Schluessel/mein-key.pem
```

## Mögliche Schlüsselpaare für Instanz anpassen

```bash
nano ./.ssh/authorized_keys
```

## System aktualisieren

Wenn Sie mit der Instanz per SSH verbunden sind, sollten sie zunächst das Betriebssystem aktualisieren.

Für Ubuntu gelten folgende Befehle:

Paketquellen aktualisieren und System updaten:

```bash
sudo apt update
sudo apt upgrade -y
```

_Optional: nützliche Basiswerkzeuge installieren_

```bash
sudo apt install -y build-essential curl git htop unzip
```
