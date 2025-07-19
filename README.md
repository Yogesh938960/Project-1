# RraFFic Light Controller using Verilog
The purpose of this project is to design a methodology using Verilog to control the traffic with specified time delays for a T-Shaped road.*

## Table of Contents
 1. Introduction
 2. Methodology
      Directiond Considered
      Problem Statement
      State Diagram
      State Table
3. RLT Code
4. Testbench
5. Output Waveforms
6. Result
7. Future Work
8. References
9. Author

    # Introduction
   Traffic control is a challenging problem in many cities. This is due to the large number of vehicles and the high dynamics of the traffic system. Poor traffic systems are the big reason for accidents, time losses. In this method of approach, it will reduce the waiting time of the vehicles at traffic signals. The hardware design has been developed using Verilog Hardware Description Language (HDL) programming.

Verilog designing is hardware descriptive language, the name itself suggest that it deals with the hardware designing and simulation. Basically, it becomes very difficult to mount the various electronic components on breadboard or PCB circuit. It also takes too much time for the simulation and sometimes many errors occur because of improper connection of components onto the circuit. And thus, to overcome this factor hardware descriptive language comes into conclusion. we can code the process using Verilog and we can mount it on a circuit or just upload it to the circuit accordingly so that particular circuit will work as according to the code we have written.

HDL language is often used for sequential circuits like shift register, combinational logic circuit like adder, subtractor etc. Basically it describes the digital systems like microprocessor or a memory. Whatever design that is described in HDL are independent, it has its unique state of work, very much easy to simulate, designing and debugging, and very useful than schematics, especially for large circuits thus, to overcome difficulties or problems to design the circuits manually with breadboard and PCB, use of Verilog designing in this complex world is increasing a way better.

This project deals with a basic design of a T - Shaped road for traffic light control. The output of system has been tested using Xilinx 14.5.

A traffic light system is an electronic device that assigns right of way at an intersection or crossing or street crossing by means of displaying the standard red, yellow and green colored indications. In addition, it also works in conjunction with pedestrian displays to assign pedestrian crossing right of way.

A traffic light, also known as traffic signal, stop light, stop-and-go lights, is a signaling device positioned at a road intersection, pedestrian crossing, or other location in order to indicate when it is safe to drive, ride, or walk using a universal colour code. Nowadays,

A red light meant traffic in all directions had to stop.
A yellow light meant cross-town traffic would have to slow and,
A green light would to go or proceed.
The problem of heavy jam is happened because of never configure the level of jam in each way and set the delay time. Another problem represents when there is no jam, but the waiting still continues. The solution for these problems is to determine the level of jam and set the delay time. This problem need of evaluation of the traffic policeman, and then there is need for manual control of the traffic. The target of this paper is to propose system provide solution for all above problems with least possible cost. Traffic light controller (TLC) can be implemented using microcontroller, FPGA, and ASIC design. FPGA has many advantages over microcontroller, some of these advantages are; the speed, number of input/output ports and performance which are all very important in TLC design, at the same time ASIC design is more expensive than FPGA. Nowadays, FPGA becomes one of the most successful of today’s technologies for developing the systems which require a real time operation. FPGA is a re-configurable integrated circuit that consists of two dimensional arrays of logic blocks and flip-flops with an electrically programmable interconnection between logic blocks. The reconfiguration property enables fast prototyping and updates for hardware devices even after market launch. Most of the TLCs implemented on FPGA are simple ones that have been implemented as examples of Finite State Machine (FSM).

The Verilog language has been selected for programming the FPGA to fill two important needs in the design process.
Firstly, it gives full description of the structure of a design that is how it is decomposed into sub-designs, and how those sub-designs are interconnected.
Secondly, it allows simulating the design before starting the manufacturing.
Accordingly, the designers can quickly compare alternatives and test for correctness without the delay and expense of hardware prototyping.
Benefits of Using Verilog HDL (Hardware Description Language) :
Verilog is a widely used Hardware Description Language (HDL) for designing digital circuits. It can also be used for modeling analog circuits. Verilog is a descriptive language that describes a relationship between signals in a circuit.

A Verilog model describes a unit of digital hardware in terms of :

Interconnections of other hardware unit whose models prescribe their behavior in a simulation.
Behavioral / procedural algorithms that abstractly describe input/output behavior
that could be personified in a hardware unit.
Hardware description language (HDL) is divided by two types, Verilog and VHDL (VHSIC – Very High Speed Integrated Circuit Hardware Description Language). Both have its advantages and its disadvantage. In this project, Verilog HDL was chosen because it’s used for synthesis of logic circuits (synthesizable code), used for verification purposes of a circuit (can be analog or digital or mixed signal), can be used by combining synthesis & verification (synthesizable & behavioral code) and it used for netlist representation of a synthesizable circuit (structural code).

The advantages using Verilog HDL are shown below :
Easy to write.
Easy to understand as it similar to C program.
Easier to learn compared with VHDL.

# Methodology
 ## Direction Considerd
  
  ![Derection](https://github.com/user-attachments/assets/eae92e52-bb87-432f-9c6a-1322ee507636)
  The directions, M1, MT, M2, S, that is been considered for analysis of our problem is shown in the figure. And, the problem statement is explained in the figure. Six states, S1, S2, S3, S4, S5, S6 are taken into consideration and state diagram, state table is made using the following logic explained in the figure.

## Problem Statement
![WhatsApp Image 2025-07-19 at 21 08 36_49874f64](https://github.com/user-attachments/assets/56a359cc-6022-4d73-ac8d-832fce6367ca)
Green light indicates that there is no traffic and there is easy flow of vehicles in that route/direction.
Red light indicates that there is a traffic jam and that route is blocked for the vehicles to move and,
Yellow light indicates that the route has medium flow of vehicles.
Time delays for changing from one state to another is considered as, TMG(from S1 to S2), TY(from S2 to S3), TTG(from S3 to S4), TY(from S4 to S5), TSG(from S5 to S6) and TY(from S6 to S1) and the cycle continues.

## State Diagram
![WhatsApp Image 2025-07-19 at 21 10 34_9f456001](https://github.com/user-attachments/assets/74530e8e-3161-4f7f-9427-7bdbadf7bed9)
In Figure, The time delays are considered as follows :

TMG = 7 seconds
TY = 2 seconds
TTG = 5 seconds
TSG = 3 seconds
Until TMG seconds, the signal will remain in S1 state, and after TMG seconds, it will move to S2 state. Until TY seconds it will remain in S2 state and after TY seconds, it will move to S3 state, and so on. After TY seconds, in state S6, it will go back to S1 state and the cycle continues.

![WhatsApp Image 2025-07-19 at 21 10 38_0d7f8c57](https://github.com/user-attachments/assets/f7878da9-0c32-44f9-8102-ed71d1112ec8)
In Figure,

R = RED,
Y = YELLOW and,
G = GREEN.
ST = State Transition; A, B and C are considered as the present state. The state table is made, considering the Logic diagram/problem statement given in Figure. From the Figure it is understood that,

In state S1(001);


  
