# Module 1 — Environment, PDK, and synthesis evidence

## Overview

This module contains screenshots associated with an OpenLane environment, a SkyWater 130 nm PDK, configuration, design contents, and synthesis. There are no setup instructions, TCL files, RTL sources, tool logs, or synthesis reports in the folder.

## Concepts and workflow

A PDK supplies technology-specific libraries, layer definitions, and process/model data used by implementation tools. Flow configuration selects a design and controls parameters; synthesis maps logic toward cells available in the selected technology. Correctness depends on the RTL and configuration, not simply on the presence of a tool window.

The screenshots suggest a sequence of preparing an environment (including Docker in the supplied image), inspecting PDK/design directories, reviewing configuration, and inspecting synthesis output. No command history or configuration file is included, so exact setup steps cannot be reproduced.

## Selected evidence

![Screenshot associated with the OpenLane environment](./openlane.png)
*OpenLane environment screenshot.*

![Screenshot associated with configuration settings](./config.tcl_2.png)
*Screenshot associated with design configuration.*

![Screenshot associated with synthesis](./synthesis.png)
*Synthesis-related screenshot.*

Additional artifacts include [`docker_1.png`](./docker_1.png), [`sky130A.png`](./sky130A.png), [`designs_inside.png`](./designs_inside.png), [`picorv32a.png`](./picorv32a.png), [`merged_lef.png`](./merged_lef.png), and [`synthesis_results.png`](./synthesis_results.png). These images are retained without assuming unrecorded environment settings or synthesis outcomes.

### Interpreting synthesis evidence

When reviewing a synthesis result, identify the design/top module, selected technology library, warnings, inferred sequential elements, and cell counts. The screenshots do not show enough context to determine whether every warning was addressed. `picorv32a.png` and `merged_lef.png` are retained as supplied; the associated source and generated LEF text are absent, so their exact relationship cannot be verified.

## Scope and limitations

The screenshots provide context for tool and PDK setup and an example design/synthesis view. The repository does not identify the PDK revision, configuration values, exact design inputs, tool versions, or success criteria. It is not possible to reproduce or validate the flow from these images alone.

[PD program index](../README.md) · [Module 2](../module2/README.md)
