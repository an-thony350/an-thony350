<div align="center">

# Anthony Bartlett

### FPGA · RTL · Low-Latency Systems

**MEng Electronic & Information Engineering**
Imperial College London · Class of 2028

![Focus](https://img.shields.io/badge/FOCUS-low--latency%20FPGA-2f81f7?style=for-the-badge\&labelColor=0d1117)
![RTL](https://img.shields.io/badge/RTL-SystemVerilog-a371f7?style=for-the-badge\&labelColor=0d1117)
![Target](https://img.shields.io/badge/TARGET-hardware%20for%20HFT-3fb950?style=for-the-badge\&labelColor=0d1117)

</div>

---

```text
market data ──► framing ──► protocol decoding ──► stateful RTL ──► decisions
```

```text
pixels ──► fixed-point compute ──► parallel cores ──► framebuffer ──► HDMI
```

I design FPGA systems that sit at the intersection of **digital architecture, high-throughput data processing and hardware/software integration**.

My work spans reference modelling, RTL implementation, verification, timing closure and deployment on physical FPGA hardware. I am particularly interested in systems where latency, determinism and throughput matter.

> A fast datapath is only useful when its interfaces, verification and measurements are credible.

---

## `01` Market data in hardware

### [ITCH Feed Handler and FPGA Order Book](https://github.com/an-thony350/ITCH-Feed-Handler-and-Order-Book)

A hardware pipeline that turns encapsulated market-data frames into a maintained limit-order book:

```text
Ethernet II
    └── IPv4
         └── UDP
              └── MoldUDP64
                   └── Nasdaq ITCH
                        └── FPGA order book
                             └── Best bid / offer
```

**Engineering highlights**

* Complete simulated network-to-book path
* Ethernet, IPv4, UDP and MoldUDP64 parsing
* ITCH message realignment and decoding
* Stateful order-reference and price-level storage
* Duplicate, stale and sequence-gap handling
* Python golden models and layered cocotb verification
* Routed on a Zynq-7020 at **106.667 MHz**
* Timing clean with **+0.020 ns WNS**

This is my main ongoing project and the closest representation of the low-latency FPGA work I want to pursue professionally.

**[Explore the architecture and RTL →](https://github.com/an-thony350/ITCH-Feed-Handler-and-Order-Book)**

---

## `02` Parallel compute and real-time graphics

### [FractalScope](https://github.com/an-thony350/FractalScope)

An interactive **1280 × 720 FPGA fractal renderer** built on the PYNQ-Z1.

Rather than calculating pixels sequentially in software, FractalScope distributes fixed-point fractal jobs across a parallel RTL compute array and writes completed pixels directly into a DDR framebuffer.

```text
view parameters
      │
      ▼
tile scheduler ──► 23 iteration cores ──► colour pipeline
                                              │
                                              ▼
                                      AXI framebuffer writer
                                              │
                                              ▼
                                         DDR ──► HDMI
```

**Engineering highlights**

* **23 parallel iteration cores**
* Signed **Q4.22 fixed-point arithmetic**
* Mandelbrot, Julia, Burning Ship and Tricorn rendering
* Progressive rendering and tile-based scheduling
* Mariani–Silver-style uniform-region skipping
* Out-of-order completion with indexed framebuffer writes
* AXI4, AXI-Lite, VDMA and HDMI integration
* Python/PYNQ application, controller and UI layer

**[See the complete FPGA system →](https://github.com/an-thony350/FractalScope)**

---

## `03` Arithmetic acceleration

### [FPGA-Accelerated Online Linear Regression](https://github.com/an-thony350/FPGA-Accelerated-Online-Linear-Regression)

A parallel RTL multiply-accumulate architecture for updating the normal-equation matrices used by an online linear-regression model.

The accelerator packs an entire feature sample into a wide input word, performs many feature-product operations concurrently and maintains 64-bit running accumulators in hardware.

**Measured results**

* Approximately **3.49 ms** hardware accumulation
* Approximately **30.4 ms** optimised software batch
* **18.24× average** multiplication-latency improvement
* **68.19× maximum** measured improvement
* **170 DSP48s** used on the Zynq-7020
* Timing estimate of **5.84 ns** against an **8 ns** target

The wider team system applied this accelerator to streaming cryptocurrency market data.

**[Read my hardware dossier →](https://github.com/an-thony350/FPGA-Accelerated-Online-Linear-Regression)**
**[View the complete team project →](https://github.com/derza-essien/Accelerated-HFT-System)**

---

## More systems work

### [RV32IM Processor](https://github.com/an-thony350/RV32IM-Processor)

Five-stage pipelined RISC-V processor with forwarding, hazard detection, cache integration, multiplication instructions and dynamic branch prediction.

### [C90 Compiler](https://github.com/an-thony350/C90-Compiler)

C++ compiler pipeline covering preprocessing, lexing, parsing, AST construction and RISC-V assembly generation.

### [SystemVerilog RTL Exercises](https://github.com/an-thony350/systemverilog-coding-problems)

A growing collection of independently implemented RTL exercises covering combinational logic, sequential design, FSMs, arithmetic structures, FIFOs and parameterised hardware.

---

## Current focus

```text
[1] Increasing market-data ingress throughput
[2] Measuring end-to-end FPGA latency accurately
[3] Timing-driven RTL optimisation
[4] Robust SystemVerilog and cocotb verification
[5] Direct-Ethernet FPGA architectures
```

---

## Working toolkit

`SystemVerilog` · `Python` · `C++` · `C` · `RISC-V Assembly`

`Vivado` · `PYNQ` · `Cocotb` · `Verilator` · `GTKWave`

`AXI4` · `AXI4-Stream` · `AXI DMA` · `BRAM` · `Fixed-Point Arithmetic`

`RTL Architecture` · `Pipelining` · `Protocol Processing` · `Golden Models`

---

<div align="center">

### Building towards FPGA and low-latency hardware engineering roles

Open to **FPGA, RTL and hardware-acceleration opportunities for 2027**.

</div>
