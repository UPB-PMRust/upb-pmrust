---
theme: seriph
# background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: true
info: |
  ## Memory Mapped IO for GPIO
drawings:
  persist: false
defaults:
  foo: true
transition: slide-left
title: MA - 02 - Memory Mapped IO
mdc: true
layout: cover
themeConfig:
  primary: '#0060df'
download: true
exportFilename: pm_cc-02
background:
---

# Memory Mapped IO used for GPIO
Lecture 2

---
---

# GPIO for RP2040

- Memory Mapped I/O
  - GPIO Peripheral
- Embedded Rust Stack
- embassy-rs

<!-- Bitwise -->

---
src: ../../resources/bitwise/slides.md
---

---
src: ../../resources/bitwise/c_bit.md
---


<!-- MMIO -->

---
src: ../../resources/mmio/slides.md
---

<!-- bitwise -->

---
src: ../../resources/bitwise/rust.md
---

---
src: ../../resources/bitwise/c.md
---

<!-- general obs on GPIO -->
---
src: ../../resources/sio/gpio_intro.md
---

<!-- AVR GPIO with C -->


---
src: ../../resources/sio/gpio_avr.md
---


<!-- SIO -->

---
src: ../../resources/sio/slides.md
---

<!-- rust-embedded -->

---
src: ../../resources/rust-embedded/slides.md
---

<!-- embassy-rs -->

---
src: ../../resources/embassy-rs/slides.md
---


<!-- embassy-rs -->

;---
;src: ../../resources/signals/digital_v2.md

;---

---
src: ../../resources/signals/basic.md
---

---
src: ../../resources/signals/extra.md
---

---
# Conclusion
we talked about

- Memory Mapped IO
- RP2040 GPIO
  - Single Cycle IO
  - IO Bank
  - Pad
- The Rust embedded standard stack
- Bare metal Rust
- The embassy-rs framework
