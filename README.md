# Traffic Light Controller Using VLDH
* The purpose of this project is to design a methodology using Verilog to control the traffic with specified time delays for a T-Shaped road.*

# Table of Contents

1. [Overview](Overview)
# Overview
This project demonstrates the development of a traffic light controller implemented on an FPGA (e.g., Xilinx Spartan series) with priority override for emergency vehicles. The design employs Hardware Description Languages (Verilog or VHDL) and is verified through simulation using tools such as ModelSim or Vivado.

# Functional Description
## Modes of Operation
### Normal Mode: Standard timing-based traffic light cycles (Red, Yellow, Green) utilizing a finite state machine (FSM).

### Priority Mode: Adaptively allocates more green time to approaches with higher vehicle density, based on sensor input.

### Emergency Override: When an emergency vehicle is detected, the system overrides all other cycles, granting a green signal on the relevant path and holding other signals at red.

## System Architecture
### Component	            Description
FPGA Board	            Xilinx Spartan series (or similar, e.g., Spartan-3E, Spartan-6)
Programming Language	Verilog HDL (or VHDL)
Sensors             	IR, RFID, or manual button input for vehicle presence/emergency detection
Outputs	                LEDs for red/yellow/green signals; optional 7-segment displays for timers
Simulation	            ModelSim or Vivado used for functional verification and waveform analysis
## Design Implementation
1. FSM (Finite State Machine) Design
Each traffic signal phase is represented as a state.

Transitions are governed by timing intervals and sensor inputs (for density and emergency detection).

Additional ‘emergency’ state overrides standard logic for priority passage.

# 2. Emergency Vehicle Priority Logic
Detection mechanism: IR, RFID, audio, or manual emergency button.

On detection, controller immediately grants green to the emergency direction.

Other directions hold red until emergency passage confirmed; then the FSM resumes normal operation.
## Control Algorithm Pseudocode:
```
 if(emergency_detected)
   state <= EMERGENCY_GREEN; // override cycle
else if(high_density_lane)
   state <= PRIORITY_GREEN;  // allocate more green time
else 
   state <= NORMAL_CYCLE;
```
# 3. Input/Output Mapping
Inputs: Clocks, reset, sensors (density, emergency).

Outputs: LEDs for each light, signals to display boards.

# 4. Deployment Flow
Coding: Write FSM and priority logic in Verilog (or VHDL).

Simulation: Develop testbench and simulate in ModelSim/Vivado.

Synthesis/Implementation: Generate bitstream for Xilinx Spartan, program FPGA.

Testing: Use buttons/sensors as input, LEDs as output.

## Verilog Code Example Snippet
Below is a simplified snippet of FSM state logic with emergency override:
```
always @(posedge clk or posedge reset) begin
  if (reset) state <= RED;
  else case(state)
    RED:     state <= (emergency) ? EMERGENCY_GREEN : GREEN;
    GREEN:   state <= YELLOW;
    YELLOW:  state <= RED;
    EMERGENCY_GREEN: state <= (emergency) ? EMERGENCY_GREEN : RED;
    default: state <= RED;
  endcase
end
```


## Simulation and Testing
Create a Verilog or VHDL testbench modeling normal and emergency scenarios.

Use ModelSim or Vivado simulation for waveform analysis and verification.

Validate by observing signal transitions – on emergency input, green is immediately assigned to the required lane.

## Implementation Notes
FPGA Board: Ensure correct mapping of LEDs and input switches on the chosen Spartan model.

Flexibility: FSM can be easily modified to add more complex urban intersection logic or handle multiple emergency scenarios.

Scalability: Design allows for future extension (VIP cars, buses, integration with smart city IoT infrastructure).

## References
The system architecture and emergency priority logic have been demonstrated in research using both Xilinx Spartan FPGAs and alternative platforms, with tested Verilog implementations.

## Key Points:

Priority system: Emergency vehicles are granted green lights with highest priority.

HDL design: FSM-based traffic light logic, coded in Verilog/VHDL.

FPGA implementation: Deployable on common educational/hobbyist FPGAs like Xilinx Spartan.

Simulation ready: Testable in ModelSim or Vivado with standard HDL testbench methodology.



# 5. Logic Diagram
<img width="1536" height="1024" alt="Logic_Diagram" src="https://github.com/user-attachments/assets/66d68f3b-636c-4bb8-988e-3504419d4c22" />


# 6. State Table
<img width="1145" height="943" alt="State Table" src="https://github.com/user-attachments/assets/9907cf94-7414-4ad3-aa9c-ec59336c2909" />


# 7. State Direction & Direction Asssignment 
<img width="450" height="710" alt="Stata Direction" src="https://github.com/user-attachments/assets/32f070b6-e622-43ae-a196-3d62ffb39dd2" />
<img width="1152" height="395" alt="Direction Assignment" src="https://github.com/user-attachments/assets/96d41466-5d6f-4075-a1da-8cb610d4c475" />


# 8. State Diagram
<img width="1024" height="1024" alt="State_Diagram" src="https://github.com/user-attachments/assets/94d48d00-b194-47e6-943f-9028b47dcb44" />

# 9. Simulation Result
[Simulation Results .pdf](https://github.com/user-attachments/files/21343772/Simulation.Results.pdf)
