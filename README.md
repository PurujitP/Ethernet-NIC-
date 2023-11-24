# Ethernet-NIC-
To design a ethernet nic card and its peripherals and implementing it on FPGA. Thereby simulating a client-server based system and verifying using PING command.

Certainly! I've reformatted the content without removing any portions from the original:

---

# Ethernet NIC (Network Interface Card) Implementation on FPGA

## Table of Contents

1. **Introduction**
    - 1.1 [What is a Network Interface Card (NIC)?](#11-what-is-a-network-interface-card-nic)
    - 1.2 [Working of a Network Interface Card](#12-working-of-a-network-interface-card)
2. **Types of Network Interface Cards**
3. **Ethernet**
    - 3.1 [What is Ethernet?](#31-what-is-ethernet)
    - 3.2 [Why is Ethernet Used?](#32-why-is-ethernet-used)
    - 3.3 [Merits and Demerits of Ethernet](#33-merits-and-demerits-of-ethernet)
4. **Working of Ethernet**
    - 4.1 [Ethernet Follows a Simple Set of Rules](#41-ethernet-follows-a-simple-set-of-rules)
    - 4.2 [The OSI Reference Model](#42-the-osi-reference-model)
    - 4.3 [TCP/IP Reference Model](#43-tcpip-reference-model)
    - 4.4 [Lightweight IP (lwIP)](#44-lightweight-ip-lwip)
5. **Design Phase**
    - 5.1 [Introduction](#51-introduction)
    - 5.2 [Construction of the NIC Card](#52-construction-of-the-nic-card)
    - 5.3 [Implementation](#53-implementation)
        - 5.3.1 [Hardware Design](#531-hardware-design)
        - 5.3.2 [Software Design](#532-software-design)
    - 5.4 [What is JTAG?](#54-what-is-jtag)
    - 5.5 [What is Cross Compilation?](#55-what-is-cross-compilation)
    - 5.6 [Design Procedure](#56-design-procedure)
    - 5.7 [Testing and Results](#57-testing-and-results)
    - 5.8 [What is IP Core?](#58-what-is-ip-core)
6. **Conclusion**
7. **References**

## 1. Introduction

### 1.1 What is a Network Interface Card (NIC)?

A Network Interface Card (NIC) is a hardware component, typically a circuit board or chip, installed on a computer to connect it to a network. NICs provide functionality such as I/O interrupt support, direct memory access (DMA) interfaces, data transmission, network traffic engineering, and partitioning.

### 1.2 Working of a Network Interface Card

The NIC uses the OSI model to send signals at the physical layer, transmit data packets at the network layer, and operate as an interface at the TCP/IP layer.

<img width="290" alt="osi" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/1c00a989-09e8-4b6a-8369-b7ac2f9ae686">

## 2. Types of Network Interface Cards

While the standard NIC is a plastic circuit board that slides into a computer to connect with the motherboard, there are multiple ways this connection can occur:

- Wireless NICs: Provide wireless reception through radio frequency waves.
- Wired NICs: Have input jacks for cables, with Ethernet being a popular wired LAN technology.
- USB NICs: Provide network connections through a device plugged into the USB port.
- Fibre Optics NICs: Expensive and complex NICs used for high-speed support in server computers.

## 3. Ethernet

### 3.1 What is Ethernet?

Ethernet is a communication protocol created in 1973 that connects computers on a network over a wired connection. It is widely used for Local Area Networks (LANs) and Wide Area Networks (WANs).

<img width="450" alt="eth" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/579d1e99-1784-42c5-b40d-165a6eee9b1a">

### 3.2 Why is Ethernet Used?

Ethernet is still a common form of network connection used for its high speed, security, and reliability. It is employed in local networks, school campuses, hospitals, company offices, etc. Ethernet's low price contributed to its popularity compared to technologies like IBM's Token Ring.

### 3.3 Merits and Demerits of Ethernet

Ethernet offers advantages such as high speed, reliability, and backward compatibility. It is fully backward compatible, providing consistent speed and reliability through cables. However, it requires wiring each room for Ethernet connectivity, limiting movement, and making troubleshooting complex if issues arise.

## 4. Working of Ethernet

### 4.1 Ethernet Follows a Simple Set of Rules

Ethernet follows a set of rules governing its basic operation. It uses the OSI model, with frames analogous to sentences in human language. Frames have explicit minimum and maximum lengths, destination and source addresses, and must follow specific rules for construction.

### 4.2 The OSI Reference Model

The OSI Reference Model is essential for understanding Ethernet and serves as a universal language for computer networking. It divides communication into seven abstract layers, each stacked upon the last.

<img width="380" alt="layer" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/6b948efc-e425-49c6-8922-1373598c6d27">

### 4.3 TCP/IP Reference Model

The TCP/IP Model allows communication over large distances, offering a layered server architecture system. It complements the OSI Model and is crucial for real-time control.

<img width="420" alt="tcip" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/9c5b8814-239a-4b09-82e8-0d8f04bc72dc">

TCP VS OSI Model

<img width="420" alt="ositcp" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/1339b400-427a-4b12-bf3f-d5cc970dd52c">

### 4.4 Lightweight IP (lwIP)

lwIP is a small implementation of the TCP/IP protocol suite, designed to reduce resource usage while providing a full-scale TCP. It is suitable for embedded systems with limited RAM and code ROM.

## 5. Design Phase

### 5.1 Introduction

The implementation platform chosen is a development board with a Virtex-5 FPGA, specifically the ML507. Using the Xilinx Platform Studio (XPS) tool, the embedded PowerPC 440 processor is configured inside the Virtex-5 FPGA for designing the NIC card.

<img width="600" alt="ml507" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/da85c4aa-708e-47eb-91dd-0ffb9acc2c1b">
                                 
                          Xilinx ML-507 Evaluation Board

### 5.2 Construction of the NIC Card

The NIC card construction involves various modules connected to the PowerPC (processor) on the FPGA. It includes components like memory chips,RS232, Ethernet MAC, and a DDR_SDRAM memory device.

<img width="450" alt="myfig" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/d44faced-f309-48fd-b885-2b05bd2b7725">

### 5.3 Implementation

#### 5.3.1 Hardware Design

Hardware design components include PowerPC 440, Block RAM, interrupt controller, RS232, Ethernet MAC, and a DDR_SDRAM memory device.

#### 5.3.2 Software Design

Software design is configured using the Software Development Kit (SDK), and a C-program is written for the server that works on TCP data.

### 5.4 What is JTAG?

Joint Test Action Group (JTAG) is a standard interface and protocol used between a PC and a device (like an FPGA) for testing, programming, and debugging.

### 5.5 What is Cross Compilation?

Cross compilation is the process of compiling code on one platform and running it on a different platform. It is often used in embedded systems development.

### 5.6 Design Procedure

The design procedure involves configuring the PowerPC, connecting modules, implementing hardware and software designs, and testing the system.

Absolutely, here's the information with image mentions using the provided links:

1. **Opening XPS Platform Studio and Naming the Project**
   - After opening the XPS Platform Studio using the BSB wizard, the project is named in the directory where it is created.
   - The project is stored along with the selection of the PLB system.
<img width="500" alt="pic1" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/c5501a54-e1ff-4439-8a1b-e1517906a60a">

2. **Creating a New Design**
   - If the user has a midway completed project or a project with changes needed, they can import the .BSB file to work on it.
<img width="475" alt="pic2" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/21cb1cf6-d71a-4456-9a80-59de05d786fd">



4. **Selected Development Board Display**
   - The selected development board is displayed, and if it is a standard board, its specifications are automatically uploaded and fixed.
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/7bc36f98-997b-4fc8-aaf4-24f28eedc44f">

5. **System Configuration Window**
   - Here, the user decides whether it is a single or dual processor system.
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/f71481c3-68a9-4ac7-a7af-797cce7ed3ea">

6. **Processor Configuration Window**
   - In this window, the user decides the clock of the processor and bus. It is crucial to ensure the bus and processor run on the same clock.
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/08b82aef-e9c3-4350-8600-a6e01a645b8e">

7. **Peripheral Configuration Window**
   - This window is used to specify which inbuilt modules are to be used and remove unnecessary ones.
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/77380728-fe60-4a07-ab90-869bd4297a6d">

8. **Cache Configuration Window**
   - Since the project does not require the use of cache, it is disabled. The system uses a Harvard architecture.
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/d567e273-327a-413e-b960-34fbf2aa8f03">

9. **Project Generation with BSB Wizard**
   - Click the Finish button to finish generating the project. If something is missed or any peripheral needs to be added, it can be done by right-clicking a section in the description box and then clicking add.                                                     
<img width="475" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/e0167aa9-02cc-48bc-b76a-4ff547f4f54c">

10. **System Assembly View**
   - In this view, the user can see the list of components                                                                                                                            
<img width="525" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/ddf116b7-658b-4fd8-8629-657b4bd5ea3d">

11. **Addressing for the Peripherals/Modules**
    - This section displays the addressing used by each of the components. Users can lock the addresses.                                                                             
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/5196b1a7-786a-4903-95dd-7dfa519f9205">

12. **Port Declaration for the Peripherals/Modules**
    - Here, users can see which components use which ports.                                                                                                                                                  
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/42d7f829-741e-4cb2-8371-b70d33b4a253">

13. **Bus Interfaces for the Peripherals/Modules**
    - This section illustrates how each component is connected to the PLB bus system.                                                                                                                                       
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/054829e4-fbf1-4919-b709-ff5f7a7dbf29">                                                                                                                                  
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/130c1085-4b2e-47c3-9441-0c0e6e579ec4">

14. **Implementing the Design**
    - After generating the project using the BSB wizard, the design is implemented in the "Implement Flow" section by running it through "Generate Netlist," "Generate Bitstream," and then exporting the design into SDK to create the software.

15. **Hardware Platform Specifications in SDK Window**
    - After uploading the project to SDK, users can see hardware platform specifications.
 <img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/7bbc7d06-aa04-4bed-96ee-d6b5f2a0ace2">

16. **New Application Project Creation Window**
    - Users can create a new application project, selecting the language (C or C++).
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/7b104c9a-59e4-45f1-8f45-5cd49edfab0c">

17. **Template Selection - lwIP Echo Server**
    - In the template selection, the lwIP Echo server is chosen.                                                                                                                                            
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/130c1085-4b2e-47c3-9441-0c0e6e579ec4">

18. **Generating Linker Script**
    - Users can generate the linker script to view the address and size allocated for memory components. They can also increase the heap and stack size if needed.                                                            
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/6ebc2fa1-b2b2-4937-984b-f81d19c5b2de">
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/75efecb2-251e-4b56-814d-840fd85792bd">
    

18. **Including lwIP Library in Boards Manager**
    - Users need to include the lwIP library in the Boards Manager to avoid errors during compilation.
<img width="625" alt="pic3" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/656d654d-4ecc-46b8-8658-74a44adba8ef">

### 5.7 Testing and Results

Following the outlined design procedure and utilizing the JTAG for boundary scan through the Impact tool, the implementation of Ethernet on the FPGA has been successfully executed. The testing phase involves using the "ping" command to validate IP-level connectivity between the FPGA and a computer.

#### Ping Command for Verification

The "ping" command is employed to verify IP-level connectivity to another TCP/IP computer. This is achieved by sending Internet Control Message Protocol (ICMP) echo Request messages, and the corresponding echo Reply messages are received and displayed, along with round-trip times. The "ping" command serves as a primary TCP/IP tool for troubleshooting connectivity, reachability, and name resolution. When used without parameters, the command displays Help content.

The request is initiated from the PC and sent to the FPGA through an Ethernet cable. The FPGA responds back with the information, which is displayed in the command line. This establishes a successful server-client system between the FPGA and a computer via Ethernet.

#### Results Overview

- **Screenshot 1**
<img width="500" alt="pic21" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/e8c9d96a-1f70-4455-9464-cc45cb00e54a">

- **Screenshot 2**
<img width="500" alt="pic21" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/f61c83ba-f560-440c-bbf7-f65344e86896">

In these screenshots, the configuration of the lwIP TCP Echo server is visible, along with the responses from the FPGA board to the continuous "ping" commands. The information is displayed as long as the connection remains intact.

#### Cable Disconnection and Reconnection

- **Screenshot 3**
<img width="500" alt="pic21" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/401f98e1-e865-4d56-8d44-b1d240a9b4a4">

- **Screenshot 4**
<img width="500" alt="pic21" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/00ddc434-fa0e-46e2-b8ff-b77c6a928426">

These screenshots illustrate the behavior when the Ethernet cable is disconnected. When the connection is disrupted, a "General Failure" message is displayed. Upon reconnecting the cable, the information is promptly restored, indicating the resumption of connectivity.

#### Connection Status Monitoring

- **Screenshot 5**
<img width="500" alt="pic21" src="https://github.com/PurujitP/Ethernet-NIC-/assets/78445072/8521cc73-efd7-4a6a-9d72-824dae256238">

This screenshot shows the continuous monitoring of the connection status. The information reflects the dynamic nature of the connection, instantly responding to cable disconnection and reconnection events.



### 5.8 What is IP Core?

An Intellectual Property (IP) Core is a reusable unit of logic, cell, or chip layout design that can be easily integrated into a larger design.

## 6. Conclusion

The objective of implementing Ethernet NIC communication on FPGA was successfully achieved. The tools used include Xilinx tools (XPS, SDK, IMPACT) and Tera Term. The project successfully establishes a server-client system between the ML507 development board and a PC via Ethernet.

## 7. References

- www.xilinx.com
- "The Design Warrior's Guide to FPGAs" - Book by Clive Maxfield
- www.google.in
- researchgate.net/publication/350483427_What_You_Need_to_Know_About_Smart_Network_Interface_Cards
- geeksforgeeks.org/what-is-cross-compiler/
- [www.mouser.in/blog/three-things-you-should-know-about-ethernet-phy](www.mouser.in/blog/three-things-you-should-know-about-ethernet-phy)
- www.wikipedia.com

---

Feel free to use this formatted content for your README file.
