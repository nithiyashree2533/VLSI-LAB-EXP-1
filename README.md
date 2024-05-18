# VLSI-LAB-EXPERIMENTS 



EXP NO : 1

Date :16.2.24/23.2.24
               

           SIMULATION AND IMPLEMENTATION OF LOGIC GATES, ADDERS AND SUBTRACTIONS


           
AIM: 


      To simulate and synthesis Logic Gates,Adders and Subtractor using Xilinx ISE.



APPARATUS REQUIRED: 



        Vivado - software



PROCEDURE:


STEP:1 Start the Xilinx navigator, Select and Name the New project. 



STEP:2 Select the device family, device, package and speed.



STEP:3 Select new source in the New Project and select Verilog Module as the Source type. 



STEP:4 Type the File Name and Click Next and then finish button. Type the code and save it.



STEP:5 Select the Behavioral Simulation in the Source Window and click the check syntax.



STEP:6 Click the simulation to simulate the program and give the inputs and verify the outputs as per the truth table.



STEP:7 Select the Implementation in the Sources Window and select the required file in the Processes Window.



STEP:8 Select Check Syntax from the Synthesize XST Process. Double Click in the Floorplan Area/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 



STEP:9 In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.



STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.



STEP:11 Load the Bit file into the SPARTAN 6 FPGA 



STEP:12 On the board, by giving required input, the LEDs starts to glow light, indicating the output.



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



### Logic Gates:
```
module logicgate (a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);
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


### Half Adder
```
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
xor g1(sum,a,b);
and g2(carry,a,b);
endmodule
```



### Half Subtractor
```
module halfsubtractor(a,b,diff,borrow);
input a,b;
output diff,borrow;
xor g1(diff,a,b);
and g2(borrow,~a,b);
endmodule
```



### Full Adder
```
module fadd(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
wire w1,w2,w3;
xor g1(w1,a,b);
and g2(w2,a,b);
xor g3(sum,w1,c);
and g4(w3,w1,c);
or g5(carry,w3,w2);
endmodule
```



### Full Subtractor
```



module fs(a,b,bin,d,bout);
input a,b,bin; 
output d,bout;
wire w1,w2,w3;
xor g1(w1,b,bin; 
xor g2(d,w1,a);
and g3(w2,a,~w1);
and g4(w3,~b,bin);
or g5(bout,w2,w3);
endmodule
```



### 8 bit ripple carry adder
```
module ripplemod(a, b, cin, sum, cout);
input [07:0] a;
input [07:0] b;
input cin;
output [7:0]sum;
output cout;
wire[6:0] c;
fulladd a1(a[0],b[0],cin,sum[0],c[0]);
fulladd a2(a[1],b[1],c[0],sum[1],c[1]);
fulladd a3(a[2],b[2],c[1],sum[2],c[2]);
fulladd a4(a[3],b[3],c[2],sum[3],c[3]);
fulladd a5(a[4],b[4],c[3],sum[4],c[4]);
fulladd a6(a[5],b[5],c[4],sum[5],c[5]);
fulladd a7(a[6],b[6],c[5],sum[6],c[6]);
fulladd a8(a[7],b[7],c[6],sum[7],cout);
endmodule
module fulladd(a, b, cin, sum, cout);
input a;
input b;
input cin;
output sum;
output cout;
assign sum=(a^b^cin);
assign cout=((a&b)|(b&cin)|(a&cin));
endmodule
```



OUTPUT:  


### Logic Gates:



#### AND GATE



![and gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/559dbcef-d330-462d-ae7d-38a97b4509f2)



#### OR GATE



![or gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/60d878d7-c456-4f2f-9a97-68c0cb471e17)



#### NAND GATE



![nand gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/65482277-69bf-465f-9d15-c155a45a5c2c)



#### NOR GATE



![nor gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/e27ae117-5ca7-42c2-b6ca-103bedd6f0b2)



#### XOR GATE



![xor gate - Copy](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/d8c54505-215a-47e6-a7bb-417c29e3dbc5)



#### XNOR GATE



![xnor gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/5f3b131f-72e0-40d5-85e9-05131e23dcc0)



#### NOT GATE



![not gate](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/11841114-0b18-4ba1-9e0d-8b2669596c73)



### HALF ADDER



![ex no;1 half adder](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/3e242fd3-fa9a-45a2-8bf9-8626f452ab83)



### HALF SUBTRACTOR



![ex no 5 half subtractor](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/f77b3dd7-37d7-450c-ab38-eca4e0fe8f93)



### FULL ADDER



![EX NO 3 full adder](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/fbbcbac8-1da0-4792-aaf7-b87d5c4d4300)



### FULL SUBTRACTOR



![ex no 4 full subtractor](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/e7e4c1e7-27de-4251-92e0-19e8e0acac4e)



### 8 BIT RIPPLE CARRY ADDER



![ex no;2 allgates](https://github.com/nithiyashree2533/VLSI-LAB-EXP-1/assets/161813688/d922f01e-c994-4883-b653-7670fa932894)



RESULT:



Hence Logic Gates,Adders and Subtractor are simulated and synthesised using Xilinx ISE.
