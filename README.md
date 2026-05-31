# Sommersprint App – Smart-Sanierungs-Assistent (Prototyp)

Die **Sommersprint App** ist ein intuitiver, mobiler Sanierungs-Assistent, der speziell für den Baustellenalltag entwickelt wird[span_1](start_span)[span_1](end_span). Ziel des Projekts ist es, die Digitalisierungslücke im Handwerk zu schließen und komplexe BIM-Planungsprozesse (Building Information Modeling) so einfach wie ein Zeichentool zu machen – direkt auf dem Smartphone und ohne CAD-Studium[span_2](start_span)[span_2](end_span).

Dieser Prototyp wurde als Web-App umgesetzt und dient zur Validierung der Kernfunktionen rund um die Raum- und Gewerkebasierte Leitungsplanung[span_3](start_span)[span_3](end_span).

---

## 🚀 Kernfunktionen des Prototyps

Der aktuelle Entwicklungsstand zeigt bereits die grundlegende Navigation und die wichtigsten Planungs-Schritte:

### 1. Gewerkewahl & Übersicht
* **Auswahl des Arbeitsbereichs:** Flexibler Einstieg über die Gewerke **Heizung**, **Elektro**, **Sanitär** oder **Sonstiges** (siehe `1000038203.jpg`)[span_4](start_span)[span_4](end_span).
* **Layer-System:** Jedes Gewerk erhält eine eigene Ebene, um Überschneidungen und Planungsfehler zu minimieren[span_5](start_span)[span_5](end_span).

### 2. Grundriss- & Raumverwaltung
* **Gebäude-Struktur:** Navigation durch Stockwerke (UG, EG, OG) und Räume (siehe `1000038204.jpg`).
* **Interaktive Raumansicht:** Visualisierung einzelner Räume (z. B. Küche, Wohnzimmer) mit exakter Bemaßung, Wandsegmenten, Fenstern und Türen (siehe `1000038245.jpg`)[span_6](start_span)[span_6](end_span).

### 3. Wand-Planungstool (2D-Canvas)
* **Intuitives Zeichnen:** Über eine Raster-Leinwand können Leitungen direkt auf die Wand projiziert werden (siehe `1000038206.jpg`, `1000038207.jpg`).
* **Parametrisierung:** Schieberegler zur präzisen Einstellung von Verlegehöhe, Verlegetiefe und Raummaßen (siehe `1000038208.jpg`)[span_7](start_span)[span_7](end_span).
* **Intelligente Werkzeuge:** Integration von Bauteilen wie Rohren (z. B. DN 22), Winkeln, T-Stücken, Heizkörpern (HK), Fußbodenheizung (FBH), Pumpen und Ventilen (siehe `1000038207.jpg`)[span_8](start_span)[span_8](end_span).

### 4. Integrierte Materialliste & Logistik
* **Automatische Mengenermittlung:** Das System erfasst im Hintergrund verplante Materialien wie Kupfer- oder Verbundrohre sowie Formteile (siehe `1000038205.jpg`)[span_9](start_span)[span_9](end_span).
* **Lagerort-Zuweisung:** Möglichkeit zur direkten Verknüpfung mit einem virtuellen Regalsystem (z. B. "Regal B3") für eine optimierte Baustellenlogistik (siehe `1000038208.jpg`)[span_10](start_span)[span_10](end_span).

---

## 🛠️ Geplante Features & Bildungskonzept

Für die finale Version der App sind folgende Erweiterungen vorgesehen[span_11](start_span)[span_11](end_span):
* **Automatisches Fitting & Snapping:** Intelligentes Einrasten von Rohren und automatisches Setzen von Winkeln[span_12](start_span)[span_12](end_span).
* **Echtzeit-Kollisionsprüfung:** Warnung, wenn sich Leitungen verschiedener Gewerke überschneiden[span_13](start_span)[span_13](end_span).
* **BIM-Export:** Brückenfunktion zur Übersetzung der Zeichnungen in standardisierte Planersprache (Export als IFC, JSON, UGL)[span_14](start_span)[span_14](end_span).
* **Didaktisches Scaffolding:** Einsatz der App in der Berufsschule als interaktiver Lern-Assistent ("Lücken-Methodik" für Auszubildende im Handwerk)[span_15](start_span)[span_15](end_span).

---

## 💻 Technische Basis des Prototyps

* **Frontend:** HTML5, CSS3, JavaScript / TypeScript
* **Rendering:** HTML5 Canvas für die 2D-Zeichenflächen (`1000038206.jpg`)[span_16](start_span)[span_16](end_span)
* **Hosting:** GitHub Pages (`-art-coder.github.io`)

---

## ⚠️ Status des Prototyps

> **Hinweis:** Dies ist ein fortlaufendes Projekt ("Work in Progress"). Der Code wurde initial mithilfe von KI-Unterstützung (Claude) generiert, um die Benutzeroberfläche und den Workflow schnell greifbar zu machen. Einige Funktionen sind aktuell noch rein visuelle Platzhalter und werden in kommenden Sprints funktional ausgebaut[span_17](start_span)[span_17](end_span).
> 
