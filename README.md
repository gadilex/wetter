# 🌤 Wetter App — v3.3

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
- Infokarte „MeteoSwiss Modell aktiv" bei Schweizer Standort

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
- 🇨🇭 **MeteoSwiss-Radar** — automatisch aktiv bei Schweizer Standort (1 km Auflösung)
- 📊 **Niederschlagsprognose 24h** — stündliche Balken + Liniengrafik + Zusammenfassung
- **Auto-Refresh** — Radar-Daten werden alle 5 Min. automatisch aktualisiert
- **⏭ Neuester Frame** — springt direkt zum aktuellsten Zeitpunkt
- **↻ Manueller Refresh** — sofortige Aktualisierung auf Knopfdruck
- Zeitstempel zeigt Stand der Daten an (z.B. „14 Frames · Stand 18:45")

### Allgemein
- 🔍 **Ortssuche** — beliebigen Ort weltweit suchen
- 🌙 / ☀️ **Hell-/Dunkel-Modus** — wird gespeichert
- 📍 GPS-Standorterkennung mit Höhenangabe (m ü.M.)
- Alpiner Modus: Sonderdaten ab 800m, Hochalpin ab 1500m
- Saisonal angepasste Daten (Schnee nur Herbst/Winter)
- Versionsnummer im Header

---

## 🇨🇭 MeteoSwiss — Schweizer Standort

Bei Standorten innerhalb der Schweiz wird automatisch auf die **MeteoSwiss ICON-CH Modelle** umgeschaltet:

| | Ausserhalb CH | In der Schweiz |
|---|---|---|
| **Wetterdaten** | Open-Meteo best_match | MeteoSwiss ICON-CH1 + ICON-CH2 |
| **Auflösung** | ~5–10 km | **1 km (CH1) / 2.1 km (CH2)** |
| **Kurzfrist (0–33h)** | Bestes verfügbares Modell | ICON-CH1-EPS (1 km) |
| **Mittelfrist (2–5 Tage)** | Bestes verfügbares Modell | ICON-CH2-EPS (2.1 km) |
| **Aktualisierung** | je nach Modell | alle 3h (CH1) / 6h (CH2) |
| **Radar** | RainViewer | RainViewer + MeteoSwiss CombiPrecip |
| **Radar-Auflösung** | ~5–10 km | **1 km** |

Der aktive Modelname wird im Header (`🇨🇭 ICON-CH1/2`) und als Chip im Jetzt-Tab angezeigt.

> **Hinweis:** MeteoSwiss Radardaten sind aktuell statisch (kein animierter Forecast). Animierte Zeitreihen-API geplant für Ende 2026.

---

## 📊 Niederschlagsprognose (Radar-Tab)

Direkt unter der Radarkarte zeigt die App eine **standortgenaue 24h-Regenprognose**:

| Element | Beschreibung |
|---------|-------------|
| **Wahrscheinlichkeits-Balken** | Stündlich · blau = Regen · blau-weiß = Schnee · grau = trocken |
| **mm-Beschriftung** | Erwartete Niederschlagsmenge pro Stunde |
| **Liniengrafik** | mm/h-Verlauf als Kurve |
| **Zusammenfassung** | „Regen in 2h", „Kein Niederschlag" oder „Regen fällt gerade" |
| **Detailangaben** | Gesamtmenge · Regenstunden · Intensität |

---

## 🔄 Radar Auto-Refresh (v3.1)

Der Radar aktualisiert sich jetzt automatisch:

- **Alle 5 Minuten** werden neue Frames von RainViewer geladen (sofern keine Animation läuft)
- **↻ Button** — sofortiger manueller Refresh
- **⏭ Button** — springt zum neuesten verfügbaren Frame
- Der **Zeitstempel** im Header zeigt immer den Stand der geladenen Daten an
- Nach einem Refresh wird automatisch der neueste Frame angezeigt

---

## 🌐 Verwendete APIs

| Dienst | Zweck | Kosten |
|--------|-------|--------|
| [Open-Meteo](https://open-meteo.com) | Wetterdaten & Vorhersage (Welt) | Kostenlos (CC BY 4.0) |
| [Open-Meteo MeteoSwiss](https://open-meteo.com/en/docs/meteoswiss-api) | ICON-CH1/CH2 für die Schweiz | Kostenlos (CC BY 4.0) |
| [RainViewer](https://www.rainviewer.com/api.html) | Radar & Satellitenbild | Kostenlos |
| [MeteoSwiss / geo.admin.ch](https://wms.geo.admin.ch) | CombiPrecip WMS CH (Radar-Overlay) | Kostenlos (Open Data) |
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

Umschalten per 🌙 / ☀️ Knopf oben rechts. Wird gespeichert. Kartenkacheln wechseln ebenfalls (CartoDB dark/light).

---

## 🗺 Standort & Datenschutz

- Standort wird **nur im Browser** verwendet, **nicht gespeichert**
- Keine persönlichen Daten an Dritte
- APIs erhalten nur Koordinaten (lat/lon)
- Hell-/Dunkel-Modus gespeichert via `localStorage`

---

## ⚠️ Bekannte Einschränkungen

- **Radar-Forecast:** Animierte Regenfront-Prognose über mehrere Stunden ist in der kostenlosen RainViewer-API nicht enthalten. Ersatz: standortgenaue 24h-Prognose via Open-Meteo.
- **MeteoSwiss Radar-Animation:** Zeitreihen-API geplant Ende 2026.
- **Blitzortung CORS:** Direkte API kann im Browser blockiert sein → Fallback auf CAPE-basierte Erkennung.
- **Standortzugriff:** Einmalig in Safari/Chrome erlauben.
- **Alpine Täler:** Radarsignale werden von Gipfeln abgeschirmt — MeteoSwiss CombiPrecip korrigiert dies teilweise.
- **Offline:** Internetverbindung erforderlich.

---

## 📋 Changelog

### v3.3
- Fix: Cache-Busting für RainViewer JSON (`cache: no-store` + Timestamp-Parameter)
- Fix: Browser cached keine alten Radar-Frames mehr
- Neu: Zeitstempel zeigt Alter des Frames in Minuten (z.B. „18:45 (3 Min. alt)")
- Neu: Fehlertext im Radar-Header bei Ladefehler verbessert
- Versionsnummer erhöht

### v3.2
- Fix: Korrekter Open-Meteo Endpoint (`/v1/forecast` statt `/v1/meteoswiss`)
- Fix: Korrekter Modellname (`meteoswiss_icon_ch1/ch2` statt `icon_ch1/ch2`)
- Neu: Automatischer Fallback auf `best_match` wenn MeteoSwiss nicht verfügbar
- Neu: Fallback-Status sichtbar im Header und Jetzt-Tab (⚠ Fallback)
- Versionsnummer erhöht

### v3.1
- Radar Auto-Refresh alle 5 Minuten
- ⏭ Button: springt zum neuesten Frame
- ↻ Button: manueller Radar-Refresh
- Zeitstempel zeigt Stand der Radardaten
- Alte Radar-Layer werden korrekt entfernt beim Refresh
- Versionsnummer erhöht

### v3.0
- MeteoSwiss ICON-CH1/CH2 für Schweizer Standorte
- Hell-/Dunkel-Modus mit Speicherung
- Ortssuche weltweit
- Niederschlagsprognose 24h im Radar-Tab
- MeteoSwiss CombiPrecip Radar-Overlay (CH)
- Blitzortung, Satellit, Temperatur-Heatmap
- Windkompass, Sparklines, alpine Erkennung

---

## 📄 Lizenz

Wetter-App Code: frei verwendbar für private Zwecke.
Wetterdaten: Open-Meteo [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
MeteoSwiss-Daten: [Open Government Data](https://www.meteoswiss.admin.ch/services-and-publications/service/open-data.html) — Quellenangabe: MeteoSwiss
Radardaten: RainViewer (nur für private/nicht-kommerzielle Nutzung)
Blitzdaten: Blitzortung.org (nur für private/nicht-kommerzielle Nutzung)
