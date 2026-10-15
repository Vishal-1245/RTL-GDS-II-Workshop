# Day 4 — Assignment semantics and multiplexer examples

## Overview

This folder collects screenshots associated with blocking/non-blocking assignment examples and a ternary-operator multiplexer. The original RTL, testbenches, waveform files, and Yosys logs are not included.

## Concepts

- Blocking assignment (`=`) evaluates and updates in procedural order. It is commonly used in combinational procedural blocks.
- Non-blocking assignment (`<=`) schedules updates for the end of the current simulation time step. It is the standard style for clocked sequential blocks and models concurrent register updates.
- Assignment operators do not, by themselves, determine whether hardware is correct. Correct sensitivity, complete assignments, and intended sequential behavior matter; careless ordering can create simulation races or mismatches.
- A 2:1 MUX is commonly expressed as `assign y = sel ? b : a;`.

### Sequential assignment example

With non-blocking assignments, the right-hand sides are evaluated using the pre-edge values and the updates take effect together:

```verilog
always @(posedge clk) begin
  a <= b;
  c <= a;
end
```

Thus `c` receives the old value of `a` at that edge. This is the usual way to model two cascaded registers. Blocking assignments update immediately in procedural order and can make simulation behavior depend on statement ordering; using them in clocked logic can create unintended simulation behavior and races between processes. The correct diagnosis depends on the complete RTL and testbench, not only on an operator or screenshot.

### Combinational MUX example

```verilog
always @* begin
  case (sel)
    1'b0: y = a;
    1'b1: y = b;
    default: y = 1'b0;
  endcase
end
```

For a two-state 1-bit select, both binary values are listed. The `default` behavior specifies what simulation should do for unknown or otherwise unmatched values; select a default that matches the design's verification and synthesis intent. Alternatively, use the continuous assignment shown above.

### Review checklist

- Use non-blocking assignments for edge-triggered state updates as a consistent RTL style.
- Use blocking assignments in combinational procedural blocks and assign every output on every path.
- Avoid multiple procedural drivers for the same variable.
- Compare simulation with the intended state transition/Boolean equations. A matching-looking synthesis diagram alone does not prove functional equivalence.

## Evidence

| Artifact | Evidence represented by the filename/context |
| --- | --- |
| [`bad_mux_gtk.png`](./bad_mux_gtk.png) and [`bad_mux_yosys.png`](./bad_mux_yosys.png) | Screenshots associated with the “bad MUX” example. |
| [`blocking_caveat_gtk.png`](./blocking_caveat_gtk.png) and [`blocking_caveat_yosys.png`](./blocking_caveat_yosys.png) | Waveform and synthesis screenshots associated with a blocking-assignment caveat. |
| [`ternary_operator_mux_rtl.png`](./ternary_operator_mux_rtl.png) | MUX RTL view. |
| [`ternary_operator_mux_yoys_rtl.png`](./ternary_operator_mux_yoys_rtl.png) | Synthesis-related MUX screenshot; the supplied filename spelling is preserved. |

![GTKWave screenshot associated with the blocking-assignment caveat](./blocking_caveat_gtk.png)
*GTKWave screenshot associated with the blocking-assignment caveat.*

![MUX RTL screenshot associated with the ternary operator](./ternary_operator_mux_rtl.png)
*RTL-view screenshot associated with a ternary-operator MUX.*

## Tools and reproduction

GTKWave and Yosys are referenced by the images. The source and exact run commands are absent; screenshots alone do not establish a simulation/synthesis mismatch or its cause.

## Learning outcome

Choose procedural assignment semantics according to the intended combinational or sequential behavior, then validate with a testbench and inspect synthesis output.

[Workshop index](../README.md) · [Day 3](../DAY_3/README.md) · [Day 5](../DAY_5/README.md)
