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
<svg width="1080" height="720" viewBox="0 0 1080 720" xmlns="http://www.w3.org/2000/svg" font-family="monospace">
<title>10-Channel LED Sequencer - with potentiometer speed control</title>
<desc>555 astable oscillator clocking a CD4017 decade counter. R2 is replaced with a potentiometer wired as a two-terminal rheostat, with wiper jumpered to one outer terminal, to make the chase speed adjustable.</desc>
<rect width="1080" height="720" fill="#ffffff"/>

<defs>
  <g id="resistorH">
    <path d="M0,0 L8,0 L14,-8 L22,8 L30,-8 L38,8 L46,-8 L52,0 L60,0"
          fill="none" stroke="#111" stroke-width="2" stroke-linejoin="round"/>
  </g>
  <g id="resistorV">
    <path d="M0,0 L0,8 L8,14 L-8,22 L8,30 L-8,38 L8,46 L0,52 L0,60"
          fill="none" stroke="#111" stroke-width="2" stroke-linejoin="round"/>
  </g>
  <g id="capV">
    <line x1="0" y1="0" x2="0" y2="12" stroke="#111" stroke-width="2"/>
    <line x1="-12" y1="12" x2="12" y2="12" stroke="#111" stroke-width="2.5"/>
    <line x1="-12" y1="18" x2="12" y2="18" stroke="#111" stroke-width="2.5"/>
    <line x1="0" y1="18" x2="0" y2="30" stroke="#111" stroke-width="2"/>
  </g>
  <g id="ecapV">
    <line x1="0" y1="0" x2="0" y2="12" stroke="#111" stroke-width="2"/>
    <line x1="-12" y1="12" x2="12" y2="12" stroke="#111" stroke-width="2.5"/>
    <path d="M-12,18 Q0,26 12,18" fill="none" stroke="#111" stroke-width="2.5"/>
    <line x1="0" y1="22" x2="0" y2="30" stroke="#111" stroke-width="2"/>
    <text x="16" y="10" font-size="12">+</text>
  </g>
  <g id="led">
    <path d="M0,-10 L0,10 L18,0 Z" fill="none" stroke="#111" stroke-width="2"/>
    <line x1="18" y1="-10" x2="18" y2="10" stroke="#111" stroke-width="2"/>
    <line x1="18" y1="0" x2="30" y2="0" stroke="#111" stroke-width="2"/>
    <path d="M14,-16 L24,-26 M20,-26 L24,-26 L24,-22" fill="none" stroke="#111" stroke-width="1.5"/>
    <path d="M20,-9 L30,-19 M26,-19 L30,-19 L30,-15" fill="none" stroke="#111" stroke-width="1.5"/>
  </g>
  <!-- vertical potentiometer: body terminals at local (0,0) top and (0,60) bottom,
       wiper terminal at local (24,30) with arrow pointing into the body -->
  <g id="potV">
    <path d="M0,0 L0,8 L8,14 L-8,22 L8,30 L-8,38 L8,46 L0,52 L0,60"
          fill="none" stroke="#111" stroke-width="2" stroke-linejoin="round"/>
    <line x1="24" y1="30" x2="4" y2="30" stroke="#111" stroke-width="2"/>
    <path d="M4,30 L10,26 M4,30 L10,34" fill="none" stroke="#111" stroke-width="2"/>
  </g>
</defs>

<!-- power rails -->
<line x1="30" y1="40" x2="1040" y2="40" stroke="#111" stroke-width="2.5"/>
<text x="30" y="27" font-size="15" font-weight="bold">+9V (VCC / VDD)</text>
<line x1="30" y1="680" x2="1040" y2="680" stroke="#111" stroke-width="2.5"/>
<text x="30" y="700" font-size="15" font-weight="bold">GND (VSS)</text>

<!-- ===== 555 IC ===== -->
<rect x="90" y="180" width="140" height="220" rx="4" fill="#fbfbfb" stroke="#111" stroke-width="1.8"/>
<text x="160" y="203" text-anchor="middle" font-size="14" font-weight="bold">NE555P</text>
<g font-size="11.5">
<text x="98" y="228">1 GND</text>
<text x="98" y="248">2 TRIG</text>
<text x="98" y="268">3 OUT</text>
<text x="98" y="288">4 RESET</text>
<text x="98" y="308">5 CV</text>
<text x="98" y="328">6 THR</text>
<text x="98" y="348">7 DISCH</text>
<text x="98" y="368">8 VCC</text>
</g>

<line x1="160" y1="180" x2="160" y2="40" stroke="#111" stroke-width="2"/>
<line x1="160" y1="400" x2="160" y2="680" stroke="#111" stroke-width="2"/>

<!-- R1: rail to node A -->
<use href="#resistorV" x="290" y="40"/>
<line x1="290" y1="100" x2="290" y2="348" stroke="#111" stroke-width="2"/>
<text x="325" y="130" font-size="12">R1  1k&#8486;</text>

<!-- node A -->
<circle cx="290" cy="348" r="3.5" fill="#111"/>
<line x1="230" y1="348" x2="290" y2="348" stroke="#111" stroke-width="2"/>
<text x="325" y="352" font-size="12">node A (pin 7, DISCH)</text>

<!-- POT wired as rheostat: top terminal = node A, wiper jumpered to bottom terminal = node B -->
<use href="#potV" x="290" y="348"/>
<line x1="314" y1="378" x2="330" y2="378" stroke="#111" stroke-width="2"/>
<line x1="330" y1="378" x2="330" y2="408" stroke="#111" stroke-width="2"/>
<line x1="330" y1="408" x2="290" y2="408" stroke="#111" stroke-width="2"/>
<text x="345" y="373" font-size="11">wiper, jumpered</text>
<text x="345" y="386" font-size="11">to bottom terminal</text>
<text x="325" y="410" font-size="12" opacity="0">.</text>
<text x="640" y="335" font-size="12">R2 replaced with POT1</text>
<text x="640" y="350" font-size="12">100k&#8486; linear, wired as</text>
<text x="640" y="365" font-size="12">2-terminal rheostat</text>
<line x1="600" y1="355" x2="640" y2="355" stroke="#111" stroke-width="1" stroke-dasharray="3,3"/>

<!-- node B -->
<circle cx="290" cy="408" r="3.5" fill="#111"/>
<line x1="230" y1="248" x2="245" y2="248" stroke="#111" stroke-width="2"/>
<line x1="245" y1="248" x2="245" y2="408" stroke="#111" stroke-width="2"/>
<line x1="245" y1="408" x2="290" y2="408" stroke="#111" stroke-width="2"/>
<line x1="230" y1="328" x2="290" y2="328" stroke="#111" stroke-width="2"/>
<line x1="290" y1="328" x2="290" y2="408" stroke="#111" stroke-width="2"/>
<text x="325" y="412" font-size="12">node B (pins 2 &amp; 6, TRIG/THR)</text>

<!-- C1: node B to GND -->
<use href="#ecapV" x="290" y="408"/>
<line x1="290" y1="438" x2="290" y2="680" stroke="#111" stroke-width="2"/>
<text x="325" y="435" font-size="12">C1  10&#181;F (+ toward node B)</text>

<!-- decoupling cap on 555 -->
<use href="#capV" x="55" y="40"/>
<line x1="55" y1="70" x2="55" y2="680" stroke="#111" stroke-width="2"/>
<text x="10" y="60" font-size="11">100nF</text>

<!-- pin5 CV bypass cap -->
<line x1="230" y1="308" x2="390" y2="308" stroke="#111" stroke-width="2"/>
<use href="#capV" x="390" y="308"/>
<line x1="390" y1="338" x2="390" y2="680" stroke="#111" stroke-width="2"/>
<text x="405" y="303" font-size="11">10nF</text>

<!-- 555 OUT to CD4017 CLK -->
<line x1="230" y1="268" x2="440" y2="268" stroke="#111" stroke-width="2"/>
<line x1="440" y1="268" x2="440" y2="198" stroke="#111" stroke-width="2"/>
<line x1="440" y1="198" x2="470" y2="198" stroke="#111" stroke-width="2"/>

<!-- ===== CD4017 ===== -->
<rect x="470" y="150" width="200" height="330" rx="4" fill="#fbfbfb" stroke="#111" stroke-width="1.8"/>
<text x="570" y="173" text-anchor="middle" font-size="14" font-weight="bold">CD4017</text>
<g font-size="11.5">
<text x="480" y="203">14 CLK</text>
<text x="480" y="223">13 CLK INH</text>
<text x="480" y="243">15 RESET</text>
<text x="480" y="263">16 VDD</text>
<text x="480" y="283">8  VSS</text>
<text x="480" y="303">12 CARRY OUT (n/c)</text>
<text x="480" y="335">Q0=p3  Q1=p2  Q2=p4</text>
<text x="480" y="353">Q3=p7  Q4=p10 Q5=p1</text>
<text x="480" y="371">Q6=p5  Q7=p6</text>
<text x="480" y="389">Q8=p9  Q9=p11</text>
</g>

<line x1="570" y1="150" x2="570" y2="40" stroke="#111" stroke-width="2"/>
<line x1="530" y1="480" x2="530" y2="680" stroke="#111" stroke-width="2"/>

<use href="#capV" x="700" y="40"/>
<line x1="700" y1="70" x2="700" y2="680" stroke="#111" stroke-width="2"/>
<text x="715" y="60" font-size="11">100nF</text>

<line x1="470" y1="223" x2="430" y2="223" stroke="#111" stroke-width="2"/>
<line x1="430" y1="223" x2="430" y2="680" stroke="#111" stroke-width="2"/>
<line x1="470" y1="243" x2="445" y2="243" stroke="#111" stroke-width="2"/>
<line x1="445" y1="243" x2="445" y2="680" stroke="#111" stroke-width="2"/>

<!-- ===== 10 LED branches ===== -->
<g stroke="#111" stroke-width="2" fill="none">
<line x1="670" y1="210" x2="740" y2="210"/>
<line x1="670" y1="234" x2="740" y2="234"/>
<line x1="670" y1="258" x2="740" y2="258"/>
<line x1="670" y1="282" x2="740" y2="282"/>
<line x1="670" y1="306" x2="740" y2="306"/>
<line x1="670" y1="330" x2="740" y2="330"/>
<line x1="670" y1="354" x2="740" y2="354"/>
<line x1="670" y1="378" x2="740" y2="378"/>
<line x1="670" y1="402" x2="740" y2="402"/>
<line x1="670" y1="426" x2="740" y2="426"/>
</g>

<use href="#resistorH" x="740" y="210"/>
<use href="#resistorH" x="740" y="234"/>
<use href="#resistorH" x="740" y="258"/>
<use href="#resistorH" x="740" y="282"/>
<use href="#resistorH" x="740" y="306"/>
<use href="#resistorH" x="740" y="330"/>
<use href="#resistorH" x="740" y="354"/>
<use href="#resistorH" x="740" y="378"/>
<use href="#resistorH" x="740" y="402"/>
<use href="#resistorH" x="740" y="426"/>

<g stroke="#111" stroke-width="2" fill="none">
<line x1="800" y1="210" x2="850" y2="210"/>
<line x1="800" y1="234" x2="850" y2="234"/>
<line x1="800" y1="258" x2="850" y2="258"/>
<line x1="800" y1="282" x2="850" y2="282"/>
<line x1="800" y1="306" x2="850" y2="306"/>
<line x1="800" y1="330" x2="850" y2="330"/>
<line x1="800" y1="354" x2="850" y2="354"/>
<line x1="800" y1="378" x2="850" y2="378"/>
<line x1="800" y1="402" x2="850" y2="402"/>
<line x1="800" y1="426" x2="850" y2="426"/>
</g>

<use href="#led" x="850" y="210"/>
<use href="#led" x="850" y="234"/>
<use href="#led" x="850" y="258"/>
<use href="#led" x="850" y="282"/>
<use href="#led" x="850" y="306"/>
<use href="#led" x="850" y="330"/>
<use href="#led" x="850" y="354"/>
<use href="#led" x="850" y="378"/>
<use href="#led" x="850" y="402"/>
<use href="#led" x="850" y="426"/>

<g stroke="#111" stroke-width="2" fill="none">
<line x1="880" y1="210" x2="990" y2="210"/>
<line x1="880" y1="234" x2="990" y2="234"/>
<line x1="880" y1="258" x2="990" y2="258"/>
<line x1="880" y1="282" x2="990" y2="282"/>
<line x1="880" y1="306" x2="990" y2="306"/>
<line x1="880" y1="330" x2="990" y2="330"/>
<line x1="880" y1="354" x2="990" y2="354"/>
<line x1="880" y1="378" x2="990" y2="378"/>
<line x1="880" y1="402" x2="990" y2="402"/>
<line x1="880" y1="426" x2="990" y2="426"/>
<line x1="990" y1="210" x2="990" y2="680"/>
</g>

<g font-size="12">
<text x="920" y="203">Q0</text>
<text x="920" y="227">Q1</text>
<text x="920" y="251">Q2</text>
<text x="920" y="275">Q3</text>
<text x="920" y="299">Q4</text>
<text x="920" y="323">Q5</text>
<text x="920" y="347">Q6</text>
<text x="920" y="371">Q7</text>
<text x="920" y="395">Q8</text>
<text x="920" y="419">Q9</text>
<text x="770" y="194" text-anchor="middle">all 470&#8486;</text>
<text x="1000" y="450">cathode bus</text>
<text x="1000" y="464">-&gt; GND</text>
</g>

<text x="540" y="20" text-anchor="middle" font-size="15" font-weight="bold">10-Channel LED Sequencer with speed control</text>
<text x="540" y="715" text-anchor="middle" font-size="12" fill="#555">POT1 (rheostat-wired) sets chase speed; 555 astable (U1) clocks CD4017 (U2) driving LED0-LED9</text>
</svg>
