# Winterstromlücke Schweiz 2050

**Interaktive Parameteranalyse der Studie Kelevitz et al., *Energies* 2025**

[![Lizenz: MIT](https://img.shields.io/badge/Lizenz-MIT-blue.svg)](LICENSE)
[![Lizenz: CC BY 4.0](https://img.shields.io/badge/Daten%20%26%20Docs-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Studie: DOI](https://img.shields.io/badge/DOI-10.3390%2Fen18215601-green.svg)](https://doi.org/10.3390/en18215601)
[![GitHub Pages](https://img.shields.io/badge/Demo-GitHub%20Pages-orange.svg)](https://NousWorksHQ.github.io/Winterstromluecke-2050)

---

## Über diese Anwendung

Diese Web-App veranschaulicht, wie Massnahmen im Schweizer Gebäudesektor die projizierte **Winterstromlücke von 2050** beeinflussen. Vier Parameter können interaktiv variiert werden; das Simulationsergebnis aktualisiert sich in Echtzeit.

[Demo Web-App](https://NousWorksHQ.github.io/Winterstromluecke-2050)

### Studienbasis

> Kelevitz K., Haller M., Frommelt M., Meier B. —  
> *Influence of Scenarios for Space Heating and Domestic Hot Water in Buildings on the Winter Electricity Demand of Switzerland in 2050.*  
> Institut für Solartechnik SPF, Ostschweizer Fachhochschule OST, Rapperswil.  
> **Energies 2025, 18, 5601.** https://doi.org/10.3390/en18215601

Die Studie erweitert das Energiesystem-Werkzeug **PowerCheck** (https://powercheck.ch) um ein Bottom-up-Modell des Schweizer Gebäudeparks (60 Kategorien, stündliche Auflösung, GWR-Datenbasis). Zwölf Szenarien variieren vier Parameter und quantifizieren deren Einfluss auf die saisonale Stromlücke. Ausgangspunkt: **Energieperspektiven 2050+** des Bundesamts für Energie (BFE).

---

## Funktionen

- **Vier interaktive Parameter** mit je 3–4 Stufen:
  1. Sanierungsrate Gebäudehülle / Jahr (0.5 % / 1.1 % / 1.5 % / 2.0 %)
  2. Warmwasser-Wärmerückgewinnung (0 % / 20 % / 50 %)
  3. Anteil Erdsonden-Wärmepumpen (20 % / 50 % / 80 %)
  4. Angenommene Klimaerwärmung (+0 °C / +1 °C / +2 °C / +3 °C)
- **Echtzeit-Berechnung** der Winterstromlücke in TWh
- **Szenarien-Vergleichsdiagramm** (Chart.js) mit Referenzwerten aus der Studie
- **Dynamische Zusammenfassung** der aktiven Parameter
- **Keine Abhängigkeiten** ausser Chart.js (CDN); keine Build-Pipeline erforderlich

---

## Schnellstart

### Lokal öffnen

```bash
# Repository klonen
git clone https://github.com/USERNAME/Winterstromluecke-2050.git
cd winterstromluecke-2050

# index.html direkt im Browser öffnen – kein Server nötig
open index.html          # macOS
xdg-open index.html      # Linux
start index.html         # Windows
```

---

## Deployment auf GitHub Pages

1. Repository auf GitHub erstellen (öffentlich oder privat mit Pages-Berechtigung)
2. `index.html` im Root-Verzeichnis belassen
3. GitHub → Settings → Pages → Source: **Deploy from branch** → `main` / `root`
4. Die App ist danach unter `https://USERNAME.github.io/Winterstromluecke-2050` erreichbar

---

## Modellhinweise

Die Winterstromlücke wird als additive Kombination der publizierten Einzelszenario-Werte berechnet:

| Parameter | Stufe | Δ gegenüber Basis (TWh) |
|-----------|-------|------------------------|
| Sanierung | 0.5 %/a | +3.2 |
| Sanierung | 1.1 %/a (Basis) | 0 |
| Sanierung | 1.5 %/a | −2.14 |
| Sanierung | 2.0 %/a | −4.70 |
| WW-WRG | 20 % | −0.10 |
| WW-WRG | 50 % | −0.25 |
| Erdsonden-WP | 50 % | −0.15 |
| Erdsonden-WP | 80 % | −0.30 |
| Klima | +1 °C | −0.25 |
| Klima | +2 °C | −0.45 |
| Klima | +3 °C | −0.65 |

**Basis:** 10.7 TWh (PowerCheck-Simulation, EP2050+ Szenario, Kelevitz et al. 2025, Abschn. 3.1)

Abweichungen gegenüber den in der Studie publizierten Kombinationsszenarien (Com1/Com2, Fig. 8) betragen aufgrund der additiven Näherung ≤ 5 %.

---

## Referenzwerte im Diagramm

| Szenario | Winterstromlücke 2050 |
|----------|----------------------|
| Tiefe Sanierung (0.5 %/a) | 13.9 TWh |
| EP2050+ Basis (1.1 %/a) | 10.7 TWh |
| BFE-Schätzung EP2050+ | 9.0 TWh |
| Optimum Sanierung (2.0 %/a) | 6.0 TWh |

Quelle für alle Werte: Kelevitz et al. 2025, Fig. 8 und Abschn. 3.1–3.2.

---

## Technologie

| Komponente | Beschreibung |
|-----------|-------------|
| `index.html` | Einzel-Datei-Anwendung, kein Build-Schritt |
| [Chart.js 4.4.1](https://www.chartjs.org) | Balkendiagramm (CDN) |
| [DM Sans](https://fonts.google.com/specimen/DM+Sans) | Schriftart (Google Fonts CDN) |
| [IBM Plex Mono](https://fonts.google.com/specimen/IBM+Plex+Mono) | Zahlendarstellung (Google Fonts CDN) |

Die Anwendung funktioniert vollständig offline, sobald die Schriften und Chart.js einmalig geladen wurden (Browser-Cache).

---

## Lizenz

Der Quellcode in diesem Repository steht unter der [MIT-Lizenz](LICENSE).  
Daten, Ergebnisse und Dokumentation stehen unter [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Der wissenschaftliche Inhalt (Simulationsdaten, Szenariowerte) basiert auf der Open-Access-Publikation Kelevitz et al. 2025 (CC BY 4.0): [https://doi.org/10.3390/en18215601](https://doi.org/10.3390/en18215601)

---

## Zitation

Wenn Sie diese Visualisierung verwenden, zitieren Sie bitte die Originalstudie:

```
Kelevitz, K.; Haller, M.; Frommelt, M.; Meier, B.
Influence of Scenarios for Space Heating and Domestic Hot Water in Buildings
on the Winter Electricity Demand of Switzerland in 2050.
Energies 2025, 18, 5601. https://doi.org/10.3390/en18215601
```
