# 10-Channel LED Sequencer (555 + CD4017)

A discrete-logic LED chaser circuit using an NE555 timer configured as an
astable oscillator to clock a CD4017 decade counter. Each of the counter's
ten outputs drives a single LED, producing a sequential "chase" effect with
one LED active at a time.

## Features
- Adjustable chase speed via potentiometer (R2 in the 555 timing network)
- Fully discrete — no microcontroller required
- Configurable loop length (tie RESET to any Qx output to shorten the cycle)

## Hardware
- NE555P timer
- CD4017 decade counter/divider
- 10x LED + 470Ω resistors
- R1 = 1kΩ, R2 = 47–100kΩ (or pot), C1 = 10µF
- 9V supply

## Circuit
555 astable output (pin 3) clocks the CD4017 (pin 14). CLK INH and RESET
tied to GND for free-running 0–9 count. Each Qx output drives an LED
through a current-limiting resistor.
