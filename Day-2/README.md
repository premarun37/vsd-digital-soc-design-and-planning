\# Day 2 - Good Floorplan vs Bad Floorplan and Introduction to Library Cells



\## Objective



The objective of Day-2 is to understand the floorplanning and placement stages of the ASIC physical design flow. This includes studying floorplan parameters, die/core area calculation, power planning, pin placement, tap cell insertion, and standard-cell placement using OpenLANE and the Sky130 PDK.



\---



\# Theory



\## What is Floorplanning?



Floorplanning is the process of defining the physical structure of the chip before placement and routing.



The main goals of floorplanning are:



\* Determining die and core dimensions.

\* Defining the utilization factor.

\* Defining the aspect ratio.

\* Placing macros and I/O pins.

\* Planning the power distribution network (PDN).

\* Reserving routing resources.



A good floorplan minimizes congestion, improves timing, and reduces chip area.



\---



\## Utilization Factor



The utilization factor determines the percentage of core area occupied by standard cells.



```text

Utilization Factor =

(Standard Cell Area / Core Area) × 100

```



Higher utilization results in a smaller chip area but may increase routing congestion.



Lower utilization reduces congestion but increases chip area.



In the OpenLANE configuration:



```tcl

set ::env(FP\_CORE\_UTIL) 50

```



The design is configured for 50% core utilization.



\---



\## Aspect Ratio



Aspect ratio is defined as:



```text

Aspect Ratio =

Core Height / Core Width

```



In the configuration:



```tcl

set ::env(FP\_ASPECT\_RATIO) 1

```



An aspect ratio of 1 indicates a square floorplan.



\---



\## Power Planning



Power planning ensures reliable distribution of VDD and VSS throughout the design.



The Power Distribution Network (PDN) consists of:



\* Power rails

\* Power straps

\* Power rings

\* Tap cells



The PDN helps reduce:



\* IR Drop

\* Electromigration

\* Power integrity issues



\---



\## Pin Placement



Pins are placed around the boundary of the core area.



In the configuration:



```tcl

set ::env(FP\_IO\_MODE) 1

```



Pins are placed using the random equidistant placement mode.



This helps:



\* Reduce routing congestion.

\* Improve timing.

\* Distribute signals uniformly.



\---



\## Placement



Placement assigns physical locations to all standard cells within the core area.



Objectives of placement:



\* Minimize wire length.

\* Reduce congestion.

\* Improve timing.

\* Improve routability.



\---



\# Floorplan Configuration



\### Screenshot



!\[Floorplan Details](Img/Img\_11\_Floorplan\_details.png)



\### Observation



\* Floorplanning parameters are configured before physical implementation.

\* Core utilization, aspect ratio, margins, and PDN parameters are defined.

\* These parameters determine the physical dimensions of the design.



\---



\# Floorplan Configuration File



\### Screenshot



!\[Floorplan Configuration](Img/Img\_12\_Floorplan\_config\_details.png)



\### Observation



\* The OpenLANE floorplan configuration file contains parameters controlling floorplan generation.

\* Core utilization is set to 50%.

\* Aspect ratio is set to 1.

\* PDN generation and I/O placement options are enabled.



\---



\# Sky130 Standard Cell Configuration



\### Screenshot



!\[Sky130 Configuration](Img/Img\_13\_sky130\_fd\_sc\_hd\_config\_details.png)



\### Observation



\* The Sky130 HD library provides the standard cells used during implementation.

\* Cell dimensions, placement rules, and technology-specific parameters are defined in the library.



\---



\# Running Floorplanning



\### Screenshot



!\[Floorplan Command](Img/Img\_14\_floorplan\_cmd.png)



\### Observation



\* The floorplanning stage is initiated using OpenLANE.

\* OpenLANE computes the die area and core area based on utilization and aspect ratio constraints.



\---



\# Successful Floorplan Generation



\### Screenshot



!\[Floorplan Success](Img/Img\_15\_floorplan\_success.png)



\### Observation



\* Floorplan generation completed successfully.

\* Core dimensions and floorplan data were generated.



\---



\# Generated Floorplan Files



\### Screenshot



!\[Floorplan Files](Img/Img\_16\_floorplan\_results\_files.png)



\### Observation



\* Floorplan reports and DEF files are generated.

\* These files are used in later placement and routing stages.



\---



\# Die Area Information



\### Screenshot



!\[Die Area Information](Img/Img\_17\_floorplan\_die\_area\_info.png)



\### Observation



\* Die dimensions and core dimensions are reported.

\* These values are calculated using utilization factor and aspect ratio settings.



\---



\# Viewing Floorplan in Magic



\### Screenshot



!\[Floorplan GUI Command](Img/Img\_18\_floorplan\_result\_gui\_cmd.png)



\### Observation



\* Magic is used to visualize the generated floorplan.

\* LEF and DEF files are loaded to inspect the design physically.



\---



\# Floorplan Layout View



\### Screenshot



!\[Floorplan Layout](Img/Img\_19\_floorplan\_result\_gui\_view.png)



\### Observation



\* Core area and die boundary can be visualized.

\* Floorplan structure is verified before placement.



\---



\# Equidistant I/O Pins



\### Screenshot



!\[Equidistant Pins](Img/Img\_20\_equidistant\_cells.png)



\### Observation



\* I/O pins are distributed around the core boundary.

\* This behavior is controlled by FP\_IO\_MODE = 1.

\* Proper pin placement improves routing efficiency.



\---



\# Cell Identification Using Magic



\### Screenshot



!\[Cell Details](Img/Img\_21\_cell\_1\_details.png)



\### Observation



\* The `what` command in Magic identifies selected cells.

\* Cell information and hierarchy can be inspected interactively.



\---



\# I/O Pin Details



\### Screenshot



!\[I/O Pin Details](Img/Img\_22\_io\_pin\_details.png)



\### Observation



\* Input and output pins can be examined individually.

\* Pin locations influence routing quality and timing.



\---



\# Standard Cell Details



\### Screenshot



!\[Standard Cell Details](Img/Img\_23\_standard\_cell\_details.png)



\### Observation



\* Standard cells from the Sky130 HD library are visible in the floorplan.

\* Cell properties can be inspected using Magic.



\---



\# Metal Layer Details



\### Screenshot



!\[Metal Details](Img/Img\_24\_metal\_details.png)



\### Observation



\* Metal layers are used for signal and power routing.

\* Different routing layers support different routing directions.



\---



\# Floorplan Configuration After Execution



\### Screenshot



!\[Configuration After Floorplan 1](Img/Img\_25\_config\_details\_after\_floorplan\_1.png)



!\[Configuration After Floorplan 2](Img/Img\_26\_config\_details\_after\_floorplan\_2.png)



\### Observation



\* OpenLANE updates configuration values during floorplan generation.

\* Generated parameters are used in subsequent stages.



\---



\# Floorplan Log Files



\### Screenshot



!\[Floorplan Logs](Img/Img\_27\_floorplan\_log\_files.png)



\### Observation



\* Log files record floorplan execution details.

\* Useful for debugging and verification.



\---



\# I/O Placement Logs



\### Screenshot



!\[IO Placer Logs](Img/Img\_28\_io\_placer\_log\_details.png)



\### Observation



\* Pin placement operations are recorded.

\* Confirms successful I/O placement.



\---



\# Tap Cell Insertion



\### Screenshot



!\[Tap Cell Logs](Img/Img\_29\_tap\_cell\_log\_details.png)



\### Observation



\* Tap cells connect substrate and wells to power rails.

\* They prevent latch-up and improve reliability.



\---



\# Power Distribution Network (PDN)



\### Screenshot



!\[PDN Logs 1](Img/Img\_30\_pdn\_log\_details\_1.png)



!\[PDN Logs 2](Img/Img\_31\_pdn\_log\_details\_2.png)



\### Observation



\* PDN generation creates power rails and power straps.

\* Ensures stable power delivery across the design.



\---



\# Running Placement



\### Screenshot



!\[Placement Command](Img/Img\_32\_placement\_cmd.png)



\### Observation



\* Placement assigns locations to standard cells.

\* Placement optimization attempts to minimize wire length and congestion.



\---



\# Successful Placement



\### Screenshot



!\[Placement Success](Img/Img\_33\_placement\_success.png)



\### Observation



\* Placement completed successfully.

\* Standard cells were distributed throughout the core area.



\---



\# Placement Layout View



\### Screenshot



!\[Placement Layout](Img/Img\_34\_placement\_view\_gui.png)



\### Observation



\* Standard cells are visible inside the core region.

\* Placement quality can be visually inspected.



\---



\# Congestion Analysis



\### Screenshot



!\[Congestion View 1](Img/Img\_35\_placement\_congested\_view\_1.png)



!\[Congestion View 2](Img/Img\_37\_placement\_congested\_view\_2.png.png)



\### Observation



\* Congested regions indicate areas with high routing demand.

\* Congestion must be minimized for successful routing.



\---



\# Placement Cell Details



\### Screenshot



!\[Placement Cell Details](Img/Img\_36\_placement\_cell\_detail.png)



\### Observation



\* Individual placed cells can be inspected using Magic.

\* Placement legality and orientation can be verified.



\---



\# Metal Layers After Placement



\### Screenshot



!\[Metal Cell Details](Img/Img\_38\_placement\_metal\_cell\_details.png)



!\[Metal 2 Details](Img/Img\_40\_metal\_2\_detail\_placement.png)



!\[Metal 3 Details](Img/Img\_41\_metal\_3\_details\_placement.png)



\### Observation



\* Metal layers provide routing resources for signals and power.

\* Different layers are used to reduce routing congestion.



\---



\# Standard Cells After Placement



\### Screenshot



!\[Placed Standard Cells](Img/Img\_42\_standard\_cells\_placed\_after\_placement.png)



\### Observation



\* Standard cells are distributed throughout the core area.

\* Placement prepares the design for Clock Tree Synthesis (CTS).



\---



\# Key Learnings



\* Understanding floorplanning concepts.

\* Utilization factor and aspect ratio.

\* Power planning and PDN generation.

\* Pin placement strategies.

\* Tap cell insertion.

\* Physical layout inspection using Magic.

\* Standard-cell placement.

\* Congestion analysis and placement quality.



\---



\# Conclusion



Day-2 focused on floorplanning, power planning, and placement using OpenLANE and the Sky130 PDK. The floorplan was generated based on utilization and aspect ratio constraints, the PDN was created for reliable power delivery, and standard cells were successfully placed within the core area, preparing the design for Clock Tree Synthesis and routing.



