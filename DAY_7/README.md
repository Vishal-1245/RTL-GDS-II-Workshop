# Day 7 — Sequence-detector evidence

## Overview

This folder contains a sequence-detector block-diagram screenshot, RTL and gate-level waveform screenshots, and a Yosys statistics/console screenshot. No sequence-detector RTL, testbench, synthesized netlist, waveform dumps, or logs are included.

## Design context

A sequence detector is commonly implemented as a finite-state machine that tracks recent input history and asserts an output when a target pattern is recognized. The supplied block diagram is a synthesized logic graph labeled `sequence_detector`, and the waveform screenshots show signals named `clk`, `reset`, `din`, `detected`, and `detection_count`. The target sequence, overlap policy, reset polarity, and counter semantics cannot be identified reliably from the available files, so they are intentionally not specified here.

## Evidence

### Logic diagram

![Logic graph screenshot labeled sequence_detector](./sequence_detector_block_diagram.png)
*Logic graph screenshot for the design labeled `sequence_detector`.*

### RTL and gate-level waveforms

![GTKWave screenshot associated with the sequence-detector RTL simulation](./sequence_detector_rtl_waveform.png)
*Waveform screenshot associated with the RTL simulation.*

![GTKWave screenshot associated with the sequence-detector gate-level simulation](./sequence_detector_gls_waveforms.png)
*Waveform screenshot associated with the gate-level simulation.*

The waveforms show a clock, reset, input, detection signal, and a detection counter. The filenames associate them with RTL and GLS views; without the source and testbench, the intended sequence, expected number of detections, and equivalence cannot be checked.

### Synthesis statistics

![Yosys console screenshot showing sequence_detector cell statistics and a check summary](./sequence_detcetor_stats.png)
*Yosys console screenshot with displayed cell counts and check summary.*

The screenshot reports a Yosys check summary and cell counts for the displayed design. It is not a complete textual report and does not establish timing, area in a target technology, or physical signoff. The original misspelling in `sequence_detcetor_stats.png` is retained to preserve the existing path.

The screenshot visibly lists 26 cells in total: 8 `$_ANDNOT_`, 1 `$_AND_`, 7 `$_DFF_P_`, 2 `$_NOR_`, 1 `$_NOT_`, 1 `$_ORNOT_`, 5 `$_OR_`, and 1 `$_SDFF_PP0_`. Its check summary says that 0 problems were found. These are transcribed from the image and are not a replacement for the full Yosys log; the cell types are generic internal cells, not a technology-mapped area report.

## Verification approach

For a complete review, define the target sequence and overlap behavior, then create directed input vectors covering detection, non-detection, back-to-back/overlapping cases if applicable, and reset during operation. Check the detection pulse timing and count against an independent expected result. Use identical testbench stimuli for RTL and gate-level runs. The screenshots suggest that RTL/GLS views were made, but do not contain enough inputs or expected values to demonstrate that these checks passed.

## Reproduction requirements

Reproducibility requires the RTL, testbench, Yosys/simulator versions, constraints as applicable, exact commands, and the original log and waveform files. These are not present in this directory.

## Learning outcome

Connect a detector's state/logic representation to observed input/output waveforms, and use synthesis statistics as a structural check while keeping functional verification and implementation signoff as separate questions.

[Workshop index](../README.md) · [Day 6](../DAY_6/README.md) · [PD program](../PD%20program/README.md)
