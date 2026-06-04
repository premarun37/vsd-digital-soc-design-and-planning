# VSD Digital SoC Design and Planning

This repository documents my learning journey through the **VSD-NASSCOM Digital VLSI SoC Design and Planning Workshop**, covering the complete **RTL-to-GDSII ASIC Design Flow** using **OpenLANE**, **OpenROAD**, and the **Sky130 PDK**.

## Progress

* [x] Day 1 – OpenLANE, Synthesis and Floorplanning Basics
* [x] Day 2 – Floorplanning, Power Planning and Placement
* [ ] Day 3 – Standard Cell Design and Characterization
* [ ] Day 4 – Timing Characterization and STA
* [ ] Day 5 – Final Physical Design Flow and Verification

---

## Course Notes

### Day-wise Documentation

* [Day 1 - Inception of Open-Source EDA, OpenLANE and Sky130 PDK](Day-1/README.md)
* [Day 2 - Floorplanning, Power Planning and Placement](Day-2/README.md)

---

## Topics Covered

### Day 1

* Introduction to ASIC Design Flow
* OpenLANE Flow Overview
* Sky130 PDK Introduction
* RTL Synthesis using Yosys
* Understanding SDC Constraints
* Analysis of Cell Count and Area Reports
* Pin Placement Concepts
* Floorplanning Basics

### Day 2

* Floorplanning Theory
* Utilization Factor and Aspect Ratio
* Core Area vs Die Area
* Physical Design Cells

  * Endcap Cells
  * Well Tap Cells
  * Hard Macros
  * Soft Macros
  * IP Blocks
  * Spare Cells
  * Decap Cells
  * Guard Ring Cells
* Power Distribution Network (PDN)
* Floorplan Generation in OpenLANE
* Floorplan Analysis using Magic VLSI
* IO Placement Analysis
* Tap Cell Insertion
* PDN Generation
* Standard Cell Placement
* Placement Congestion Analysis
* Metal Layer Identification in Magic

---

## Tools Covered

* OpenLANE
* OpenROAD
* Sky130 PDK
* Yosys
* Magic VLSI
* Netgen
* OpenSTA

---

## Learning Objectives

* Understand the RTL-to-GDSII ASIC Design Flow
* Learn Physical Design Concepts
* Explore Open-Source EDA Tools
* Perform Synthesis, Floorplanning, Placement, CTS and Routing
* Analyze Timing using STA
* Perform DRC and LVS Verification
* Understand Power Planning and Standard Cell Placement

---

## Repository Structure

```text
vsd-digital-soc-design-and-planning/
│
├── README.md
│
├── Day-1/
│   ├── README.md
│   └── Img/
│
├── Day-2/
│   ├── README.md
│   └── Img/
│
├── Day-3/
├── Day-4/
└── Day-5/
```

---

## Workshop Flow

```text
RTL Design
    ↓
Synthesis
    ↓
Floorplanning
    ↓
Placement
    ↓
Clock Tree Synthesis (CTS)
    ↓
Routing
    ↓
STA + DRC + LVS
    ↓
GDSII (Tapeout)
```
