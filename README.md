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

## pinouts

<img width="794" height="437" alt="image" src="https://github.com/user-attachments/assets/7cc00d18-23bd-4e76-aac9-369c10091168" />
<img width="440" height="480" alt="image" src="https://github.com/user-attachments/assets/f79c7421-7ed7-4c57-ab0a-c99271ebbc08" />

## Circuit 
<img width="1080" height="720" alt="schematic_pot" src="https://github.com/user-attachments/assets/7a4f7a57-4beb-43d1-84f6-a46401df63c0" />
<svg width="1080" height="720" viewBox="0 0 1080 720" xmlns="http://www.w3.org/2000/svg" font-family="monospace">

## pictures
<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/da4f51c7-ffa4-44b0-a6f7-5871a0be8558" />  
<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/101b8a3e-1a31-481e-b77a-f8255ce87e88" />
<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/71823241-1e2c-4216-9a7d-42e83b1d037d" />
<img width="1536" height="2048" alt="image" src="https://github.com/user-attachments/assets/0e96156c-3bdc-495e-b9a2-9947ac1754c1" />


https://github.com/user-attachments/assets/1daed020-2bbb-45b4-8abc-e52f3bc1a27e
