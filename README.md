# VLSI-LAB-EXPERIMENT

AIM: To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.

APPARATUS REQUIRED: Xilinx 14.7 Spartan6 FPGA

PROCEDURE: 

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

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
<img width="954" alt="full adder" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/7e069dfe-1a96-46b8-a7f7-7ef0a8ea9e92">

Full Subractor
![full subractor](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/b57faf90-78fe-4fc3-ab79-dc909d37e368)
<img width="962" alt="full subractor" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/94d1feb1-71e1-4f65-8baa-7d7d5ac090f1">

Half Adder
![half adder](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/954088fc-3af5-47ab-bb47-1407ed4d4c0e)
<img width="962" alt="half adder" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/12033a0e-30f7-4ccc-97c8-807177cfb018">

Half Subractor
![half subractor](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/7df075ba-e93c-444d-9d8e-642120f44ad4)
<img width="962" alt="half sub" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/def7bc86-1022-429a-af60-2535f83e51fd">

Logic Gates
![logic gates](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/06738fdd-56e0-4d76-8323-be721962f252)
<img width="962" alt="logic gates" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/a02904ff-83db-4015-a564-912d7a9948b9">

Ripple Carry Adder
![ripple carry adder](https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/b5b54f59-b2ed-4929-a6c0-ec411a8be469)
<img width="956" alt="ripple carry adder" src="https://github.com/yuva007tech/VLSI-LAB-EXP-1/assets/123287599/65a64bfe-c308-4d92-ba3e-fea19e4e90c1">

result:

Thus the Simulation of Logic Gates ,Adders and Subtractors is done and verified.
