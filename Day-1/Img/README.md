# Day 1 - Inception of Open-Source EDA, OpenLANE and Sky130 PDK

## Objective

The objective of Day-1 is to understand the basic ASIC design flow, OpenLANE framework, synthesis process, design constraints, and floorplanning concepts using the picorv32a design.

---

# ASIC Design Flow

The complete RTL-to-GDSII flow consists of:

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
Static Timing Analysis (STA)
           +
Design Rule Check (DRC)
           +
Layout Versus Schematic (LVS)
    ↓
GDSII (Tapeout)
```

---

# OpenLANE Invocation

OpenLANE is an open-source RTL-to-GDSII automated flow based on OpenROAD and the Sky130 PDK.

### Commands Used

```tcl
cd Desktop/work/tools/openlane_working_dir/openlane

docker

./flow.tcl -interactive

package require openlane 0.9

prep -design picorv32a
```

### Screenshot

![OpenLANE Invoke](Img/Img_1_OpenLane_Invoke.png)

### Observation

* OpenLANE environment was successfully launched.
* The picorv32a design was prepared for the RTL-to-GDSII flow.

---

# Running Synthesis

Synthesis converts RTL Verilog code into a gate-level netlist using standard cells from the Sky130 library.

### Command

```tcl
run_synthesis
```

### Screenshot

![Running Synthesis](Img/Img_2_Running_Synthesis.png)

### Observation

* RTL code is mapped into standard cells.
* Timing and area optimization are performed during synthesis.

---

# Successful Synthesis

### Screenshot

![Successful Synthesis](Img/Img_3_Successful_Synthesis.png)

### Observation

* Synthesis completed successfully.
* Gate-level netlist was generated.
* Area and timing reports were generated.

---

# Total Number of Cells

### Screenshot

![Cell Count](Img/Img_4_Total_Cell_Count.png)

### Observation

* The synthesis report provides the total number of standard cells used in the design.
* Cell count directly impacts silicon area and power consumption.

---

# Number of D Flip-Flops

### Screenshot

![DFF Count](Img/Img_5_DFF_Count.png)

### Observation

* D Flip-Flops are sequential elements used to store data.
* The report shows the number of registers used in the processor design.

---

# Chip Area After Synthesis

### Screenshot

![Chip Area](Img/Img_6_Chip_Area.png)

### Observation

* Chip area estimation is obtained after synthesis.
* Area is calculated based on the standard cells utilized by the design.

---

# Synthesis Flow Summary

### Screenshot

![Synthesis Summary](Img/Img_7_Synthesis_Summary.png)

### Observation

* Provides an overview of area, cell count, and synthesis statistics.
* Used to evaluate design quality before moving to floorplanning.

---

# SDC Constraint File

### Screenshot

![SDC Constraints](Img/Img_8_Yosys_SDC.png)

### Understanding SDC

* SDC (Synopsys Design Constraints) defines timing requirements for the design.
* Clock period, input delays, output delays, and timing constraints are specified.
* These constraints guide synthesis and timing optimization.

### Observation

* After running synthesis, OpenLane automatically generates a file named `yosys.sdc` inside the `runs/<run_name>/tmp/` directory.
* This file contains the timing constraints used during synthesis and is generated from the design configuration.
* The constraints in `yosys.sdc` guide Yosys during technology mapping and cell selection.
* The final area, timing, and power characteristics of the synthesized netlist depend on these constraints.

---

# Pin Placement Details

### Screenshot

![Pin Placement](Img/Img_9_Pin_Placement.png)

### Observation

* Input and output pins are placed around the boundary of the core area.
* Clock pins are placed near the center to reduce clock distribution delay and clock skew.
* Proper pin placement helps achieve efficient routing and improved timing performance.

---

# Logic Cell Placement Details

### Screenshot

![Logic Cell Placement](Img/Img_10_Logic_Cell_Placement.png)

### Observation

* Placement blockages are created near I/O pin regions.
* Standard cells are prevented from being placed inside blockage areas.
* This helps reduce routing congestion and improves routing quality.
* Proper placement ensures better timing and utilization.

---

# Key Learnings

* Introduction to the OpenLANE flow.
* Understanding of the Sky130 PDK.
* RTL-to-Gate-Level Netlist conversion through synthesis.
* Importance of timing constraints using SDC files.
* Analysis of area and cell count reports.
* Basics of pin placement and placement blockages.
* Preparation of the design for floorplanning and placement stages.

---

# Conclusion

Day-1 focused on understanding the OpenLANE flow and synthesis process using the picorv32a RISC-V processor design. The synthesis reports, timing constraints, pin placement, and floorplanning concepts provide the foundation for the subsequent physical design stages in the RTL-to-GDSII flow.
