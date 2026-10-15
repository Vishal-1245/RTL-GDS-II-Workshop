# Module 3 — CMOS inverter and ngspice-related evidence

## Overview

This module contains screenshots associated with a SkyWater CMOS inverter, SPICE-related views, ngspice output, and Magic/layout activity. No transistor-level netlist, SPICE deck, model files, command log, or numerical measurement report is included.

## CMOS and simulation context

A CMOS inverter pairs a PMOS pull-up device with an NMOS pull-down device. For a valid supply and suitable input levels, the output logically inverts the input; switching behavior depends on device models, load, parasitics, and input slew. Transient SPICE analysis can show voltages over time, while a layout viewer shows geometry/layers. The screenshots do not provide enough information to derive delay, rise/fall time, power, or design-rule status.

An auditable circuit-level experiment should identify device models/PDK corner, supply, input pulse, output load, transient-analysis settings, and measurement definitions for any reported value. Those details and the source deck are absent here.

## Selected evidence

![CMOS inverter screenshot associated with SkyWater 130 nm](./Inverter_sky130A_3.png)
*Inverter screenshot associated with the SkyWater 130 nm technology.*

![Inverter-related circuit or simulation view](./Cmosinverter_tcon_3.png)
*Circuit or simulation view associated with the inverter example.*

![ngspice output screenshot](./ngspice_1_output_3.png)
*ngspice output screenshot.*

![ngspice simulation output view](./ngspice_simulation_op.png)
*ngspice simulation output view.*

Other images include [`Inverter_spiceext_3.png`](./Inverter_spiceext_3.png), [`Cloning_sky130a_3.png`](./Cloning_sky130a_3.png), [`Magic_git_3.png`](./Magic_git_3.png), [`magic_met3_3.png`](./magic_met3_3.png), [`Floorplan_changing_variables.png`](./Floorplan_changing_variables.png), and [`Floorplan_tcl_mode_check.png`](./Floorplan_tcl_mode_check.png). The file [`openlane_1png`](./openlane_1png) is also present, but has no image extension; it is not embedded here.

## Suggested interpretation

Use circuit/simulation screenshots to identify the inverter setup and displayed response, then compare them with the corresponding SPICE deck and model. Use a Magic/layout view to distinguish visual geometry from an electrically extracted netlist. A layout screenshot alone does not show whether extraction, DRC, LVS, or parasitic-aware simulation was performed.

## Scope and limitations

The images indicate exposure to circuit-level simulation and layout tools. They do not provide enough information to confirm model provenance, supply and load conditions, transient-analysis settings, measured delays, or successful physical verification.

[PD program index](../README.md) · [Module 2](../module2/README.md) · [Module 4](../module4/README.md)
