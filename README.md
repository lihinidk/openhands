# Task
Implement a parameterized up-counter.

## DUT requirements
- File: rtl/counter.sv
- Module name: counter
- Parameters: WIDTH (default 8)
- Ports:
  - input  logic clk
  - input  logic rst_n        (active-low synchronous reset)
  - input  logic en
  - output logic [WIDTH-1:0] q
- Behavior:
  - On rising edge of clk:
    - if !rst_n: q <= 0
    - else if en: q <= q + 1
    - else: hold

## Verification requirements (cocotb)
- File: tb/test_counter.py
- Must test:
  1) reset sets q=0
  2) en increments
  3) en=0 holds
  4) wraparound at max value (for small WIDTH like 4)

## Harness requirements
- Create harness/scripts and harness/outputs
- Run:
  - Yosys: read + synth + stat + check (log to harness/outputs/yosys.log)
  - Cocotb sim with Icarus (log to harness/outputs/sim.log)
- The agent must run the harness and fix issues until it passes.
