# Physical-design program evidence

## Overview

This folder organizes five physical-design learning modules. Its contents are screenshots only: no RTL, SPICE decks, TCL scripts, constraints, tool logs, generated netlists, or layout databases are included. The images indicate topics and GUI/tool activity; they are not a substitute for reproducible inputs or complete reports.

## Module index

| Module | Subject suggested by available artifacts | Guide |
| --- | --- | --- |
| 1 | OpenLane/PDK environment, configuration, and synthesis views | [Module 1](./module1/README.md) |
| 2 | Floorplan, I/O placement, and layout/placement views | [Module 2](./module2/README.md) |
| 3 | SkyWater 130 nm CMOS inverter, Magic, and ngspice-related views | [Module 3](./module3/README.md) |
| 4 | Synthesis/configuration, library-corner, track, and placement views | [Module 4](./module4/README.md) |
| 5 | CTS, placement, and routing screenshots | [Module 5](./module5/README.md) |

The topics above are inferred from artifact names and visible screenshot context. There are no actual program scripts or input/output directories here from which to document commands or claim a complete run.

## How the modules fit together

The ordering provides a conceptual route from environment and synthesis context (Module 1), through floorplanning and placement (Module 2), circuit-level CMOS behavior (Module 3), library/constraint concepts (Module 4), and clocking/routing stages (Module 5). Module 3 is a transistor-level exercise, not necessarily another sequential backend stage in one implementation run. The repository does not establish that all modules use the same design, PDK revision, or tool setup.

## Inputs and outputs for a reproducible review

| Activity | Typical inputs | Useful review outputs |
| --- | --- | --- |
| RTL synthesis | RTL, top module, libraries, flow configuration | Synthesis log, netlist, warnings, cell statistics |
| Floorplan and placement | Netlist, floorplan/I/O constraints, technology LEF | Layout database, legality and congestion reports |
| CMOS simulation | SPICE deck, device models, supply, stimulus | Transient log and waveform/measurement results |
| Timing/corner review | Timing constraints, libraries, operating conditions | Setup/hold reports and unconstrained-path report |
| CTS and routing | Placed design, clock constraints, routing technology data | CTS metrics, routed database, DRC and timing reports |

This table describes material normally needed for review; these inputs and outputs are not all checked into this repository.

## Representative module evidence

![Floorplan screenshot from Module 2](./module2/floorplan.png)
*Module 2 floorplan screenshot.*

![ngspice simulation screenshot from Module 3](./module3/ngspice_simulation_op.png)
*Module 3 screenshot associated with ngspice simulation output.*

## Tools and technologies represented

The material names or visibly references OpenLane, OpenROAD, SkyWater `sky130A`, Magic, ngspice, and Yosys. Tool versions, installation details, PDK revision, design configuration, and exact commands are not recorded in the repository.

## Interpreting the evidence

The five guides select representative screenshots and describe only what they are associated with. A screenshot labeled for a stage does not establish that the stage completed, passed design-rule checks, met timing, or produced a manufacturable layout. Those conclusions need the complete logs, constraints, reports, and generated design files.

[Workshop index](../README.md) · [BabySoC post-route evidence](../PostRoute_STA_VSDBabySOC_OpenRoad/README.md)
