# Day 2 — Sequential logic and hierarchy

## Overview

This folder contains screenshots associated with D flip-flop/reset behavior and multi-module design. It has no RTL, testbench, waveform dump, or synthesis source, so the original examples cannot be reproduced from this folder alone.

## Concepts

- A D flip-flop samples its data input at an active clock edge.
- A synchronous reset is sampled at the clock edge; an asynchronous reset can act independently of that edge. Reset polarity and assertion behavior depend on the design.
- Hierarchical RTL composes modules through explicit ports. Flattening is a synthesis transformation that can remove hierarchy in the netlist; it does not change the intended function when performed correctly.
- Asynchronous control signals crossing clock domains require careful handling; a screenshot alone cannot establish whether metastability risk was addressed.

### RTL idioms

These short examples illustrate reset styles; they are conceptual examples, not source recovered from the screenshots.

```verilog
// Active-low asynchronous reset
always @(posedge clk or negedge reset_n) begin
  if (!reset_n)
    q <= 1'b0;
  else
    q <= d;
end
```

```verilog
// Active-high synchronous reset
always @(posedge clk) begin
  if (reset)
    q <= 1'b0;
  else
    q <= d;
end
```

The reset polarity and value must match the interface and implementation requirements. In either style, sequential state updates conventionally use non-blocking assignments. Asynchronous reset assertion can occur between clock edges; its deassertion must be handled according to the receiving clock domain's requirements.

### Hierarchy and flattening

A parent module connects child-module ports to signals. Keeping hierarchy can make a design easier to understand and debug; flattening can expose logic across module boundaries for optimization or produce a single-level netlist. Inspect the tool's hierarchy and statistics before/after transformation rather than assuming flattening always improves area or timing.

### Review checklist

1. Identify the active clock edge and reset polarity from the RTL/interface.
2. In a waveform, check reset assertion, reset release, and behavior at subsequent clock edges.
3. Confirm the stored value changes only according to the specified reset/data behavior.
4. For hierarchy screenshots, trace port names and direction; verify that flattened logic represents the intended connectivity.

## Evidence

| Artifact | Evidence represented by the filename/context |
| --- | --- |
| [`dff_asy_gtk.png`](./dff_asy_gtk.png) | GTKWave screenshot associated with an asynchronous-reset DFF. |
| [`dff_syncres.png`](./dff_syncres.png) | Screenshot associated with synchronous reset behavior. |
| [`asynchronous.png`](./asynchronous.png) | Asynchronous-design topic illustration. |
| [`multiple_modules.png`](./multiple_modules.png) | Multi-module hierarchy illustration. |
| [`sub_module1.png`](./sub_module1.png) | Submodule illustration. |
| [`flatten_netlist.png`](./flatten_netlist.png) | Screenshot associated with a flattened netlist. |

![GTKWave screenshot associated with an asynchronous-reset DFF](./dff_asy_gtk.png)
*Figure 1. GTKWave screenshot associated with an asynchronous-reset DFF.*

![Screenshot associated with synchronous reset behavior](./dff_syncres.png)
*Figure 2. Screenshot associated with synchronous reset behavior.*

![Screenshot associated with a flattened netlist](./flatten_netlist.png)
*Figure 3. Netlist screenshot associated with flattening.*

## Tools and reproduction

GTKWave and Yosys are referenced by the existing material. Exact source, commands, tool versions, and run logs are absent. Do not treat the former example commands as executable repository instructions: their referenced HDL and VCD files are not checked in.

## Learning outcome

Distinguish clocked storage from combinational logic, understand reset timing, and recognize how hierarchy is represented in a design flow.

[Workshop index](../README.md) · [Day 1](../DAY_1/README.md) · [Day 3](../DAY_3/README.md)
