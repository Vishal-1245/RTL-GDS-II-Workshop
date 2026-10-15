# Module 2 — Floorplan and placement evidence

## Overview

This module contains screenshots associated with floorplanning, I/O placement, layout, and placement. No floorplan constraints, TCL, DEF/ODB, logs, or generated reports are included.

## Concepts and workflow

Floorplanning sets the physical region and establishes macro/I/O constraints. I/O placement assigns ports to boundary locations according to interface and pin constraints. Placement maps standard cells to legal sites while accounting for connectivity, timing, and congestion. These choices affect later routing and timing; images without constraints/reports cannot quantify those effects.

The screenshot names indicate that floorplan Tcl/configuration and an I/O placer log were viewed, followed by floorplan/layout/placement views. The actual Tcl and log text are not present, so coordinates, utilization targets, pin assignments, and completion status are unknown.

## Selected evidence

![Floorplan screenshot](./floorplan.png)
*Floorplan view.*

![Floorplan results screenshot](./floorplan_results_def.png)
*Floorplan results view.*

![Placement screenshot](./placement.png)
*Placement view.*

Other supplied views include [`floorplan_tcl.png`](./floorplan_tcl.png), [`ioplacer_log.png`](./ioplacer_log.png), [`layout.png`](./layout.png), and [`layout_zoomed.png`](./layout_zoomed.png). Their names identify the associated subject, but the screenshot alone does not establish floorplan constraints, legality, congestion, or completion status.

## Physical-design review checklist

- Check core/die boundaries, aspect ratio, and macro locations against the intended floorplan.
- Check pin locations and spacing against interface constraints.
- Review placement legality and utilization when reports are available.
- Inspect congestion and routing access, especially around macros and dense regions.
- Confirm which stage a view represents; a floorplan image is not a routed result.

## Workflow context

Floorplanning defines the region and physical constraints used by later placement and routing. Placement assigns cells to legal locations within that region. The folder shows screenshots related to these activities but does not include sufficient inputs or logs to reconstruct a design-specific workflow.

[PD program index](../README.md) · [Module 1](../module1/README.md) · [Module 3](../module3/README.md)
