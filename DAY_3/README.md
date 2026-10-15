# Day 3 — Constant logic and synthesis optimization

## Overview

This folder contains screenshots associated with constant-input DFF examples, a counter, and Yosys optimization. It does not contain the RTL, testbench, Yosys scripts, or textual reports behind the images.

## Concepts

Synthesis can propagate constants, simplify Boolean expressions, and remove logic that has no effect on observable outputs. A register with a constant data input may simplify depending on its reset, enables, and use in the design. The actual transformation must be checked in the synthesized netlist and report; it cannot be inferred fully from an image filename.

Counters are sequential arithmetic structures. Their width, reset, enable, and overflow behavior should be explicit in the RTL and testbench.

### Why a constant input does not always remove a register

If a DFF's data input is tied to a constant, the output may still depend on its reset, initialization assumptions, enable, or observable timing. Optimization is contextual: inspect the resulting netlist and statistics to determine whether the register remains, simplifies, or disappears. A waveform showing a constant value alone does not prove which hardware was inferred.

### Optimization review workflow

For a reproducible comparison, use the same top module and inputs before and after optimization, then record:

1. The initial cell/statistics report.
2. The optimization passes and target technology, if any.
3. The resulting netlist and final cell/statistics report.
4. A functional check using the same testbench or an equivalence check.

Generic Yosys command patterns (replace the example filenames and top name) are:

```text
read_verilog design.v
hierarchy -top top
proc
opt
check
stat
```

The commands are guidance only; this repository does not include the design source or a saved Yosys script. A technology-mapped synthesis flow may use different passes and libraries, so generic cell counts are not directly comparable to mapped area or timing.

### Counter considerations

An `N`-bit unsigned counter naturally wraps modulo `2^N` when its value exceeds the representable range. Whether it starts from zero, clears synchronously/asynchronously, increments every cycle, or holds under an enable is design-specific. Check those details against the implementation rather than inferring them from the counter screenshot.

## Evidence

| Artifact | What the filename associates it with |
| --- | --- |
| [`dff_const_gtk.png`](./dff_const_gtk.png) and [`dff_const_yosys.png`](./dff_const_yosys.png) | Basic constant-DFF waveform and synthesis views. |
| [`deff_const2_gtk.png`](./deff_const2_gtk.png) and [`deff_const2_yosys.png`](./deff_const2_yosys.png) | Second constant-DFF example. |
| [`deff_const3_gtk.png`](./deff_const3_gtk.png) and [`dff_const3_yosys.png`](./dff_const3_yosys.png) | Third constant-DFF example. |
| [`good_counter.png`](./good_counter.png) | Counter example screenshot. |
| [`opt_check.png`](./opt_check.png), [`opt_check2.png`](./opt_check2.png), [`opt_check3.png`](./opt_check3.png) | Screenshots associated with optimization checks. |

![GTKWave screenshot associated with a constant-input DFF](./dff_const_gtk.png)
*GTKWave screenshot associated with a constant-input DFF.*

![Screenshot associated with Yosys synthesis of the constant-input DFF](./dff_const_yosys.png)
*Synthesis screenshot associated with the constant-input DFF.*

![Counter example screenshot](./good_counter.png)
*Counter example screenshot.*

## Tools and reproduction

The images refer to GTKWave and Yosys. Source files, VCDs, exact synthesis commands, and machine-readable reports are not present, so these examples cannot be independently rerun or quantitatively compared from this repository.

## Learning outcome

Use synthesis reports and netlist comparisons—not RTL appearance alone—to understand constant propagation and logic optimization.

[Workshop index](../README.md) · [Day 2](../DAY_2/README.md) · [Day 4](../DAY_4/README.md)
