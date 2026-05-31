Live Vorschau: https://femke-art-coder.github.io/Sommersprint-App/
# Sommersprint App – Smart-Sanierungs-Assistent (Prototyp)

Die **Sommersprint App** ist ein intuitiver, mobiler Sanierungs-Assistent, der speziell für den Baustellenalltag entwickelt wird. Ziel des Projekts ist es, die Digitalisierungslücke im Handwerk zu schließen und komplexe BIM-Planungsprozesse (Building Information Modeling) so einfach wie ein Zeichentool zu machen – direkt auf dem Smartphone und ohne CAD-Studium.

Dieser Prototyp wurde als Web-App umgesetzt und dient zur Validierung der Kernfunktionen rund um die Raum- und Gewerkebasierte Leitungsplanung.

---

##  Kernfunktionen des Prototyps

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

> **Hinweis:** Dies ist ein fortlaufendes Projekt ("Work in Progress"). Der Code wurde initial mithilfe von KI-Unterstützung (Claude) generiert, um die Benutzeroberfläche und den Workflow schnell greifbar zu machen. Einige Funktionen und Angaben sind aktuell noch fehlerhaft und rein visuelle Platzhalter.
>
> <img width="1080" height="1958" alt="1000038340" src="https://github.com/user-attachments/assets/fe285ab3-920c-41fb-8e75-17039c8726e8" />
<img width="961" height="1988" alt="1000038328" src="https://github.com/user-attachments/assets/033da3c9-03cd-4854-929e-dc78fd2770c8" />
<img width="1080" height="1978" alt="1000038333" src="https://github.com/user-attachments/assets/fbd7d8d5-6410-4885-9543-5afab5a70979" />
<img width="1080" height="1971" alt="1000038342" src="https://github.com/user-attachments/assets/db1d8a94-b737-4bf4-9940-94def942f2d9" />
<img width="1080" height="1994" alt="1000038341" src="https://github.com/user-attachments/assets/a7a9cd93-7560-48ac-af03-70f5f2b480e3" />
---

## 🏗️ Datenstruktur & IFC/BIM-Mapping

Um die Brückenfunktion zwischen intuitivem Zeichnen und professionellem BIM-Output zu gewährleisten, bildet die App die erfassten Daten intern direkt in einer standardisierten **IFC-Struktur (Industry Foundation Classes)** ab. 

Die Hierarchie und die zugewiesenen Attribute sind wie folgt aufgebaut:

```text
IfcProject ("Sommersprint")
└── IfcSite ("Standort / Grundstück")
    └── IfcBuilding ("Haus 1")
        ├── IfcBuildingStorey ("UG - Untergeschoss")
        │   └── IfcSpace ("U1.01 - Heizungskeller")
        │       ├── IfcWall ("W-01 - Nordwand")
        │       │   └── IfcOpeningElement ("Fenster-Öffnung")
        │       │       └── IfcWindow (Breite, Brüstung, Sturz)
        │       │   └── IfcPipeSegment (DN22, Kupfer, x/y/z)
        │       ├── IfcWall ("W-02 - Südwand")
        │       │   └── IfcOpeningElement
        │       │       └── IfcDoor (Breite, Höhe, Öffnungsrichtung)
        │       └── IfcWall ("W-03 / W-04 ...")
        │
        ├── IfcBuildingStorey ("EG - Erdgeschoss")
        │   ├── IfcSpace ("EG.01 - Wohnzimmer")
        │   │   ├── IfcWall ("W-01 - Südwand / Tür-Wand - immer W-01")
        │   │   │   └── IfcOpeningElement -> IfcDoor
        │   │   │       └── IfcPropertySet (Öffnungsrichtung: links/rechts, Öffnungswinkel: 90°)
        │   │   ├── IfcWall ("W-02 - Westwand")
        │   │   │   └── IfcOpeningElement -> IfcWindow
        │   │   │       └── IfcPropertySet (Brüstungshöhe: 90 cm, Sturzhöhe: 210 cm)
        │   │   └── IfcWall ("W-03 - Nordwand")
        │   │       └── IfcPipeSegment
        │   │           └── IfcPropertySet
        │   │               ├── DIN: EN 1057
        │   │               ├── DN: 22
        │   │               ├── x: 60 cm
        │   │               ├── y: 100 cm (Verlegehöhe)
        │   │               ├── Verlegetiefe: 5 cm
        │   │               └── Lagerort: Regal B3 / 12 m
        │   │   └── IfcWall ("W-04 - Ostwand")
        │   │
        │   ├── IfcSpace ("EG.02 - Küche")
        │   ├── IfcSpace ("EG.03 - Flur")
        │   │   └── IfcPropertySet (SpaceType: CIRCULATION)
        │   ├── IfcSpace ("EG.04 - Bad/WC")
        │   └── IfcSpace ("EG.05 - Schlafzimmer")
        │
        └── IfcBuildingStorey ("OG1 - Obergeschoss 1")
            ├── IfcSpace ("OG1.TH - Treppenhaus")
            │   └── IfcPropertySet (SpaceType: STAIRCASE)
            ├── IfcSpace ("OG1.FL - Flur OG")
            ├── IfcSpace ("OG1.01 - Kinderzimmer 1")
            └── IfcSpace ("OG1.02 - Kinderzimmer 2")
