![logic gate1](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/f0bb6689-5b1d-46cf-9066-51abc84980b3)# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)
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
![logic gate1](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/5768437b-b9e7-4b4b-800a-035e64b7b4f7)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)
```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule
```
![halfadder1](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/65689087-d9cf-47ad-8fe3-df515448034d)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)
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
![fulladder](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/343aa57a-2431-4aac-aee1-fae300cb60bb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)
```
module halfsubractor(a,b,D,B);
input a,b;
output D,B;
assign D=a^b;
assign B=~a&b;
endmodule
```
![half subtractor](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/664b8e18-9d5c-425a-a9ce-ef281fa3af6d)


Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)
```
module fullsubtractor(a,b,bin,d,out);
input a,b,bin;
output d,out;
assign d=a^b^bin;
assign out=(~a&b)|((~a^b)&bin);
endmodule
```
![full subtractor](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/649369dc-0364-467a-99fc-52f73b0b6cbb)


8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)
```
module rca(a,b,c,sum,cout) ;
 input a,b,c;
 output sum,cout;
 wire w1,w2,w3;
 xor g1(w1,a,b);
 xor g2(sum,w1,c);
 and g3(w2,a,b);
 and g4(w3,w1,c);
 or g5(cout,w3,w2);
 endmodule
 module rca1(a,b,cin,sum,cout);
 input [7:0]a,b;
 input cin;
 output [7:0]sum;
 output cout;
 wire w1,w2,w3;
 rca RC1(a[0],b[0],cin,sum[0],w1);
 rca RC2(a[1],b[1],w1,sum[1],w2);
 rca RC3(a[2],b[2],w2,sum[2],w3);
 rca RC4(a[3],b[3],w3,sum[3],w4);
 rca RC5(a[4],b[4],w4,sum[4],w5);
 rca RC6(a[5],b[5],w5,sum[5],w6);
 rca RC7(a[6],b[6],w6,sum[6],w7);
 rca RC8(a[7],b[7],w7,sum[7],cout);
 endmodule
```
![rca in binary](https://github.com/navaneethans/VLSI-LAB-EXP-1/assets/160314881/10cab355-1436-4b69-9eeb-a62fce177385)


VERILOG CODE:



OUTPUT:




RESULT:

