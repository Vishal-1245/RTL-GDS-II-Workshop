# Module 5 — CTS, placement, and routing evidence

## Overview

This module contains screenshots associated with clock-tree synthesis (CTS), placement, and routing. The folder does not contain the design, flow configuration, constraints, generated databases, reports, or logs, so stage completion and signoff cannot be established from the image names.

## Stage context

- **Placement:** assigns standard cells to physical sites and may be refined to improve timing or routability.
- **CTS:** inserts and sizes clock cells to distribute clocks to sequential endpoints. Review skew, insertion delay, transition, and clock-related setup/hold effects.
- **Routing:** connects cell pins using technology routing layers. Review congestion, unrouted nets, design-rule violations, and post-route parasitics.
- **Signoff:** requires the relevant timing and physical-verification checks for the target flow; a routed GUI view alone is not signoff.

The screenshots are associated with these stages, but quantitative logs and machine-readable reports are absent, so no pass/fail assessment can be made.

## Evidence

![Screenshot associated with CTS](./run_cts_5.png)
*Screenshot associated with clock-tree synthesis.*

![Screenshot associated with placement](./Run_placement_5.png)
*Screenshot associated with placement.*

![Screenshot associated with routing](./Run_routing_5.png)
*Screenshot associated with routing.*

## Suggested report set for evaluation

To supplement screenshots, provide placement legality/congestion results, CTS clock metrics, routing completion and DRC summaries, and post-route setup/hold reports with the constraints and technology corner used. These reports are not currently in this module.

## Physical-design context

CTS builds a clock distribution network to deliver clock signals to sequential cells. Placement and routing establish physical locations and interconnect. Timing and physical verification depend on design constraints and reports at each stage; the screenshots provide visual context, not a verified pass/fail result.

[PD program index](../README.md) · [Module 4](../module4/README.md) · [BabySoC post-route evidence](../../PostRoute_STA_VSDBabySOC_OpenRoad/README.md)
