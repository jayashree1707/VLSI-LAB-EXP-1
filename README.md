# 212222060091
 exp.no:1 simulation and implentation of logic gates,adder and subtractor using vivado
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using vivado.

APPARATUS REQUIRED: vivado 2023.2

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)
verilog code for logic gates:
```
module logic(a,b,g1,g2,g3,g4,g5,g6,g7);
input a,b;
output g1,g2,g3,g4,g5,g6,g7;
assign g1=a&b;
assign g2=a|b;
assign g3=~(a&b);
assign g4=~(a|b);
assign g5=a^b;
assign g6=~a;
assign g7=~(a^b);
endmodule
```
output:
![logic gate1](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/31b9493e-4ea5-4536-8465-cbd451482b9b)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)
verilog code for half adder:
```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule
```
output:

![halfadder1](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/1f5ed4b6-126c-4600-9157-423cfbe85971)

Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)
verilog code for full adder:
```
module fulladder(a,b,c,s,cout);
input a,b,c;
output s,cout;
wire w1,w2,w3;
xor (w1,a,b);
xor(s,w1,c);
and(w2,a,b);
and(w3,b,c);
or(cout,w2,w3);
endmodule
```
output:
![fulladder](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/3a1dd7d0-bae9-40c0-9fb3-d54e6e001dc6)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)
verilog code for half subtractor:
```
module halfsubractor(a,b,D,B);
input a,b;
output D,B;
assign D=a^b;
assign B=~a&b;
endmodule
```
output:

![half subtractor](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/3c2f7ad4-114a-4dbe-80fc-d6c59a3b3bfe)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
verilog code for full subtractor:
```
module fullsubtractor(a,b,bin,d,out);
input a,b,bin;
output d,out;
assign d=a^b^bin;
assign out=(~a&b)|((~a^b)&bin);
endmodule
```
output:
![full subtractor](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/b3753b37-d259-4dd3-987b-bec40abde39a)


8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)
verilog code for 8-bit ripple carry adder:
```
module fulladder(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire [3:1]w;
xor g1(w[1],a,b);
xor g2(sum,w[1],c);
and g3(w[2],a,b);
and g4(w[3],w[1],c);
or g5(carry,w[3],w[2])
endmodule
module ripple_8adder(
    input [7:0] a,
    input [7:0] b,
    input cin,
    output [7:0] sum,
    output carry );
    wire [6:0]c;
fulladder FA1(a[0],b[0],cin,sum[0],c[0]);
fulladder FA2(a[1],b[1],c[0],sum[1],c[1]);
fulladder FA3(a[2],b[2],c[1],sum[2],c[2]);
fulladder FA4(a[3],b[3],c[2],sum[3],c[3]);
fulladder FA5(a[4],b[4],c[3],sum[4],c[4]);
fulladder FA6(a[5],b[5],c[4],sum[5],c[5]);
fulladder FA7(a[6],b[6],c[5],sum[6],c[6]);
fulladder FA8(a[7],b[7],c[6],sum[7],carry);
endmodule
```
output:
![rca in binary](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/34df6a45-a920-4405-9d01-94c5703b7094)



RESULT:
  Thus ,the given simulation and implementation of  logic gates, adder, subtractor are  simulated and synthesis are executed successfully .
