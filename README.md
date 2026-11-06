Real-Time Object Detection SoC using PYNQ-Z2
<p align="center">
  <b>Zynq-7000 | PYNQ-Z2 | AXI DMA | AXI4-Stream | YOLOv3-Tiny</b>
</p>

**Project Overview**
This project demonstrates a Real-Time Object Detection System based on a custom System-on-Chip (SoC) architecture, implemented using the PYNQ-Z2 FPGA development board featuring the Xilinx Zynq-7000 SoC.
The project integrates the ARM-based Processing System (PS) with FPGA Programmable Logic (PL) through AXI interfaces. The hardware architecture is developed using Xilinx Vivado IP Integrator, incorporating AXI DMA, AXI4-Stream Data FIFO, AXI Interconnects, Processor System Reset, and interrupt connectivity.
On the software side, Python, OpenCV, and YOLOv3-Tiny are used to capture camera frames and perform object detection, displaying bounding boxes, object labels, and confidence scores.
The project explores hardware/software integration, AXI-based data movement, FPGA SoC architecture, and computer vision applications.

**Project Highlight**
Custom Zynq-7000-based SoC architecture.
Hardware design using Xilinx Vivado IP Integrator.
ARM Cortex-A9 Processing System integration.
AXI DMA implementation with MM2S and S2MM channels.
AXI4-Stream Data FIFO integration.
AXI Interconnect-based communication.
Processor System Reset and interrupt management.
Python and OpenCV-based image processing.
YOLOv3-Tiny-based object detection.
Live camera-based object recognition.
Object bounding boxes and confidence score visualization.

**SoC Hardware Architecture**
The custom SoC architecture consists of the following major IP blocks:
1. Zynq-7000 Processing System
The Zynq-7000 Processing System integrates the ARM Cortex-A9 processor and provides communication interfaces between the Processing System and Programmable Logic.

Responsibilities:
Executes the Linux-based PYNQ environment.
Runs Python, OpenCV, and YOLOv3-Tiny.
Provides DDR memory access.
Provides AXI GP0 and HP0 interfaces.
Generates programmable logic clock and reset signals.

2. AXI Direct Memory Access (AXI DMA)
The AXI DMA controller enables data movement between DDR memory and AXI4-Stream interfaces.
It provides two primary transfer channels:
MM2S – Memory-Mapped to Stream
Reads data from DDR memory.
Converts memory-mapped transactions into AXI4-Stream data.
Transfers data towards the programmable logic.
S2MM – Stream to Memory-Mapped
Receives AXI4-Stream data.
Transfers received data into DDR memory.

3. AXI4-Stream Data FIFO
The AXI4-Stream Data FIFO provides temporary buffering for streaming data.
Its functionality includes:
Streaming data buffering.
AXI4-Stream handshaking.
Managing temporary differences in data availability.

4. AXI Interconnect
The architecture incorporates AXI Interconnect IPs to establish communication between the Zynq Processing System, DMA controller, peripheral control interfaces, and DDR memory interface.

5. Processor System Reset
The Processor System Reset IP generates synchronized reset signals for the connected AXI interfaces and peripherals.

6. XLConcat
The XLConcat IP combines individual interrupt signals into a wider interrupt bus for connectivity with the Processing System.

7. Clock and Reset Management
The Zynq Processing System provides:
FCLK_CLK0
FCLK_RESET0_N
The Processor System Reset block distributes synchronized reset signals to the connected hardware components.

Hardware Architecture Summary
IP Block
Function
processing_system7_0
Zynq-7000 Processing System
axi_dma_0
DMA data transfer
axis_data_fifo_0
AXI4-Stream buffering
axi_interconnect_0
AXI communication
ps7_0_axi_periph
Peripheral AXI interconnect
proc_sys_reset_0
Synchronized reset generation
xlconcat_0
Interrupt concatenation
Software Implementation
The software implementation uses Python and OpenCV on the ARM Processing System.

**Technology Stack**
Technology
Application
Python
Application development
OpenCV
Image processing and object detection
NumPy
Image and buffer manipulation
YOLOv3-Tiny

Object detection model
PYNQ
FPGA overlay and DMA control
Jupyter Notebook
Development and execution
Vivado
SoC hardware development
Object Detection Pipeline

**The software pipeline consists of the following steps:**
1. Camera Capture
A USB camera captures live image frames at 640 × 480 resolution.

2. Image Enhancement
CLAHE (Contrast Limited Adaptive Histogram Equalization) is applied in LAB colour space to improve image contrast.

3. DMA Data Transfer Demonstration
The image is resized to 64 × 64 pixels and converted into grayscale.
The resulting 4,096-byte buffer is transferred using the AXI DMA send and receive channels.

4. YOLOv3-Tiny Inference
The enhanced camera frame is passed to the YOLOv3-Tiny model using OpenCV DNN with a 416 × 416 model input.

5. Detection and Post-processing
The system performs:
Object classification.
Confidence thresholding.
Non-Maximum Suppression (NMS).
Bounding box generation.
Detection label visualization.

6. Output Generation
The system displays detection statistics and saves the processed output image as latest_detection.jpg.
Demonstration Results
The system has been demonstrated in a laboratory environment with live camera input.

**Detected object categories include:**
Person
Laptop
Chair
Cup
Clock

**The output displays:**
Bounding boxes around detected objects.
Predicted object labels.
Detection confidence scores.
Frame counter.
Number of detected objects.

**Project Demonstration**

A video demonstration of the project is available here:

YouTube: [https://www.youtube.com/watch?v=7rbutfGcCGg](url)
