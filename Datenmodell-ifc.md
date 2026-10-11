# Datenmodell: Annäherung an die IFC-Logik

Lernübung zur Frage, wie sich die Struktur von IFC (Industry Foundation Classes) auf einen Sanierungs-Workflow übertragen lässt.

**Leitgedanke:** IFC-Modelle sind 3D-Datenmodelle für Planer und enthalten weit mehr Informationen, als ein Handwerker auf der Baustelle braucht. Die Struktur unten zeigt die **Auswahl der notwendigsten Daten**, die aus einem IFC-Modell in eine einfache 2D-Wandansicht übernommen würden: Geschoss, Raum, Wand, Öffnungen, Bauteile und wenige Eigenschaften wie Maße, Position und Lagerort. Alles andere bleibt im Ursprungsmodell.

**Hinweise zur Einordnung:**
- Die Darstellung ist **vereinfacht** und nicht IFC-konform. Beziehungsobjekte wie `IfcRelVoidsElement` fehlen bewusst.
- Eigenschaften wie "Lagerort" und "Bestand" sind App-Erweiterungen und nicht Teil von IFC.
- Die Wandnummern (W-01 bis W-04) gelten pro Raum.

---

## 1. Gebäudestruktur

```text
IfcProject ("Sommersprint")
└── IfcSite ("Standort / Grundstück")
    └── IfcBuilding ("Haus 1")
        │
        ├── IfcBuildingStorey ("UG – Untergeschoss")
        │   └── IfcSpace ("UG.01 – Heizungskeller")
        │       ├── IfcWall ("W-01 – Nordwand")
        │       │   ├── IfcOpeningElement ("Fenster-Öffnung")
        │       │   │   └── IfcWindow (Breite, Brüstung, Sturz)
        │       │   └── IfcPipeSegment (DN22, Kupfer, x/y/z)
        │       ├── IfcWall ("W-02 – Südwand")
        │       │   └── IfcOpeningElement
        │       │       └── IfcDoor (Breite, Höhe, Öffnungsrichtung)
        │       └── IfcWall ("W-03 / W-04 …")
        │
        ├── IfcBuildingStorey ("EG – Erdgeschoss")
        │   ├── IfcSpace ("EG.01 – Wohnzimmer")
        │   │   ├── IfcWall ("W-01 – Südwand / Tür-Wand → immer W-01")
        │   │   │   └── IfcOpeningElement → IfcDoor
        │   │   │       └── IfcPropertySet
        │   │   │           ├── Öffnungsrichtung: links/rechts
        │   │   │           └── Öffnungswinkel: 90°
        │   │   ├── IfcWall ("W-02 – Westwand")
        │   │   │   └── IfcOpeningElement → IfcWindow
        │   │   │       └── IfcPropertySet
        │   │   │           ├── Brüstungshöhe: 90 cm
        │   │   │           └── Sturzhöhe: 210 cm
        │   │   ├── IfcWall ("W-03 – Nordwand")
        │   │   │   └── IfcPipeSegment
        │   │   │       └── IfcPropertySet
        │   │   │           ├── DIN: EN 1057
        │   │   │           ├── DN: 22
        │   │   │           ├── x: 60 cm
        │   │   │           ├── y: 180 cm (Verlegehöhe)
        │   │   │           ├── Verlegetiefe: 5 cm
        │   │   │           └── Lagerort: Regal B3 / 12 m
        │   │   └── IfcWall ("W-04 – Ostwand")
        │   │
        │   ├── IfcSpace ("EG.02 – Küche")
        │   ├── IfcSpace ("EG.03 – Flur")
        │   │   └── IfcPropertySet
        │   │       └── SpaceType: CIRCULATION
        │   ├── IfcSpace ("EG.04 – Bad/WC")
        │   └── IfcSpace ("EG.05 – Schlafzimmer")
        │
        └── IfcBuildingStorey ("OG1 – Obergeschoss 1")
            ├── IfcSpace ("OG1.TH – Treppenhaus")
            │   └── IfcPropertySet
            │       └── SpaceType: STAIRCASE
            ├── IfcSpace ("OG1.FL – Flur OG")
            ├── IfcSpace ("OG1.01 – Kinderzimmer 1")
            ├── IfcSpace ("OG1.02 – Kinderzimmer 2")
            └── IfcSpace ("OG1.03 – Elternschlafzimmer")
```

---

## 2. Gewerk-Layer

Die Layer liegen parallel auf allen Räumen.

```text
IfcSystem ("Heizung")
├── IfcPipeSegment → Rohre (Kupfer, Verbund, Stahl)
├── IfcPipeFitting → Winkel, T-Stück, Reduktion
├── IfcFlowTerminal → Heizkörper, Badheizkörper
├── IfcDistributionPort → Fußbodenheizung Verteiler
└── IfcFlowMovingDevice → Umwälzpumpe

IfcSystem ("Elektro") → im Beispiel nicht ausgearbeitet
IfcSystem ("Sanitär") → im Beispiel nicht ausgearbeitet
```

---

## 3. Eigenschaften pro Objekt (IfcPropertySet)

Jedes verbaute Teil trägt:

```text
├── ID              → eindeutig, unveränderlich
├── Anzeigename     → frei editierbar (z. B. "Badezimmer")
├── DIN-Norm        → z. B. DIN EN 1057
├── DN / Dimension  → z. B. DN22
├── Position x/y/z  → in cm, Ursprung = Raumecke W-01
├── Verlegetiefe    → cm (Riegel oben)
├── Verlegehöhe     → cm (Riegel unten)
├── Lagerort        → Regal + Fach
├── Bestand         → Menge + Einheit
└── Gewerk-Layer    → Heizung / Elektro / Sanitär
```

---

## 4. Sperrzonen (IfcOpeningElement)

**Tür:**

```text
├── x-Position        → Abstand von Wandanfang
├── Breite            → cm
├── Sturzhöhe         → cm (Standard 210)
├── Öffnungsrichtung  → links / rechts
└── Öffnungswinkel    → Grad (Standard 90°)
```

**Fenster:**

```text
├── x-Position        → Abstand von Wandanfang
├── Breite            → cm
├── Brüstungshöhe     → cm (z. B. 90)
└── Sturzhöhe         → cm (z. B. 210)
```
