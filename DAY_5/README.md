# Day 5 — Case completeness and generated logic

## Overview

This folder contains screenshots associated with complete and incomplete `case`/`if` descriptions, mux/demux examples, a generated design, and a ripple-carry-adder waveform. No RTL, testbenches, generated netlists, VCD files, or logs are included.

## Concepts

In combinational procedural logic, every output must be assigned on every path. If an output must retain its previous value on an uncovered path, synthesis may infer a latch. A `default` branch or a default assignment at the beginning of the block can make intent explicit. Use `x` assignments only when the synthesis and verification intent is understood; they are not a general-purpose safe default.

Generate constructs elaborate repeated hardware at compile/elaboration time. They do not imply a particular circuit is correct or parameterized unless the corresponding source demonstrates it.

### Incomplete and complete combinational assignments

An incomplete assignment describes retention of the old value for the uncovered condition, which is latch behavior. A complete combinational block assigns a value on every path:

```verilog
always @* begin
  case (sel)
    2'b00: y = a;
    2'b01: y = b;
    2'b10: y = c;
    2'b11: y = d;
    default: y = 1'b0;
  endcase
end
```

This is a conceptual single-bit example. For vector outputs, widths and default values must be adjusted. A default assignment at the beginning of a combinational block is another common pattern. Latches are valid when intentional; the design concern is unintended storage created when combinational behavior was intended.

### Generate blocks and scalable structures

A `generate` loop can elaborate repeated hardware, such as bitwise logic over a parameterized vector. The loop executes at elaboration time; it is not a run-time loop in the implemented circuit. Generate bounds, widths, and index ranges must be legal for every supported parameter value. The repository has screenshots associated with generated MUX/demux examples but not their source, so exact parameterization is unknown.

### Verification checklist

1. Enumerate the possible control values and check that each one has defined output behavior.
2. Inspect synthesis output/statistics for inferred latch cells when a combinational block is intended.
3. Test boundary values and all branches in simulation.
4. If reviewing gate-level simulation, use the same stimulus and reset sequence as the RTL simulation before comparing outputs.

Do not infer metastability from an incomplete `case`: incomplete combinational assignment may infer a latch, but metastability requires an asynchronous timing interaction or other physical condition and is a separate issue.

## Evidence

| Artifact | Evidence represented by the filename/context |
| --- | --- |
| [`bad_case_gtk.png`](./bad_case_gtk.png), [`bad_case_yosys.png`](./bad_case_yosys.png), [`bad_case_gls.png`](./bad_case_gls.png) | Screenshots associated with a case-statement example and behavioral/synthesis/GLS views. |
| [`incomp_case_gtk.png`](./incomp_case_gtk.png), [`incomp_case_yosys.png`](./incomp_case_yosys.png), [`partial_case_assign_yosys.png`](./partial_case_assign_yosys.png) | Screenshots associated with incomplete or partial case assignments. |
| [`incomp_if.v_gtk.png`](./incomp_if.v_gtk.png), [`incomp_if_yosys.png`](./incomp_if_yosys.png), [`incomp_if2_gtk.png`](./incomp_if2_gtk.png), [`incomp_if2_yosys.png`](./incomp_if2_yosys.png) | Screenshots associated with incomplete `if` examples. |
| [`comp_case_yosys.png`](./comp_case_yosys.png) | Synthesis screenshot associated with a complete case example. |
| [`mux_generate_gtk.png`](./mux_generate_gtk.png), [`mux_generate_yosys.png`](./mux_generate_yosys.png) | Screenshots associated with a generated MUX. |
| [`demux_case_gtk.png`](./demux_case_gtk.png), [`demux_generate_gtk.png`](./demux_generate_gtk.png) | Screenshots associated with demultiplexer examples. |
| [`rca.v_gtk.png`](./rca.v_gtk.png) | GTKWave screenshot associated with a ripple-carry-adder example. |

![GTKWave screenshot associated with an incomplete case example](./incomp_case_gtk.png)
*GTKWave screenshot associated with an incomplete case example.*

![Yosys screenshot associated with a complete case example](./comp_case_yosys.png)
*Synthesis screenshot associated with a complete case example.*

![GTKWave screenshot associated with a demultiplexer example](./demux_case_gtk.png)
*GTKWave screenshot associated with a demultiplexer example.*

## Tools and reproduction

GTKWave and Yosys are referenced in the screenshots/material. Since the source, testbench, netlist, and run logs are missing, neither latch inference nor functional correctness can be independently confirmed from this repository.

## Learning outcome

Write complete combinational assignments, inspect synthesis for inferred storage, and verify generated structures with source-backed tests.

[Workshop index](../README.md) · [Day 4](../DAY_4/README.md) · [Day 6](../DAY_6/README.md)
