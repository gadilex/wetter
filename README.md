# 🌤 Wetter App — v4.1

Eine mobile Wetter-App als einzelne HTML-Datei. Kein Server, keine Installation, keine API-Keys nötig. Einfach auf GitHub Pages hosten und im iPhone-Browser öffnen.

> **v4.1 — Stabilitäts-Release:** Robuste Behandlung fehlender Daten, vereinfachtes Schweiz-Modell, kein „NaN" mehr in der Anzeige.

---

## 📱 Features

### Jetzt-Tab
- Aktuelle Temperatur, Wetterlage, Gefühlstemperatur
- Animierter Windkompass mit Richtung & Geschwindigkeit
- Hoch-/Tieftemperatur des Tages
- Schneehöhe (Herbst/Winter & alpine Standorte > 800m)
- Sturmwarnung bei Böen über 60 km/h
- Gewitterwarnung via CAPE-Index (Sommer)
- Temperaturkurve als Liniengrafik (24h)
- Stündliche Vorhersage (scrollbar, 25h) mit mm-Angaben
- Niederschlagsbalken mit mm-Werten (24h)
- Detailkarten: Taupunkt, UV-Index, Bewölkung, Böen (Bft), Sichtweite, Luftdruck, Schneefall
- Bei Schweizer Standort: MeteoSwiss ICON-CH1/CH2 Modell (1km Auflösung)

### 7-Tage-Tab
- Temperaturkurven Hoch/Tief als Liniengrafik
- 7-Tage-Liste mit Icon, Regenwahrscheinlichkeit & mm
- Schneeentwicklung als Balkendiagramm (nur Herbst/Winter)
- Wind- & Böenkurve für die Woche

### Radar-Tab
- 🌧 **Regenradar** — animiert, inkl. Kurzprognose (Nowcast)
- 🛰 **Satellit** — Infrarot-Satellitenbild (animierbar)
- Play / Vor / Zurück / Aktualisieren
- 📊 **Niederschlagsprognose 24h** — Balken + Liniengrafik + Zusammenfassung
- Radar-Intensitäts-Legende

### Allgemein
- 🔍 **Ortssuche** — beliebigen Ort weltweit suchen
- 🌙 / ☀️ **Hell-/Dunkel-Modus** — wird gespeichert
- 📍 GPS-Standorterkennung mit Höhenangabe (m ü.M.)
- Alpiner Modus: Sonderdaten ab 800m, Hochalpin ab 1500m
- Saisonal angepasste Daten (Schnee nur Herbst/Winter)

---

## 🇨🇭 MeteoSwiss — Schweizer Standort

Bei Standorten innerhalb der Schweiz nutzt die App automatisch die **MeteoSwiss ICON-CH Modelle** (über Open-Meteo):

| | Ausserhalb CH | In der Schweiz |
|---|---|---|
| **Modell** | Open-Meteo best_match | MeteoSwiss ICON-CH2 |
| **Auflösung** | ~5–10 km | **2.1 km** |
| **Vorhersage** | bis 8 Tage | bis 7 Tage (ICON-CH2-EPS) |

**Warum nur noch ICON-CH2 (statt CH1+CH2)?** Das Kombinieren zweier Modelle erzeugte gelegentlich Inkonsistenzen an der Übergangsstelle. Ein einzelnes Modell (ICON-CH2, 2.1 km, volle 5–7 Tage) ist zuverlässiger und immer noch deutlich präziser als globale Modelle.

Fällt MeteoSwiss aus oder liefert keine Kerndaten, schaltet die App automatisch auf `best_match` zurück (sichtbar als ⚠ Fallback im Header).

---

## 🗑 In v4.0 entfernt (funktionierten nicht zuverlässig)

| Entfernt | Grund |
|----------|-------|
| **Blitze (Blitzortung.org)** | CORS-Blockierung im Browser — funktionierte nie wirklich, nur simulierter Fallback |
| **Temperatur-Heatmap** | Benötigte fremden OpenWeatherMap-Key, der jederzeit gesperrt werden kann |
| **MeteoSwiss Radar-WMS-Overlay** | `wms.geo.admin.ch` lud unzuverlässig / langsam, Layer-Name veraltet |

Das **MeteoSwiss-Wettermodell** (ICON-CH über Open-Meteo) bleibt — das funktioniert sauber und ist etwas anderes als der entfernte Radar-WMS.

---

## 📊 Niederschlagsprognose (Radar-Tab)

Standortgenaue 24h-Regenprognose direkt unter der Karte:

| Element | Beschreibung |
|---------|-------------|
| **Wahrscheinlichkeits-Balken** | Stündlich · blau = Regen · blau-weiß = Schnee |
| **mm-Beschriftung** | Erwartete Niederschlagsmenge pro Stunde |
| **Liniengrafik** | mm/h-Verlauf als Kurve |
| **Zusammenfassung** | „Regen in 2h", „Kein Niederschlag" etc. |

---

## 🌐 Verwendete APIs (alle kostenlos, ohne API-Key)

| Dienst | Zweck |
|--------|-------|
| [Open-Meteo](https://open-meteo.com) | Wetterdaten, Vorhersage, Niederschlagsprognose (inkl. MeteoSwiss ICON-CH) |
| [RainViewer](https://www.rainviewer.com/api.html) | Regenradar & Satellitenbild |
| [Nominatim / OSM](https://nominatim.org) | Geocoding & Ortssuche |
| [CartoDB](https://carto.com) | Kartenkacheln (Hell/Dunkel) |
| [Leaflet](https://leafletjs.com) | Kartenbibliothek (via CDN) |

---

## 🚀 Installation

### GitHub Pages
1. `index.html` in ein neues Repository hochladen
2. **Settings → Pages → Branch: main → Save**
3. Nach 1–2 Minuten erreichbar unter `https://DEINNAME.github.io/REPONAME`

### Als iPhone Home-App
1. URL in Safari öffnen
2. Teilen-Symbol → **„Zum Home-Bildschirm"**

---

## 📂 Dateistruktur

```
/
├── index.html   ← Die gesamte App (HTML + CSS + JS in einer Datei)
└── README.md    ← Diese Datei
```

---

## ⚠️ Hinweise

- **Radar-Datenfenster:** RainViewer zeigt die letzten ~2h plus Kurzprognose. Der Zeitbereich verschiebt sich laufend mit der Echtzeit.
- **Standortzugriff:** Beim ersten Öffnen in Safari/Chrome einmalig erlauben.
- **Offline:** Internetverbindung erforderlich.

---

## 📋 Changelog

### v4.1 — Stabilitäts-Release
- Robuste Behandlung fehlender Daten: Felder die MeteoSwiss nicht liefert (z.B. Sichtweite, UV) werden ausgeblendet statt „NaN" anzuzeigen
- Schweiz vereinfacht: nur noch ICON-CH2 (ein Modell, keine Merge-Fehler mehr)
- Wochenansicht nutzt tatsächliche Anzahl Tage (kein Absturz bei kürzeren Vorhersagen)
- Sanity-Check: bei fehlenden Kerndaten automatischer Fallback
- Alle Render-Funktionen gegen null/undefined abgesichert

### v4.0 — Aufräum-Release
- Entfernt: Blitze, Temperatur-Heatmap, MeteoSwiss Radar-WMS (alle unzuverlässig)
- Toten Code, ungenutzte CSS-Regeln und Variablen entfernt
- Dateigröße von ~71 KB auf ~60 KB reduziert
- JavaScript-Syntax & alle Element-Referenzen validiert
- Nur noch 5 stabile Datenquellen, alle ohne API-Key
- MeteoSwiss ICON-CH Wettermodell bleibt (funktioniert sauber)

### v3.x
- Radar Auto-Refresh, Cache-Fixes, DWD-Experiment (verworfen)
- MeteoSwiss ICON-CH Integration, Hell-/Dunkel-Modus
- Ortssuche, Niederschlagsprognose, Windkompass, Sparklines

---

## 📄 Lizenz

Wetter-App Code: frei verwendbar für private Zwecke.
Wetterdaten: Open-Meteo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
MeteoSwiss-Daten: Open Government Data — Quellenangabe: MeteoSwiss
Radardaten: RainViewer (nur private/nicht-kommerzielle Nutzung)
