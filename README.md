# Sommersprint App – Konzeptstudie Smart-Sanierungs-Assistent

Prototyp: https://femke-art-coder.github.io/Sommersprint-App/

Datenmodell zur IFC-Struktir: Datenmodell-ifc.md
Dieser Web-Prototyp ist Teil einer selbstinitiierten Konzeptstudie zur Bau-Digitalisierung. Er entstand als Lernübung, um zu verstehen, wie Gewerke, Raumplanung, Mengenermittlung und Baustellenlogistik digital zusammenspielen.

Der Prototyp ist als reine Web-Oberfläche (HTML) umgesetzt und zeigt den Workflow, nicht ein einsatzfähiges Produkt.

---

## Untersuchte Workflow-Bausteine

### 1. Gewerkewahl & Übersicht
- **Arbeitsbereiche:** Heizung, Elektro, Sanitär, Sonstiges
- **Layer-Prinzip:** Jedes Gewerk hat eine eigene Ebene, um Überschneidungen sichtbar zu machen.

### 2. Grundriss- & Raumverwaltung
- **Gebäudestruktur:** Stockwerke (UG, EG, OG) und Räume
- **Raumansicht:** Räume mit Bemaßung, Wandsegmenten, Fenstern und Türen

### 3. Wandplanung (2D-Canvas)
- **Zeichnen:** Leitungen auf einer Rasterfläche an der Wand platzieren
- **Parametrisierung:** Verlegehöhe, Verlegetiefe und Raummaße einstellen
- **Bauteile:** Rohre (z. B. DN 22), Winkel, T-Stücke, Heizkörper, Fußbodenheizung, Pumpen, Ventile

### 4. Materialliste & Logistik
- **Mengenermittlung:** Automatische Erfassung der verplanten Materialien
- **Lagerort-Zuordnung:** Verknüpfung mit einem virtuellen Regalsystem (z. B. "Regal B3")

---

## Gedankenspiele für die Weiterentwicklung

Beim Entwerfen haben sich Fragen ergeben, die ich als Lernfelder betrachte:

- Automatisches Einrasten von Rohren und Winkeln (Fitting & Snapping)
- Kollisionsprüfung zwischen Gewerken
- Export in standardisierte Planersprache (IFC)
- Ablaufplanung und Fortschrittskontrolle
- Einsatz als Lernassistent in der Berufsschule

Diese Punkte wurden **nicht umgesetzt**. Sie zeigen, welche Themen mich an der Schnittstelle von Bau und IT interessieren.

---

## Status

**Konzeptstudie, abgeschlossen.** Der Code wurde mit KI-Unterstützung (Claude) erstellt, um Oberfläche und Workflow schnell sichtbar zu machen. Einige Funktionen und Angaben sind reine visuelle Platzhalter. Das Projekt hat mein Interesse an Bau-Digitalisierung, BIM und Prozessdigitalisierung geweckt.

## Startseite
Zur Übersicht: [Konzeptstudie Sommersprint](https://femke-art-coder.github.io/sommersprint/)
