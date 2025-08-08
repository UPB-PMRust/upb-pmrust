# Microprocesors VS Microcontrollers

<br> 

# Microcontroller
A microcontroller is a small computer on a single integrated circuit (IC).

<br> 

# Microprocessor
A microprocessor is a computer central processing unit (CPU) on a single integrated circuit (IC).

---

# Comparation

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

| Characteristic | Microcontroller            | Microprocessor           |
|----------------|----------------------------|--------------------------|
| Function       | Includes CPU, mem & I/O    | Includes only the CPU    |
| Cost           | >> *cheaper*               | >> *expensive*           |
| Complexity     | >> *simple*                | >> *complex*             |
| Use case       | *Incorporated devices*     | *PCs, Servers, Laptops*  |

---

# Graphic representation

<img src="/img/vs.png" class="w-full mx-auto block">

© https://www.electronicsforu.com/resources/difference-between-microprocessor-and-microcontroller

---

# Note: why a motherboard

<img src="/img/motherboard.png" style="width: 60%; max-width: 100%; height: auto; margin: 0 auto; display: block;" alt="Motherboard">

---

# Note: von Neumann VS Harvard

From the point of view of memory access, there are 2 architectures:

von Neumann, where memory contains both instructions and data. 
> Today's PCs are all von Neumann

Harvard, where memory access is done on separate buses, one for data, one for instructions.	
> AVR, PIC, DSPs and many microcontrollers are Harvard

Note: ARM is von Neumann with some * 
Note: GPUs (NVIDIA) are mixed arhitecture

---

# Note: microcontrollers - general observations

<br> 
<i>

# Microcontroller (MCU) – a mini computer on a single silicon chip that integrates:
</i>


## &nbsp;&nbsp;&nbsp;Processor
## &nbsp;&nbsp;&nbsp;Data memory
## &nbsp;&nbsp;&nbsp;Program memory
## &nbsp;&nbsp;&nbsp;Peripherals
<br> 

> In contrast to a microprocessor that needs other external chips for memory, control, peripherals

---

# Under the microscope

<img src="/img/microscope.png" style="width: 60%; max-width: 100%; height: auto; margin: 0 auto; display: block;" alt="Motherboard">

© https://www.bunniestudios.com/blog/?page_id=40

---

# (extra)

<div style="display: flex; align-items: center; justify-content: space-between;">
    <div style="flex: 1; padding-right: 20px;">
        <p>© https://www.tomshardware.com/news/amd-shares-new-second-gen-3d-v-cache-chiplet-details-up-to-25-tbs</p>
    </div>
    <img src="/img/amd.png" style="width: 60%; max-width: 100%; height: auto;" alt="Motherboard">
</div>

---

# Types

<img src="/img/types.svg" style="width: 100%; max-width: 100%; height: auto; margin: 0 auto; display: block;" alt="Motherboard">

---

# How to choose the right one ?

## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp; Energy consumption
## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp; Operating frequency
## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp; IO Pins & Supported Peripheral / Interface Types (discussion)
## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp;Memory
## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp;Internal functions
## &nbsp;&nbsp;&nbsp;? &nbsp;&nbsp;&nbsp;Software availability & support!
