# Kanata Key Remapping Configuration

![Kanata](https://img.shields.io/badge/Kanata-v1.12.0-blue)
![Linux](https://img.shields.io/badge/OS-Linux-green)

Dieses Repository enthält eine benutzerdefinierte Tastaturbelegung für **Kanata** – einen leistungsstarken Key-Mapper für Linux.

## Was macht dieses Skript?

Das Script `start_kanata.sh` startet Kanata mit der Konfigurationsdatei `configs/steve_remap.kbd`. Es:

1. **Lädt die benutzerdefinierte Tastaturbelegung**
2. **Aktiviert QWERTZ mit deutschen Umlauten** (ä, ü, ö, ß)
3. **Konfiguriert Tap-Hold-Modifikationen** für effizientes Tippen
4. **Aktiviert einen Neo2-Layer** mit Navigationstasten
5. **Protokolliert alle Aktivitäten** nach `/var/log/kanata.log`

## Konfigurationsübersicht

### Basis-Layout (QWERTZ)

- Deutsche Umlaute: `ä`, `ü`, `ö`, `ß` als Hold-Keys
- Standard QWERTZ-Belegung mit erweiterten Funktionen

### Tap-Hold-Modifikationen

| Taste | Tap | Hold |
| ----- | --- | ---- |
| `a`   | `a` | `ä`  |
| `u`   | `u` | `ü`  |
| `o`   | `o` | `ö`  |
| `s`   | `s` | `ß`  |
| `)`   | `(` | `)`  |
| `]`   | `{` | `}`  |
| `[`   | `[` | `]`  |
| `,`   | `<` | `>`  |
| `-`   | `-` | `+`  |
| `'`   | `'` | `"`  |
| `;`   | `:` | `;`  |
| `4`   | `$` | `$`  |

### Neo2-Layer 3 (aktivierbar)

- Navigation: `Home`, `End`, `Pfeiltasten`
- Bearbeitung: `Del`, `Backspace`, `Cut`, `Copy`, `Paste`
- Sonderzeichen: `=`, `/`, `-`

### Chords (Tastenkombinationen)

- `J + K + L` → `Enter`
- `U + I + O` → `Tab`

## Installation

### Voraussetzungen

- Linux (x64)
- Kanata v1.10.1 oder höher
- Root-Rechte (für Tastatur-Intercept)

### Setup

```bash
# Repository klonen
git clone <repository-url>
cd stevolution

# Kanata herunterladen (falls nicht vorhanden)
wget https://github.com/jtroo/kanata/releases/download/v1.12.0/linux-binaries-x64.zip
unzip linux-binaries-x64.zip -d ~/apps/kanata/

# Berechtigungen setzen
chmod +x start_kanata.sh
```

## Verwendung

### Starten

```bash
./start_kanata.sh
```

### Stoppen

```bash
sudo pkill kanata
```

### Logs anzeigen

```bash
tail -f /var/log/kanata.log
```

## Dateistruktur

```
stevolution/
├── README.md              # Diese Datei
├── start_kanata.sh        # Startscript für Kanata
└── configs/
    └── steve_remap.kbd    # Hauptkonfiguration
```

## Technische Details

### Kanata-Konzept

Kanata interceptiert Tastendrücke auf Low-Level und ermöglicht:

- **Tap-Hold**: Schnelles Tippen vs. Modifikator-Halten
- **Layers**: Verschiedene Belegungen pro Taste
- **Chords**: Mehrfachbelegungen durch gleichzeitiges Drücken
- **Unicode**: Direkte Eingabe von Sonderzeichen

### Konfigurationsparameter

- `tap_time`: 200ms (Zeit für Tap vs. Hold)
- `hold_time`: 200ms
- `combo_time`: 60ms (Chord-Timing)

## Links

- [Kanata GitHub Repository](https://github.com/jtroo/kanata)
- [Kanata Releases](https://github.com/jtroo/kanata/releases)
- [Kanata Dokumentation](https://github.com/jtroo/kanata/blob/master/docs/README.md)

## Lizenz

N/A
