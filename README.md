# 🌤 Wetter App — v3.0

Eine mobile Wetter-App als einzelne HTML-Datei. Kein Server, keine Installation, keine API-Keys nötig. Einfach auf GitHub Pages hosten und im iPhone-Browser öffnen.

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

### 7-Tage-Tab
- Temperaturkurven Hoch/Tief als Liniengrafik
- 7-Tage-Liste mit Icon, Regenwahrscheinlichkeit & mm
- Schneeentwicklung als Balkendiagramm (nur Herbst/Winter)
- Wind- & Böenkurve für die Woche

### Radar-Tab
- 🌧 **Regenradar** — animiert, 14 Frames inkl. Nowcast-Prognose
- 🛰 **Satellit** — Infrarot-Satellitenbild (animierbar)
- 🌡 **Temperatur** — Heatmap über Europa
- ⚡ **Blitze** — Live-Blitzortung, alle 2 Min. aktualisiert
- 🇨🇭 **MeteoSwiss-Radar** — automatisch aktiv bei Schweizer Standort (siehe unten)
- Radar-Intensitäts-Legende

### Allgemein
- 🔍 **Ortssuche** — beliebigen Ort weltweit suchen
- 🌙 / ☀️ **Hell-/Dunkel-Modus** — wird gespeichert
- 📍 GPS-Standorterkennung mit Höhenangabe (m ü.M.)
- Alpiner Modus: Sonderdaten ab 800m, Hochalpin ab 1500m
- Saisonal angepasste Daten (Schnee nur Herbst/Winter)
- Versionsnummer im Header

---

## 🇨🇭 MeteoSwiss Hochauflösungs-Radar (Schweiz)

Wird der Standort innerhalb der Schweiz erkannt, wird automatisch der **MeteoSwiss CombiPrecip WMS-Layer** zusätzlich über den RainViewer-Radar eingeblendet:

| | RainViewer | MeteoSwiss CombiPrecip |
|---|---|---|
| **Auflösung** | ~5–10 km | **1 km** |
| **Aktualisierung** | 10 Min. | **5 Min.** |
| **Abdeckung** | Europa/Welt | Schweiz + Nachbarregionen |
| **Besonderheit** | Animation, Nowcast | Kombiniert Radar + Bodenstationen |
| **Alpine Täler** | Eingeschränkt | Optimiert für Alpentopographie |

Das MeteoSwiss-Radar wird automatisch ein- und ausgeblendet je nach Standort. Ein Badge im Radar-Header zeigt die aktive Datenquelle an.

> **Hinweis:** MeteoSwiss stellt derzeit noch keine animierte Zeitreihen-API bereit (geplant Ende 2026). Der MeteoSwiss-Layer zeigt daher immer den aktuellen Zeitpunkt; die Animation läuft weiterhin über RainViewer.

---

## 🌐 Verwendete APIs

| Dienst | Zweck | Kosten |
|--------|-------|--------|
| [Open-Meteo](https://open-meteo.com) | Wetterdaten & Vorhersage | Kostenlos (CC BY 4.0) |
| [RainViewer](https://www.rainviewer.com/api.html) | Radar & Satellitenbild (Europa/Welt) | Kostenlos |
| [MeteoSwiss / geo.admin.ch](https://wms.geo.admin.ch) | Hochauflösungs-Radar CH (WMS) | Kostenlos (Open Data) |
| [OpenWeatherMap](https://openweathermap.org) | Temperatur-Heatmap | Kostenlos (free tier) |
| [Blitzortung.org](https://www.blitzortung.org) | Blitzortung live | Kostenlos (non-commercial) |
| [Nominatim / OSM](https://nominatim.org) | Geocoding & Ortssuche | Kostenlos |
| [CartoDB](https://carto.com) | Kartenkacheln (Hell/Dunkel) | Kostenlos |

**Kein API-Key erforderlich** — alle Dienste funktionieren ohne Registrierung.

---

## 🚀 Installation

### GitHub Pages (empfohlen)
1. `index.html` in ein neues Repository hochladen (oder dieses forken)
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

## 🎨 Hell-/Dunkel-Modus

Der Modus wird per Knopf oben rechts (🌙 / ☀️) umgeschaltet und im Browser gespeichert — bleibt also auch nach dem Schliessen erhalten. Die Kartenkacheln wechseln ebenfalls zwischen dunklem und hellem CartoDB-Theme.

---

## 🗺 Standort & Datenschutz

- Der Standort wird **nur im Browser** verwendet und **nicht gespeichert**
- Es werden keine persönlichen Daten an Dritte übermittelt
- Die Wetter-APIs erhalten nur Koordinaten (Breitengrad/Längengrad)
- Der Hell-/Dunkel-Modus wird lokal im Browser gespeichert (`localStorage`)

---

## ⚠️ Bekannte Einschränkungen

- **Blitzortung:** Aufgrund von Browser-CORS-Einschränkungen kann die direkte Blitzortung-API blockiert sein. Die App fällt dann auf eine lokale Gewittererkennung basierend auf CAPE-Werten zurück.
- **MeteoSwiss-Animation:** Animierte Zeitreihen sind bei MeteoSwiss noch nicht als API verfügbar (geplant Ende 2026). Nur der aktuelle Zeitpunkt wird als Overlay gezeigt.
- **Standortzugriff:** Safari/Chrome fragt beim ersten Öffnen nach dem Standort — einmalig erlauben.
- **Offline:** Die App benötigt eine Internetverbindung für Wetterdaten und Karten.
- **Alpine Täler:** Radarsignale werden von Berggipfeln abgeschirmt — CombiPrecip von MeteoSwiss korrigiert dies teilweise durch Interpolation.

---

## 📄 Lizenz

Wetter-App Code: frei verwendbar für private Zwecke.  
Wetterdaten: Open-Meteo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)  
MeteoSwiss-Daten: [Open Government Data](https://www.meteoswiss.admin.ch/services-and-publications/service/open-data.html) — Quellenangabe: MeteoSwiss  
Radardaten: RainViewer (nur für private/nicht-kommerzielle Nutzung)  
Blitzdaten: Blitzortung.org (nur für private/nicht-kommerzielle Nutzung)
