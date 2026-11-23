 This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

This project implements a **4-bit BCD (Binary-Coded Decimal) to 7-Segment Decoder** using purely combinational logic gates (`NOT`, `AND`, and `OR`)[cite: 1]. 

The circuit takes a 4-bit binary input word represented by four lines from the input port (`ui_in[3:0]`):
* `ui_in[0]` (**z**, bit 0 — LSB)[cite: 1]
* `ui_in[1]` (**y**, bit 1)[cite: 1]
* `ui_in[2]` (**x**, bit 2)[cite: 1]
* `ui_in[3]` (**w**, bit 3 — MSB)[cite: 1]

These four inputs and their inverted signals (generated via `NOT` gates on `z`, `y`, and `x`) feed into a sum-of-products logic array made of 2-input `AND` and `OR` gates[cite: 1]. Each of the 7 combinational logic branches computes the boolean equation required to drive one individual segment (`a`, `b`, `c`, `d`, `e`, `f`, `g`) of a common-cathode 7-segment display, routing the resulting 7-bit output to `uo_out[6:0]`[cite: 1].

## How to test
1. Set the input switches:** Use the 4-bit DIP switches connected to `ui_in[3:0]` (`w, x, y, z`) to input a binary value between `0000` (0) and `1001` (9)[cite: 1].
2. Observe the display:** Because the circuit is purely combinational, the 7-segment display connected to `uo_out[6:0]` will immediately update to show the corresponding decimal digit (for example, setting `ui_in[3:0] = 0000` illuminates segments `a, b, c, d, e, f` to display the number **0**)[cite: 1].
3. **Verify all states:** Cycle through all binary combinations from `0000` to `1001` and confirm that digits `0` through `9` render cleanly on the display.

## External hardware

Common-cathode 7-segment display** connected to `uo_out[6:0]` (`abcdefg`) with its common pin tied to `GND` (included on the standard Tiny Tapeout demo board)[cite: 1].
-bit DIP switch** connected to `ui_in[3:0]` to manually toggle the binary inputs[cite: 1].
Explain how to use your project

## External hardware

List external hardware used in your project (e.g. PMOD, LED display, etc), if any
