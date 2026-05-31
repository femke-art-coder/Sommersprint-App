# Sommersprint App – Smart-Sanierungs-Assistent (Prototyp)

Die **Sommersprint App** ist ein intuitiver, mobiler Sanierungs-Assistent, der speziell für den Baustellenalltag entwickelt wird. Ziel des Projekts ist es, die Digitalisierungslücke im Handwerk zu schließen und komplexe BIM-Planungsprozesse (Building Information Modeling) so einfach wie ein Zeichentool zu machen – direkt auf dem Smartphone und ohne CAD-Studium.

Dieser Prototyp wurde als Web-App umgesetzt und dient zur Validierung der Kernfunktionen rund um die Raum- und Gewerkebasierte Leitungsplanung.

---

## 🚀 Kernfunktionen des Prototyps

Der aktuelle Entwicklungsstand zeigt bereits die grundlegende Navigation und die wichtigsten Planungs-Schritte:

### 1. Gewerkewahl & Übersicht
* **Auswahl des Arbeitsbereichs:** Flexibler Einstieg über die Gewerke **Heizung**, **Elektro**, **Sanitär** oder **Sonstiges** 
* **Layer-System:** Jedes Gewerk erhält eine eigene Ebene, um Überschneidungen und Planungsfehler zu minimieren.

### 2. Grundriss- & Raumverwaltung
* **Gebäude-Struktur:** Navigation durch Stockwerke (UG, EG, OG) und Räume.
* **Interaktive Raumansicht:** Visualisierung einzelner Räume (z. B. Küche, Wohnzimmer) mit exakter Bemaßung, Wandsegmenten, Fenstern und Türen 
### 3. Wand-Planungstool (2D-Canvas)
* **Intuitives Zeichnen:** Über eine Raster-Leinwand können Leitungen direkt auf die Wand projiziert werden 
* **Parametrisierung:** Schieberegler zur präzisen Einstellung von Verlegehöhe, Verlegetiefe und Raummaßen 
* **Intelligente Werkzeuge:** Integration von Bauteilen wie Rohren (z. B. DN 22), Winkeln, T-Stücken, Heizkörpern (HK), Fußbodenheizung (FBH), Pumpen und Ventilen 

### 4. Integrierte Materialliste & Logistik
* **Automatische Mengenermittlung:** Das System erfasst im Hintergrund verplante Materialien wie Kupfer- oder Verbundrohre sowie Formteile .
* **Lagerort-Zuweisung:** Möglichkeit zur direkten Verknüpfung mit einem virtuellen Regalsystem (z. B. "Regal B3") für eine optimierte Baustellenlogistik 

---

## 🛠️ Geplante Features & Bildungskonzept

Für die finale Version der App sind folgende Erweiterungen vorgesehen
* **Automatisches Fitting & Snapping:** Intelligentes Einrasten von Rohren und automatisches Setzen von Winkeln
* **Echtzeit-Kollisionsprüfung:** Warnung, wenn sich Leitungen verschiedener Gewerke überschneiden
* **BIM-Export:** Brückenfunktion zur Übersetzung der Zeichnungen in standardisierte Planersprache (Export als IFC, JSON, UGL)
* **Didaktisches Scaffolding:** Einsatz der App in der Berufsschule als interaktiver Lern-Assistent ("Lücken-Methodik" für Auszubildende im Handwerk)

---



---

## ⚠️ Status des Prototyps

> **Hinweis:** Dies ist ein fortlaufendes Projekt ("Work in Progress"). Der Code wurde initial mithilfe von KI-Unterstützung (Claude) generiert, um die Benutzeroberfläche und den Workflow schnell greifbar zu machen. Einige Funktionen sind aktuell noch rein visuelle Platzhalter und werden in kommenden Sprints funktional ausgebaut.
> 
