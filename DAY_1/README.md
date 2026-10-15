# Day 1 — Multiplexer fundamentals

## Overview

This folder documents introductory RTL work on a 2:1 multiplexer. The repository contains two waveform screenshots; it does not contain the RTL, testbench, VCD file, or tool log used to produce them.

## Concepts

A 2:1 multiplexer selects one of two data inputs using a select signal:

```text
y = (~sel & a) | (sel & b)
```

Equivalent RTL can use a conditional expression, an `if` statement, or a `case` statement. All branches must define the output for combinational logic.

### Truth table

| `sel` | `y` |
| --- | --- |
| 0 | `a` |
| 1 | `b` |

For a one-bit MUX, the equation and a concise synthesizable RTL form are:

```verilog
assign y = sel ? b : a;
```

The select value chooses the data input; the MUX does not store state. For a multi-bit datapath, `a`, `b`, and `y` can be vectors of matching width while `sel` remains one bit.

### What to verify

- Exercise both select values with both possible values on each data input. That gives eight input combinations for a 1-bit 2:1 MUX.
- Check that a change on the unselected input does not affect `y`.
- Check that a change on the selected input is reflected at `y` after the combinational simulation update.
- In a synthesis view, look for selection logic rather than a clocked storage element. Exact gate mapping depends on the synthesis target and constraints.

## Evidence

| Artifact | What it shows |
| --- | --- |
| [`good_mux_both.png`](./good_mux_both.png) | Screenshot associated with the MUX example; the original image is retained as supplied. |
| [`good_mux_gtk.png`](./good_mux_gtk.png) | GTKWave screenshot associated with the MUX example. |

The screenshots are illustrative evidence, not a substitute for the missing source and reproducible simulation inputs.

![GTKWave screenshot associated with the 2:1 MUX example](./good_mux_gtk.png)
*Figure 1. GTKWave view associated with the 2:1 MUX exercise.*

![Waveform screenshot associated with the MUX example](./good_mux_both.png)
*Figure 2. Waveform evidence retained from the MUX exercise.*

## Tools and reproduction

The existing notes refer to Icarus Verilog, GTKWave, and Yosys. No source files or exact commands are included in this folder, so the original run cannot be reproduced from this repository alone. For a new design, a typical sequence is to compile the actual RTL and testbench with Icarus Verilog, run the resulting simulation, inspect the generated VCD with GTKWave, and then synthesize the same RTL with the intended target in Yosys. Replace all filenames and top-module names with the ones in the design being evaluated; do not assume files named `mux.v` or `tb_mux.v` exist here.

When presenting results, include the RTL, testbench, tool versions, commands, and waveform/netlist outputs alongside screenshots. This makes the MUX behavior independently reviewable.

## Learning outcome

Understand selection logic, relate a select transition to the chosen data input, and verify a combinational implementation with a testbench and waveform.

[Workshop index](../README.md) · [Day 2](../DAY_2/README.md)
