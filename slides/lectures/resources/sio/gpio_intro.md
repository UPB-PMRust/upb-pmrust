---
layout: section
---
# GPIO
General Purpose Input Output - Why


---
layout: two-cols
---

# Why GPIO can be complex

### This is a minimalistic representation of a typical GPIO ping

<br>

> the diodes are topical over and under voltage protections

<br>

> C represents the topical "parasitic" capacity 

<br>

> Rpu = Pull-up Resistor with a transistor for on/ off towards the positive supply rail 

:: right ::

<br>
<br>
<br>
<br>


 <img src="./gpio_simple.png" class="h-80 rounded">

---
layout: two-cols
---

# AVR 328P GPIO

- PUD: PULLUP DISABLE
- SLEEP: SLEEP CONTROL
- CLKI/O: I/O CLOCK

- WDx: WRITE DDRx
- RDx: READ DDRx
- WRx: WRITE PORTx
- RRx: READ PORTx REGISTER
- RPx: READ PORTx PIN
- WPX: WRITE PINx REGISTER

:: right ::

<img src="./gpio_328p.png">
