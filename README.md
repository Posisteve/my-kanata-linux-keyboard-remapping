# Kanata Key Remapping Configuration

![Kanata](https://img.shields.io/badge/Kanata-v1.12.0-blue)
![Linux](https://img.shields.io/badge/OS-Linux-green)
![Windows](https://img.shields.io/badge/OS-Windows-blue)

Dieses Repository enthält benutzerdefinierte Tastaturbelegungen für **Kanata** – einen leistungsstarken Key-Mapper für Linux und Windows.

## Was macht dieses Skript?

Das Script `start_kanata.sh` startet Kanata mit der Konfigurationsdatei `configs/steve_remap.kbd`. Es:

1. **Lädt die benutzerdefinierte Tastaturbelegung**
2. **Aktiviert QWERTZ mit deutschen Umlauten** (ä, ü, ö, ß)
3. **Konfiguriert Tap-Hold-Modifikationen** für effizientes Tippen
4. **Aktiviert einen Neo2-Layer** mit Navigationstasten
5. **Protokolliert alle Aktivitäten** nach `/var/log/kanata.log`

## Dateien

| Datei | Plattform | Beschreibung |
|-------|-----------|--------------|
| `configs/steve_remap.kbd` | Linux | Hauptkonfiguration für Linux |
| `configs/steve_remap_win.kbd` | Windows | Windows-Version mit AltGr-Fix |

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

## Windows-Unterschiede

Die Windows-Version (`steve_remap_win.kbd`) unterscheidet sich nur in **einer Zeile**, ist aber **zwangsläufig notwendig**:

```kotlin
windows-altgr cancel-lctl-press
```

**Warum?** Ohne diesen Fix sendet AltGr immer `Strg` mit, wodurch `Backspace` zu `Strg + Backspace` wird. Das betrifft nur Windows 11 und erfordert Kanata v1.12.0+.

## Installation

### Voraussetzungen

- Linux (x64)
- Kanata v1.10.1 oder höher
- Root-Rechte (für Tastatur-Intercept)

### Setup (Linux)

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

### Setup (Windows)

1. Kanata v1.12.0+ installieren
2. `configs/steve_remap_win.kbd` verwenden
3. Kanata mit dieser Konfiguration starten

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
├── start_kanata.sh        # Startscript für Kanata (Linux)
└── configs/
    ├── steve_remap.kbd    # Linux-Konfiguration
    └── steve_remap_win.kbd # Windows-Konfiguration (mit AltGr-Fix)
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

Keine Lizenz angegeben – frei für jeden verwendbar.
