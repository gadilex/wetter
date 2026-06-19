# 🌤 Wetter App — v3.0

Eine mobile Wetter-App als einzelne HTML-Datei. Kein Server, keine Installation, keine API-Keys nötig. Einfach auf GitHub Pages hosten und im iPhone-Browser öffnen.

---

## 📱 Features

### Jetzt-Tab
- Aktuelle Temperatur, Wetterlage, Gefühlstemperatur
- Animierter Windkompass mit Richtung & Geschwindigkeit
- Hoch-/Tieftemperatur des Tages
- Schneehöhe (Herbst/Winter & alpine Standorte)
- Sturmwarnung bei Böen über 60 km/h
- Gewitterwarnung via CAPE-Index (Sommer)
- Temperaturkurve als Liniengrafik (24h)
- Stündliche Vorhersage (scrollbar, 25h)
- Niederschlagsbalken mit mm-Angaben (24h)
- Detailkarten: Taupunkt, UV-Index, Bewölkung, Böen, Sichtweite, Luftdruck, Schneefall

### 7-Tage-Tab
- Temperaturkurven Hoch/Tief als Liniengrafik
- 7-Tage-Liste mit Icon, Regenwahrscheinlichkeit & mm
- Schneeentwicklung als Balkendiagramm (saisonal)
- Wind- & Böenkurve für die Woche

### Radar-Tab
- 🌧 **Regenradar** — animiert, 14 Frames, Nowcast-Prognose
- 🛰 **Satellit** — Infrarot-Satellitenbild (animierbar)
- 🌡 **Temperatur** — Heatmap über Europa
- ⚡ **Blitze** — Live-Blitzortung, alle 2 Min. aktualisiert
- Radar-Intensitäts-Legende

### Allgemein
- 🔍 **Ortssuche** — beliebigen Ort weltweit suchen
- 🌙 / ☀️ **Hell-/Dunkel-Modus** — wird gespeichert
- 📍 GPS-Standorterkennung
- Höhenerkennung mit alpinem Modus (> 800m / > 1500m)
- Saisonal angepasste Daten (Schnee nur Herbst/Winter)
- Versionsnummer im Header

---

## 🌐 Verwendete APIs

| Dienst | Zweck | Kosten |
|--------|-------|--------|
| [Open-Meteo](https://open-meteo.com) | Wetterdaten, Vorhersage | Kostenlos (CC BY 4.0) |
| [RainViewer](https://www.rainviewer.com/api.html) | Radar & Satellitenbild | Kostenlos |
| [OpenWeatherMap](https://openweathermap.org) | Temperatur-Heatmap | Kostenlos (free tier) |
| [Blitzortung.org](https://www.blitzortung.org) | Blitzortung | Kostenlos (non-commercial) |
| [Nominatim / OSM](https://nominatim.org) | Geocoding & Ortssuche | Kostenlos |
| [CartoDB](https://carto.com) | Kartenkacheln | Kostenlos |

**Kein API-Key erforderlich** — alle Dienste funktionieren ohne Registrierung.

---

## 🚀 Installation

### GitHub Pages (empfohlen)
1. Dieses Repository forken oder die `index.html` in ein neues Repo hochladen
2. **Settings → Pages → Branch: main → Save**
3. Nach 1–2 Minuten erreichbar unter:
   ```
   https://DEINNAME.github.io/REPONAME
   ```

### Als iPhone Home-App speichern
1. URL in Safari öffnen
2. Teilen-Symbol antippen
3. **„Zum Home-Bildschirm"** wählen
4. Die App erscheint wie eine native App auf dem Homescreen

---

## 📂 Dateistruktur

```
/
├── index.html   ← Die gesamte App (HTML + CSS + JS in einer Datei)
└── README.md    ← Diese Datei
```

---

## 🗺 Standort & Datenschutz

- Der Standort wird **nur im Browser** verwendet und **nicht gespeichert**
- Es werden keine persönlichen Daten an Dritte übermittelt
- Die Wetter-APIs erhalten nur Koordinaten (Breitengrad/Längengrad)
- Der Hell-/Dunkel-Modus wird lokal im Browser gespeichert (`localStorage`)

---

## ⚠️ Hinweise

- **Blitzortung:** Aufgrund von Browser-CORS-Einschränkungen kann die direkte Blitzortung-API blockiert sein. In diesem Fall zeigt die App eine lokale Gewittererkennung basierend auf CAPE-Werten.
- **Standortzugriff:** Safari/Chrome fragt beim ersten Öffnen nach dem Standort — einmalig erlauben.
- **Offline:** Die App benötigt eine Internetverbindung für Wetterdaten und Karten.

---

## 📄 Lizenz

Wetter-App Code: frei verwendbar für private Zwecke.  
Wetterdaten: Open-Meteo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)  
Radardaten: RainViewer (nur für private/nicht-kommerzielle Nutzung)  
Blitzdaten: Blitzortung.org (nur für private/nicht-kommerzielle Nutzung)
