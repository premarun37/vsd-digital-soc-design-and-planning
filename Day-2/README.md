# Day 2 - Floorplanning, Power Planning and Placement

## Objective

The objective of Day-2 is to understand the floorplanning, power planning, and placement stages of the ASIC physical design flow using OpenLANE and the Sky130 PDK.

---

# Introduction to Floorplanning

Floorplanning is the first stage of physical design after synthesis. It determines the physical dimensions of the chip core and defines the placement area for standard cells, macros, power networks, and I/O pins.

### Goals of Floorplanning

* Define chip and core dimensions.
* Determine utilization factor and aspect ratio.
* Place I/O pins around the core boundary.
* Create routing channels.
* Insert tap cells and decap cells.
* Prepare the design for power planning and placement.

---

# Floorplanning Theory

## What is Floorplanning?

Floorplanning is the first physical design stage after synthesis. It defines the chip dimensions, core area, placement regions, power network, and I/O locations.

A good floorplan helps reduce congestion, improve timing, and optimize chip area.

---

## Key Floorplanning Parameters

### 1. Utilization Factor

Represents the percentage of core area occupied by standard cells.

```text
Utilization Factor = Netlist Area / Core Area
```

- Higher utilization reduces chip area.
- Excessive utilization can increase routing congestion.

### 2. Aspect Ratio

Determines the shape of the core.

```text
Aspect Ratio = Core Height / Core Width
```

- Aspect Ratio = 1 → Square core
- Aspect Ratio > 1 → Tall core
- Aspect Ratio < 1 → Wide core

### 3. Core Area and Die Area

- **Core Area:** Region used for standard cell placement.
- **Die Area:** Total chip area including core, I/O cells, and margins.

---

## Important Physical Design Cells

### Endcap / Boundary Cells
- Placed at row boundaries.
- Prevent edge-related DRC violations.

### Well Tap Cells
- Connect wells to VDD/GND.
- Help prevent latch-up.

### Hard Macros
- Fixed-layout blocks.
- Examples: SRAM, PLL, Analog IP.

### Soft Macros
- RTL-defined functional blocks.
- Implemented during synthesis and placement.

### IP Blocks
- Reusable pre-verified design modules.
- Examples: UART, SPI, I2C, Processors.

### I/O Pins
- Interface between chip and external world.
- Placed around the core boundary.

### Spare Cells
- Reserved cells for future ECO modifications.
- Reduce redesign effort.

### Decap Cells
- Store local charge.
- Reduce voltage fluctuations and noise.

### Guard Ring Cells
- Surround sensitive blocks.
- Reduce noise coupling and latch-up effects.

---

## Power Planning

Power planning creates the Power Distribution Network (PDN) using:

- Power Rails
- Power Straps
- Power Rings

Objectives:

- Reduce IR drop
- Prevent electromigration
- Ensure reliable power delivery

---

## Pin Placement

I/O pins are placed around the core boundary to:

- Reduce routing congestion
- Minimize wire length
- Improve timing performance

---

## Importance of Floorplanning

A good floorplan:

- Improves timing closure
- Reduces congestion
- Optimizes chip area
- Improves power distribution
- Simplifies placement and routing

---

# Floorplan Configuration Parameters

### Screenshot

![Floorplan Details](Img/Img_11_Floorplan_details.png)

### Observation

* Floorplanning parameters are defined through OpenLANE configuration files.
* These parameters determine the size and shape of the core area.
* Proper floorplanning reduces routing congestion and improves timing.

---

### Screenshot

![Floorplan Configuration](Img/Img_12_Floorplan_config_details.png)

### Observation

* Core utilization defines the percentage of the core occupied by standard cells.
* Aspect ratio determines the shape of the core.
* Margins provide routing space between the core and die boundaries.

---

### Screenshot

![Sky130 Configuration](Img/Img_13_sky130_fd_sc_hd_config_details.png)

### Observation

* Technology-specific parameters are obtained from the Sky130 standard-cell library.
* Cell dimensions and placement constraints are defined in these files.

---

# Running Floorplan

### Command

```tcl
run_floorplan
```

### Screenshot

![Floorplan Command](Img/Img_14_floorplan_cmd.png)

### Observation

* OpenLANE starts floorplanning using synthesized netlists and configuration parameters.
* Core dimensions and pin locations are calculated.

---

### Screenshot

![Floorplan Success](Img/Img_15_floorplan_success.png)

### Observation

* Floorplanning completed successfully.
* DEF files and reports were generated.

---

# Floorplan Results

### Screenshot

![Floorplan Result Files](Img/Img_16_floorplan_results_files.png)

### Observation

* Floorplan output files are stored in the results directory.
* DEF files contain physical layout information.

---

### Screenshot

![Die Area Information](Img/Img_17_floorplan_die_area_info.png)

### Observation

* Die area and core area dimensions are reported.
* Core utilization directly affects final chip area and routing congestion.

---

# Viewing Floorplan in Magic

### Command

```bash
magic -T sky130A.tech \
lef read ../../tmp/merged.lef \
def read picorv32a.floorplan.def &
```

### Screenshot

![Magic GUI Command](Img/Img_18_floorplan_result_gui_cmd.png)

### Observation

* Magic loads the floorplan DEF file and displays the layout.
* The layout can be inspected visually.

---

### Screenshot

![Magic Layout View](Img/Img_19_floorplan_result_gui_view.png)

### Observation

* The die boundary and core area are visible.
* I/O pins are placed around the boundary.

---

# I/O Pin Placement

### Screenshot

![Equidistant Pins](Img/Img_20_equidistant_cells.png)

### Observation

* I/O pins are placed equidistantly around the core boundary.
* This placement is controlled by the parameter `FP_IO_MODE`.

---

### Screenshot

![Cell Details](Img/Img_21_cell_1_details.png)

### Observation

* Magic's `what` command displays information about selected objects.
* Cell instances and coordinates can be inspected.

---

### Screenshot

![I/O Pin Details](Img/Img_22_io_pin_details.png)

### Observation

* Input and output ports are placed on metal layers.
* Proper pin placement improves routability.

---

### Screenshot

![Standard Cell Details](Img/Img_23_standard_cell_details.png)

### Observation

* Standard cells are visible inside the core area.
* Cells remain unplaced at the floorplanning stage.

---

### Screenshot

![Metal Details](Img/Img_24_metal_details.png)

### Observation

* Metal layers are used for routing signals and power connections.
* Multiple routing layers are available in the Sky130 process.

---

# Power Planning

Power planning ensures reliable delivery of VDD and GND throughout the chip.

### Objectives

* Minimize IR drop.
* Reduce electromigration.
* Provide uniform power distribution.
* Improve reliability.

---

### Screenshot

![Configuration After Floorplan 1](Img/Img_25_config_details_after_floorplan_1.png)

### Screenshot

![Configuration After Floorplan 2](Img/Img_26_config_details_after_floorplan_2.png)

### Observation

* Power planning parameters are generated after floorplanning.
* Power grid generation depends on these settings.

---

# Floorplan Log Analysis

### Screenshot

![Floorplan Log Files](Img/Img_27_floorplan_log_files.png)

### Observation

* Log files record all floorplanning activities.
* Errors and warnings can be analyzed through logs.

---

### Screenshot

![IO Placer Logs](Img/Img_28_io_placer_log_details.png)

### Observation

* The I/O placer determines the location of input and output pins.
* Equidistant placement helps reduce congestion.

---

### Screenshot

![Tap Cell Logs](Img/Img_29_tap_cell_log_details.png)

### Observation

* Tap cells prevent latch-up by connecting substrate and wells to power rails.
* Tap cell insertion is an important reliability requirement.

---

### Screenshot

![PDN Logs 1](Img/Img_30_pdn_log_details_1.png)

### Screenshot

![PDN Logs 2](Img/Img_31_pdn_log_details_2.png)

### Observation

* Power Distribution Network (PDN) generation creates power rails and straps.
* PDN ensures stable voltage delivery across the chip.

---

# Placement

Placement assigns physical locations to standard cells inside the core area.

### Objectives

* Reduce wire length.
* Minimize congestion.
* Improve timing.
* Optimize power consumption.

---

# Running Placement

### Command

```tcl
run_placement
```

### Screenshot

![Placement Command](Img/Img_32_placement_cmd.png)

### Observation

* OpenLANE starts global placement followed by detailed placement.
* Cells are arranged based on connectivity and timing requirements.

---

### Screenshot

![Placement Success](Img/Img_33_placement_success.png)

### Observation

* Placement completed successfully.
* Standard cells were assigned legal physical locations.

---

# Viewing Placement Results

### Screenshot

![Placement GUI](Img/Img_34_placement_view_gui.png)

### Observation

* Standard cells are distributed across the core area.
* Placement density can be visually inspected.

---

### Screenshot

![Placement Congestion 1](Img/Img_35_placement_congested_view_1.png)

### Observation

* Congested regions may lead to routing difficulties.
* Placement optimization attempts to reduce congestion.

---

### Screenshot

![Placement Cell Details](Img/Img_36_placement_cell_detail.png)

### Observation

* Cell-level placement information can be viewed using Magic.
* Instance names and coordinates are available.

---

### Screenshot

![Placement Congestion 2](Img/Img_37_placement_congested_view_2.png.png)

### Observation

* Congestion analysis helps evaluate placement quality before routing.

---

### Screenshot

![Metal Cell Details](Img/Img_38_placement_metal_cell_details.png)

### Observation

* Routing layers become more visible after placement analysis.

---

### Screenshot

![Mask Details](Img/Img_39_mask_details_placement.png)

### Observation

* Layout layers correspond to mask layers used during fabrication.

---

### Screenshot

![Metal 2 Details](Img/Img_40_metal_2_detail_placement.png)

### Screenshot

![Metal 3 Details](Img/Img_41_metal_3_details_placement.png)

### Observation

* Different metal layers provide routing resources for signal connections.
* Higher metal layers generally support longer routes.

---

### Screenshot

![Placed Standard Cells](Img/Img_42_standard_cells_placed_after_placement.png)

### Observation

* Standard cells are fully placed inside the core area.
* The design is now ready for Clock Tree Synthesis (CTS).

---

# Key Learnings

* Understanding floorplanning concepts and parameters.
* Analysis of core utilization and aspect ratio.
* Viewing floorplan layouts using Magic.
* Understanding I/O pin placement strategies.
* Importance of tap cells and power planning.
* Power Distribution Network (PDN) generation.
* Global and detailed placement concepts.
* Congestion analysis and placement quality evaluation.

---

# Conclusion

Day-2 focused on floorplanning, power planning, and placement stages of the OpenLANE flow. The generated floorplan, PDN, and placement results provide the physical foundation required for the next stages of the ASIC implementation flow, including Clock Tree Synthesis (CTS), routing, timing optimization, and signoff verification.
