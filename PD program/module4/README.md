# Module 4 — Synthesis, libraries, and implementation views

## Overview

This module contains screenshots associated with configuration/constraints, synthesis, library-corner names, placement, and routing tracks. It contains no SDC/TCL files, source design, library files, timing reports, or logs; corner analysis and timing results therefore cannot be independently verified.

## Concepts

Synthesis maps logic into cells from a target library. Libraries may provide timing/power data for different process, voltage, and temperature conditions. A timing-constraint file such as SDC describes clocks and I/O/path requirements; incomplete constraints can leave paths unconstrained. Track patterns define preferred routing grids/layers in the technology and affect physical implementation.

Corner labels alone are not enough to interpret timing: the exact libraries, voltage, temperature, parasitic corner, constraints, and analysis mode are needed. The supplied screenshot `sky140_slow_4.png` uses a different technology-number spelling from the `sky130` filenames; it is preserved exactly and is not assumed to be a valid or comparable corner for the same flow.

## Selected evidence

![Synthesis-related screenshot](./Synthesis_4.png)
*Synthesis-related screenshot.*

![Screenshot associated with a typical Sky130 library corner](./sky130_typical_4.png)
*Screenshot associated with a typical Sky130 library corner.*

![Screenshot associated with a base SDC configuration](./base.sdc_4.png)
*Screenshot associated with the base timing-constraint file.*

Other artifacts include [`Configuration_readme_4.png`](./Configuration_readme_4.png), [`sky130_fast_4.png`](./sky130_fast_4.png), [`sky140_slow_4.png`](./sky140_slow_4.png), [`sky_typical_4.png`](./sky_typical_4.png), [`sky130_inv_4.png`](./sky130_inv_4.png), [`placement_4.png`](./placement_4.png), [`Tracks_info_4.png`](./Tracks_info_4.png), and [`tracks_as_grids_4.png`](./tracks_as_grids_4.png). The supplied name `sky140_slow_4.png` is preserved; it is not relabeled as a Sky130 corner.

## Corner-analysis review checklist

For a defensible timing comparison, record the library/corner name and revision, process-voltage-temperature conditions, clock definitions and uncertainty, input/output delays, parasitic assumptions, and analysis mode. Compare setup and hold results and inspect unconstrained endpoints. A screenshot of a library name or configuration pane is not itself a timing report.

## Scope and limitations

Process-corner timing analysis requires the exact library corner, voltage/temperature, constraints, and timing reports. The supplied screenshots do not provide enough reproducible evidence to assert timing closure or compare corner results quantitatively.

[PD program index](../README.md) · [Module 3](../module3/README.md) · [Module 5](../module5/README.md)
