# VLSI-LAB-EXPERIMENTS
AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: STEP:1 Start the Xilinx navigator, Select and Name the New project. STEP:2 Select the device family, device, package and speed. STEP:3 Select new source in the New Project and select Verilog Module as the Source type. STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it. STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax. STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table. STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window. STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu. STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here. STEP:12 Load the Bit file into the SPARTAN 6 FPGA STEP:11 On the board, by giving required input, the LEDs starts to glow light, indicating the output.

Logic Diagram :

Logic Gates:
![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/ee17970c-3ac9-4603-881b-88e2825f41a4)


Half Adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/0e1ecb96-0c25-4556-832b-aeeedfdfe7b9)


Full adder:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/9bb3964c-438f-469d-a3de-c1cca6f323fb)


Half Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/731470b7-eb4e-49f8-8bb7-2994052a7184)



Full Subtractor:

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/d66f874b-c1f2-44b3-a035-7149b56430c1)



8 Bit Ripple Carry Adder

![image](https://github.com/navaneethans/VLSI-LAB-EXPERIMENTS/assets/6987778/7385a408-40a5-4203-8050-b72818622d79)



VERILOG CODE:
Full Adder:

module fulladder (sum, cout, a,b,c);

input a,b,c;

output sum, cout;

wire w1,w2,w3,w4,w5;

xor x1(w1,a,b);

xor x2(sum,w1,c);

and al(w2,a,b);

and a2(w3,b,c);

and a3(w4,a,c);

or o1(w5,w2,w3); or o2(cout,w5,w4);

endmodule


Full Subractor:

module full_subtractor(a, b, c,D, Bout);

input a, b, c;

output D, Bout;

assign D = a^b^c;

assign Bout = (~a & b) | (~(a^ b) & c);

endmodule


Half Adder:

module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

or(sum,a,b);

and(carry,a,b);

endmodule


Half Subractor:

module half_subtractor(D,Bo,A,B);

input A,B;

output D,Bo;

assign D=A^B;

assign Bo=(~A)&B;

endmodule


Logic Gates:

module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);

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


Ripple Carry Adder 4Bit:


module rippe_adder(S, Cout, X, Y,Cin);

 input [3:0] X, Y;// Two 4-bit inputs
 
 input Cin;
 
 output [3:0] S;
 
 output Cout;
 
 wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);
 
 fulladder u2(S[1], w2,X[1], Y[1], w1);
 
 fulladder u3(S[2], w3,X[2], Y[2], w2);
 
 fulladder u4(S[3], Cout,X[3], Y[3], w3);

endmodule

module fulladder(S, Co, X, Y, Ci);

  input X, Y, Ci;

  output S, Co;
  
  wire w1,w2,w3;
  
  xor G1(w1, X, Y);
  
  xor G2(S, w1, Ci);
  
  and G3(w2, w1, Ci);
  
  and G4(w3, X, Y);
  
  or G5(Co, w2, w3);

endmodule

OUTPUT:

Full Adder
![full adder](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/67c15795-e99e-4577-964b-5e594d5491dc)

Full Subractor
![full subractor](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/b57faf90-78fe-4fc3-ab79-dc909d37e368)

Half Adder
![half adder](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/954088fc-3af5-47ab-bb47-1407ed4d4c0e)

Half Subractor
![half subractor](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/7df075ba-e93c-444d-9d8e-642120f44ad4)

Logic Gates
![logic gates](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/06738fdd-56e0-4d76-8323-be721962f252)

Ripple Carry Adder
![ripple carry adder](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/b5b54f59-b2ed-4929-a6c0-ec411a8be469)
