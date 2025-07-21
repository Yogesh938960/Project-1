# Traffic Light Controller Using VLDH
* The purpose of this project is to design a methodology using Verilog to control the traffic with specified time delays for a T-Shaped road.*

# Table of Contents

1. [Introduction](#Introduction)
2. [VHDL Code for Traffic Light Controller](#VHDLCodeforTrafficLightController)

## Introduction 
Traffic Light Controller interfacing with Spartan FPGA
### Traffic Light Controller
Traffic light controller consists of 12 Nos. point led arranged by 4Lanes. Each lane has Go (Green), Listen(Yellow) and Stop(Red) LED is being placed. Each LED has provided for current limiting resistor to limit the current flows to the LEDs.

Traffic Light Controller interfacing with Spartan6 FPGA kit

All the 12 LED’s interfaced with Spartan6 FPGA Development Board

through series Resister 330 ohm and another end is terminated to ground.

### Pin Description for Traffic Light Controller
Schematics to interface Traffic Light Controller with Spartan6 FPGA
Traffic Light Controller Placement in Spartan6 FPGA Development Kit



## VHDL Code for Traffic Light Controller
library IEEE;

use IEEE.STD_LOGIC_1164.ALL;

use IEEE.STD_LOGIC_ARITH.ALL;

use IEEE.STD_LOGIC_UNSIGNED.ALL;

 

entity traffic_light is

port ( clk : in std_logic;

       rst : in std_logic;

       northgreen : out std_logic;

               northred   : out std_logic;

               northyel   : out std_logic;

               southgreen : out std_logic;

               southred   : out std_logic;

               southyel   : out std_logic;

               eastgreen  : out std_logic;

               eastred    : out std_logic;

               eastyel    : out std_logic;

               westred    : out std_logic;

               westgreen  : out std_logic;

               westyel    : out std_logic);

end traffic_light;

 

architecture Behavioral of traffic_light is

type contol is (north,south,east,west);

signal control,control1 : contol := north;

begin

process(clk,rst)

variable i : integer := 0;

begin

if rst = '1' then

if clk'event and clk = '1' then

if i < 1500000000 then

i := i + 1;

elsif i = 1500000000 then

control <= control1;

i := 0;

end if;

if control = north then

if i >= 0 and i <= 750000000 then

northgreen <= '1';

northred   <= '0';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 750000000 and i <= 1000000000 then

northgreen <= '0';

northred   <= '0';

northyel   <= '1';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 1000000000 and i < 1500000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '1';

eastred    <= '0';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

 

control1 <= east;

end if;

elsif control = east then

 

if i >= 0 and i <= 750000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '1';

eastred    <= '0';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 750000000 and i <= 1000000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '0';

eastyel    <= '1';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 1000000000 and i < 1500000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '1';

southred   <= '0';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

 

 

control1 <= south;

end if;

elsif control = south then

if i >= 0 and i <= 750000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '1';

southred   <= '0';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 750000000 and i <= 1000000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '0';

southyel   <= '1';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

elsif i > 1000000000 and i < 1500000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '0';

westgreen  <= '1';

westyel    <= '0'; 

 

control1 <= west;

end if;

elsif control = west then

 

if i >= 0 and i <= 750000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '0';

westgreen  <= '1';

westyel    <= '0'; 

elsif i > 750000000 and i <= 1000000000 then

northgreen <= '0';

northred   <= '1';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '0';

westgreen  <= '0';

westyel    <= '1'; 

elsif i > 1000000000 and i < 1500000000 then

northgreen <= '1';

northred   <= '0';

northyel   <= '0';

southgreen <= '0';

southred   <= '1';

southyel   <= '0';

eastgreen  <= '0';

eastred    <= '1';

eastyel    <= '0';

westred    <= '1';

westgreen  <= '0';

westyel    <= '0'; 

 

 

control1 <= north;

end if;

end if;

end if;

end if;

end process;

end Behavioral;

## TESTBENCH

```

`timescale 1ns / 1ps
module Traffic_Light_Controller_TB;
reg clk,rst;
wire [2:0]light_M1;
wire [2:0]light_S;
wire [2:0]light_MT;
wire [2:0]light_M2;
wire [3:0] count;
wire [2:0]ps;
Traffic_Light_Controller dut(.clk(clk) , .rst(rst) , .light_M1(light_M1) , .light_S(light_S)  ,.light_M2(light_M2),.light_MT(light_MT)  );
initial
begin
    clk=1'b0;
    forever #(1000000000/2) clk=~clk;
end

initial
begin
    rst=0;
    #1000000000;
    rst=1;
    #1000000000;
    rst=0;
    #(1000000000*200);
    $finish;
end
endmodule

```



  
