# Day 6 — BabySoC simulation waveform evidence

## Overview

This folder contains two GTKWave screenshots labeled pre-synthesis and post-synthesis. The displayed hierarchy includes `vsdbabysoc_tb`; visible signal names include `CLK`, `OUT`, `Enb_CP`, `Enb_VCO`, `RV_TO_DAC[9:0]`, `VCO_IN`, `VREFH`, and `reset`.

The repository contains no HDL sources, testbench, VCD/FST files, simulator command, or run log. Therefore the screenshots document a waveform view but do not allow reproduction or a source-level assessment of the stimulus and expected behavior.

## Evidence

### Pre-synthesis waveform

![GTKWave screenshot labeled pre-synthesis with BabySoC testbench and DAC-related signals](./pre_synth%20waveform.png)
*Pre-synthesis GTKWave screenshot; signals are visible, but source and expected values are not included.*

### Post-synthesis waveform

![GTKWave screenshot labeled post-synthesis with BabySoC testbench and DAC-related signals](./post_synth_sim%20waveforms.png)
*Post-synthesis GTKWave screenshot; the image does not establish RTL/netlist equivalence.*

The screenshots show signal activity and signal names. They do not, by themselves, demonstrate RTL-to-netlist equivalence, complete test coverage, or a passing verification result.

## Reading the waveform

The top-level testbench name shown in the GTKWave hierarchy is `vsdbabysoc_tb`. Visible signals include the clock (`CLK`), output (`OUT`), enable controls (`Enb_CP`, `Enb_VCO`), a 10-bit bus (`RV_TO_DAC[9:0]`), reference/control signals (`VCO_IN`, `VREFH`), and `reset`. The pre-synthesis view spans roughly 0–85 µs in the displayed window. These labels describe what is visible in the screenshots; the design's intended function, test vectors, clock period, and expected output values are not provided.

When inspecting a waveform, first locate reset assertion and release, then check clock edges and control enables, and finally compare data-bus activity to the output behavior specified by the design. For a bus displayed as individual bits, GTKWave can show bit-level transitions; the expected numeric interpretation still depends on bus signedness and encoding.

## Comparing pre- and post-synthesis simulations

For a meaningful comparison, use the same testbench stimulus, reset sequence, clock configuration, and observation points. Account for possible gate-level delays and initialization semantics. Compare functional values at corresponding stable times rather than assuming every transition must occur at an identical timestamp. Record the simulator, synthesis options, libraries (if technology-mapped), and any timing model used. None of this run metadata is included with these images.

## Reproduction requirements

To make this evidence reproducible, include or link to the design sources, testbench, simulator and synthesis versions, exact commands/scripts, and generated waveform files. None are currently checked in here.

## Learning outcome

Use waveform viewers to inspect signals over time, and support verification conclusions with the source, expected results, and a repeatable simulation—not only screenshots.

[Workshop index](../README.md) · [Day 5](../DAY_5/README.md) · [Day 7](../DAY_7/README.md)
