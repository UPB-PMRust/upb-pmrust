---
layout: section
---

# Embedded Software 

---

# Why Embedded Software is Different

<v-click>

## It tends to be very application-specific
*  It comes in the form of a blob, which contains data, configuration, application and drivers
* While some operating systems exist for embedded devices, they are very rare

</v-click>

<v-click>


## It uses specialized hardware to achieve its goal
* DSPs for audio/video processing
* On-chip/off-chip peripherals (ADCs/DACs for data acquisition, audio playback, capacitive touch)
* Displays, buttons for user interfaces

</v-click>

<v-click>


## It is much more tightly coupled to hardware than PC/server software
* This allows for smaller binaries but the trade-off is less portable code 
* It must be designed in parallel with the hardware

</v-click>

---

# Hardware Programming & Debugging Devices

<div grid="~ cols-2 gap-20">
<div>

Software tools + hardware tools:
- IDE
- compiler
- programming device/ debugger
- hardware device

Extras:
- oscilloscope
- waveform analyzer
- power analyzer 


</div>

<img src="/img/lauterbach.png" class="w-2500">[^1]

</div>

[^1]: https://wiki.dave.eu/index.php/MITO8M-AN-001:_Advanced_multicore_debugging,_tracing,_and_energy_profiling_with_Lauterbach_TRACE32

---

# Program Flow - ARM vs AVR

<style>
    table {
        width: 100%;
        border-collapse: collapse;
        background-color: #ccd8e6;
    }
    th, td {
        border: 1px solid #000;
        padding: 8px;
        text-align: left;
    }
    th {
        background-color: #add8e6;
        font-weight: bold;
    }
    td {
        vertical-align: top;
    }
    em {
        font-weight: bold;
    }
</style>

<table>
    <thead>
        <tr>
            <th>What</th>
            <th>ARM</th>
            <th>AVR</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Program Load</td>
            <td>Using an external programmer or bootloader</td>
            <td>(same)</td>
        </tr>
        <tr>
            <td>Execution launch</td>
            <td>When the microcontroller is reset, execution starts from a preset address</td>
            <td> (same) </td>
        </tr>
        <tr>
            <td>Execution threads</td>
            <td> Supports multiple threads, multiple values for the Program Counter PC (R15) </td>
            <td> Single thread, controlled by PC (Program Counter)</td>
        </tr>
        <tr>
            <td>In/ Out interaction</td>
            <td>Memory mapped I/O</td>
            <td>Port-mapped I/O</td>
        </tr>
    </tbody>
</table>

---

# The code

## How do we program a microcontroller?

<v-click>

1. The code is compiled and a binary file containing the machine code instructions is produced.
- .UF2 / .BIN / .HEX on ARM
- .HEX on AVR

</v-click>

<v-click>

2. The binary must end up in the microcontroller's program memory (Flash) [^1]
- Using an external programmer (In-System Programmer or JTAG)
- using a bootloader 

> The bootloader takes up space in the program memory for AVR (for RPI it resides in ROM).

</v-click>

<v-click>

3. After programming, a RESET is automatically applied to the processor, and it starts execution from the start address. 
> Depending on the configuration (eg where the bootloader is written), it may not be 0.

</v-click>


[^1]: ARM microcontrollers are able to execute code from RAM

---

# In / Out

## No 
- screen :) 
- console :)

## Yes
- LEDs
- LCD
- Serial interface
- Hardware Debugger

---

# Variables

## Allocation


<div grid="~ cols-2 gap-20">
<div>

- Local variables > stack
> Be careful when using recursive functions
- Global variables > data
- Dynamic variables > heap 
> Dynamic variables require an allocator - might not be ideal on an AVR / when you are low on memory 
- Const > flash memory (program memory - written at compile time) 
> Const on AVR can also be stored on EEPROM (slow)


</div>

<img src="/img/stack.png">

</div>

---

# Memory on AVR - 328P example

<style>
    table {
        width: 100%;
        border-collapse: collapse;
        background-color: #ccd8e6;
    }
    th, td {
        border: 1px solid #000;
        padding: 8px;
        text-align: left;
    }
    th {
        background-color: #add8e6;
        font-weight: bold;
    }
    td {
        vertical-align: top;
    }
    em {
        font-weight: bold;
    }
</style>

## ATmega328P Memory Details
<table>
    <tr>
        <th>Memory Type</th>
        <th>Size</th>
        <th>Purpose</th>
    </tr>
    <tr>
        <td>Flash (ROM)</td>
        <td>32 KB</td>
        <td>Stores program instructions (non-volatile).</td>
    </tr>
    <tr>
        <td>SRAM (RAM)</td>
        <td>2 KB</td>
        <td>Stores variables, stack, heap, and registers.</td>
    </tr>
    <tr>
        <td>EEPROM</td>
        <td>1 KB</td>
        <td>Stores persistent data (non-volatile, writable).</td>
    </tr>
    <tr>
        <td>General Purpose Registers</td>
        <td>32 Bytes</td>
        <td>Fast-access CPU registers.</td>
    </tr>
    <tr>
        <td>I/O Registers</td>
        <td>64 Bytes</td>
        <td>Port-mapped peripheral control registers.</td>
    </tr>
    <tr>
        <td>Extended I/O Registers</td>
        <td>160 Bytes</td>
        <td>Memory mapped peripheral control registers.</td>
    </tr>

</table>

---

# Memory on ARM - RP2350 example - M33 based

<style>
    table {
        width: 100%;
        border-collapse: collapse;
        background-color: #ccd8e6;
    }
    th, td {
        border: 1px solid #000;
        padding: 8px;
        text-align: left;
    }
    th {
        background-color: #add8e6;
        font-weight: bold;
    }
    td {
        vertical-align: top;
    }
    em {
        font-weight: bold;
    }
</style>
## RP2350 Memory Breakdown
<table>
    <tr>
        <th>Memory Type</th>
        <th>Size</th>
        <th>Purpose</th>
    </tr>
    <tr>
        <td>XIP Flash  </td>
        <td>Up to 16 MB</td>
        <td>Stores program code (external QSPI Flash).</td>
    </tr>
    <tr>
        <td>SRAM (On-chip)</td>
        <td>520 KB</td>
        <td>Stores stack, heap, variables, and data.</td>
    </tr>
    <tr>
        <td>Boot ROM</td>
        <td>32 KB</td>
        <td>Stores bootloader, factory firmware.</td>
    </tr>
    <tr>
        <td>OTP</td>
        <td>8 KB</td>
        <td>One-time-programmable (Product id, cryptographic keys). </td>
    </tr>
    <tr>
        <td>Peripheral Space</td>
        <td>Varies</td>
        <td>Memory-mapped I/O for GPIO, UART, SPI, DMA.</td>
    </tr>
    <tr>
        <td>Registers</td>
        <td>16 + control registers</td>
        <td>General purpose + program flow + special purpose</td>
    </tr>
</table>

<br> 

> XIP = Execute in Place (without this, the code would need to be copied in RAM first)

---
layout: two-cols
---

# Let's see some code


<v-click>


```c

#include <stdio.h>
#include <stdint.h>

void printBinary(uint32_t num) {
    for (int i = 31; i >= 0; i--) {
        printf("%d", (num >> i) & 1);
        if (i % 8 == 0) printf(" ");  
    }
    printf("\n");
}

int main()
{
    uint8_t a;
    uint32_t b;

    a = 0x01;
    b = a << 24;

    printBinary(a);
    printBinary(b);

    return 0;
}

```
<br> 

</v-click>

:: right ::

<v-click>

<br> <br> 

#### &nbsp;&nbsp;What is the resulting value? 

</v-click>

<v-click>


> &nbsp;&nbsp; it depends on the compiler and on the architecture


</v-click>


<br> 

<v-click>

#### &nbsp;&nbsp; Solution

```c
b = (uint32_t) a << 24;
//b will be 00000001 00000000 00000000 00000000  
//same result on any architecture and compiler;

```

</v-click>


---

# Variables in C

```c

#include <stdio.h>

int8_t, uint8_t
int16_t, uint16_t
int32_t, uint32_t


```

<br> 

# Variables in Rust

```rust
u8, u16, u32, u64, u128
i8, i16, i32, i64, i128
usize //word size (eg - 32b for 32b processor)
isize //word size (eg - 32b for 32b processor)

//NOTES:
char // 4 bytes != u8 //UTF-8 not ASCII like in C
b"str" //ASCII string
"str" UTF-8 string

's' // char
b's' // u8
```

---

# Why Rust-lang

### The tagline of Rust is No Undefined Behavior. 

- no null reference; the Rust compiler explicitly asks developers to check
this;
- no implicit cast, even adding a u32 to a u8 must be casted;
-  safe access to shared data across threads verified at compile time;
- uses type states to move runtime checks to compile time and force
developers to check;
- clearly defined data types, unlike i8 or u128;
- safe unions, that provide a discriminant to prevent wrong interpretation
of data;
- clear code organization into crates and modules;
- backward compatibility at crate level.
