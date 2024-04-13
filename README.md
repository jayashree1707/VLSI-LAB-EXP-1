JAYASHREE T (212222060091)
## SIMULATION AND IMPLEMENTATION OF LOGIC GATES, ADDER AND AUBTRACTOR
## AIM:
To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.
## APPARATUS REQUIRED:
Xilinx 14.7 Spartan6 FPGA
## PROCEDURE: 
STEP:1 Start the Xilinx navigator, Select and Name the New project.</br>
STEP:2 Select the device family, device, package and speed.</br>
STEP:3 Select new source in the New Project and select Verilog Module as the Source type. </br>
STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. </br>
STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.</br>
STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.</br>
STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.</br>
STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained.</br>
STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
</br>
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. </br>
STEP:11 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

## LOGIC DIAGRAM :
### Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)

### Half Adder:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)

### Full adder:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)

### Half Subtractor:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)

### Full Subtractor:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)

### 8 Bit Ripple Carry Adder
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)

## VERILOG CODE:

### Logic gates:
```
Module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
input a,b;
output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;
and(andgate,a,b);
or(orgate,a,b); 
xor(xorgate,a,b);
nand(nandgate,a,b);
nor(norgate,a,b);
xnor(xnorgate,a,b);
not(notgate,a);
endmodule
```
## OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/d3a3d3f6-7db8-4a7e-b0e6-43f2a22bce25)

## HALF ADDER:
### PROGRAM:
```
module ha(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule
```

### OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/9ffd8417-dcdf-4cd8-8cdf-ade79c8b2955)

## FULL ADDER:
### PROGRAM:
```
module fa(a,b,c,sum,carry); input a,b,c;
output sum,carry; wire [3:1]w;
xor g1(w[1],a,b);
xor g2(sum,w[1],c);
and g3(w[2],a,b);
and g4(w[3],w[1],c);
or g5(carry,w[3],w[2]);
endmodule
```
### OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/4ff72538-f023-4dc0-b6e2-c5ebf43b5ed6)

## HALF SUBTRACTOR:
### PROGRAM:
```
module hs(a,b,difference,borrow);
input a,b;
output difference,borrow;
assign difference=a^b;
assign borrow=~a&b;
endmodule
```

### OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/b24b987f-05de-4157-b2c5-ba0de15a8492)

## FULL SUBTRACTOR:
### PROGRAM:
```
module fullsubtractor(a,b,bin,d,out);
input a,b,bin;
output d,out;
assign d=a^b^bin;
assign out=(~a&b)|((~a^b)&bin);
endmodule
```

### OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/1c5c8a59-d61a-4460-b2bd-4a87db92c0c4)

## 8 BIT RIPLE CARRY ADDER:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/3db61863-bb31-4dc1-aee2-244c2608e8bc)

### PROGRAM:
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

### OUTPUT:

![image](https://github.com/jayashree1707/VLSI-LAB-EXP-1/assets/160314881/075ed2fd-4f30-4cdd-8cea-75d2637e70aa)

## RESULT:
Thus ,the given simulation and implementation of  logic gates, adder, subtractor are  simulated and synthesis are executed successfully .

