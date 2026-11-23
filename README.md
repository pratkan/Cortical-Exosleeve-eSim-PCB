# CORTICAL EXOSLEEVE — sEMG Hydraulic Controller PCB (eSim v2.6)

**eSim Winter Internship 2026 — Task 7 Submission**  
**Author:** Prat (`pratkan`)  
**Hardware Revision:** `v1.0.0`  
**License:** `CERN-OHL-S-v2` (Strongly Reciprocal)  

---

## 1. Overview
The **Cortical Exosleeve** control board is an open-hardware, mixed-signal 2-layer PCB designed and verified in **eSim v2.6**. It integrates a high-CMRR surface electromyography (sEMG) analog front-end (`INA333` instrumentation amplifier stage) with a high-current 24 V electro-hydraulic solenoid driver and active avalanche clamping circuit for rapid wearable joint stabilization.

---

## 2. Circuit Architecture & Key Subsystems
1. **sEMG Analog Front-End (`INA333xxDGK`):**
   - Low-noise differential bio-potential acquisition conditioned for 1 kHz Teager-Kaiser Energy Operator (TKEO) onset detection.
   - Isolated analog ground island (`B.Cu`) and local decoupling to prevent switching transients from coupling into microvolt-level muscle signals.
2. **24 V Solenoid Power & Active Avalanche Clamp:**
   - Step-up boost stage (`MT3608`) driving an inductive electro-hydraulic micro-solenoid valve (`8.41 ms` mechanical lock response).
   - Fast-recovery flyback and active avalanche clamping network (`UF4007` + `18 V` Zener) to accelerate coil current decay and protect switching FETs against inductive transients.
3. **PCB Stackup & Layout Verification:**
   - **Layers:** 2-Layer FR-4 (`F.Cu` signal/power routing, `B.Cu` partitioned ground plane, `1.6 mm` board thickness).
   - **DRC Status:** `0` DRC violations, `0` unconnected items, and `0` warnings verified in eSim v2.6.

---

## 3. 3D PCB Renders
### Top View (`F.Cu` Component Side)
![Cortical Exosleeve PCB Top 3D View](docs/Cortical_Exosleeve_PCB_TOP.png)

### Bottom View (`B.Cu` Partitioned Ground Plane)
![Cortical Exosleeve PCB Bottom 3D View](docs/Cortical_Exosleeve_PCB_BOTTOM.png)

---

## 4. Repository Structure
```text
Cortical_Exosleeve_PCB/
├── Cortical_Exosleeve_PCB.proj        # eSim v2.6 project wrapper
├── Cortical_Exosleeve_PCB.kicad_sch   # Complete schematic
├── Cortical_Exosleeve_PCB.kicad_pcb   # Routed 2-layer PCB layout
├── Cortical_Exosleeve_PCB.kicad_pro   # KiCad project settings
├── README.md                          # Project documentation
├── gerbers/                           # Fabrication Gerber (.gbr) & Excellon drill (.drl) files
└── docs/
    ├── Cortical_Exosleeve_PCB_TOP.png     # 3D render (Top view)
    ├── Cortical_Exosleeve_PCB_BOTTOM.png  # 3D render (Bottom view)
    ├── drc_pass.png                       # eSim v2.6 DRC 0-error verification screenshot
    ├── drc_report.rpt                     # Exported DRC report
    └── Cortical_Exosleeve_BOM.csv         # Bill of Materials