# SIMULATION AND IMPLEMENTATION OF MULTIPLIER
**AIM:**<br>

&emsp;&emsp;To simulate and implement binary multiplier using VIVADO 2023.2.<br>

**APPARATUS REQUIRED:**<br>

&emsp;&emsp;VIVADO 2023.2<br>

**PROCEDURE:**<br>

 STEP:1 Launch the Vivado 2023.2 software.<br>
 STEP:2 Click on “create project ” from the starting page of vivado.<br>
 STEP:3 Choose the design entry method:RTL(verilog/VHDL).<br>
 STEP:4 Crete design source and give name to it and click finish.<br>
 STEP:5 Write the verilog code and check the syntax.<br>
 STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.<br>
 STEP:7 Verify the output in the simulation window.<br>



**2 BIT MULTIPLIER:**

**LOGIC DIAGRAM:**
  
![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

**VERILOG CODE:**

```
module HalfAdder(a,b,sum,carry);
input a,b;
output sum,carry;
xor (sum,a,b);
and (carry,a,b);
endmodule

module Multiplier(a,b,y);
input [1:0]a,b;
output [3:0]y;
wire w1,w2,w3,w4;
and a1(y[0],a[0],b[0]);
and a2(w1,a[1],b[0]);
and a3(w2,a[0],b[1]);
and a4(w3,a[1],b[1]);
HalfAdder h0(w1,w2,y[1],w4);
HalfAdder h1(w3,w4,y[2],y[3]);
endmodule
```

**OUTPUT:**

![image](https://github.com/SwarnaMallikaPL/VLSI-LAB-EXP-3/assets/160829667/1a721c5c-f47d-4061-9f86-b1aedb05d4b0)

**4 BIT MULTIPLIER:**

**LOGIC DIAGRAM:**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)

**VERILOG CODE:**

```
module ha(s,c,a,b);
input a,b;
output s,c;
xor g1(s,a,b);
and g2(c,a,b);
endmodule

module fa(s,co,a,b,c);
input a,b,c;
output s,co;
wire w1,w2,w3;
xor g1(w1,a,b);
xor g2(s,w1,co);
and g3(w2,w1,c); 
and g4(w3,a,b);
or g5(co,w2,w3);
endmodule

module mul4(p,a,b);
input [3:0] a, b;
output [7:0] p;
wire [15:1] w;
wire [10:1] c;
wire [6:1] s;
and g1(p[0],a[0],b[0]);
and g2(w[1],a[1],b[0]);
and g3(w[2],a[2],b[0]);
and g4(w[3],a[3],b[0]);
and g5(w[4],a[0],b[1]);
and g6(w[5],a[1],b[1]);
and g7(w[6],a[2],b[1]);
and g8(w[7],a[3],b[1]);
and g9(w[8],a[0],b[2]);
and g10(w[9],a[1],b[2]);
and g11(w[10],a[2],b[2]);
and g12(w[11],a[3],b[2]);
and g13(w[12],a[0],b[3]);
and g14(w[13],a[1],b[3]);
and g15(w[14],a[2],b[3]);
and g16(w[15],a[3],b[3]);
ha ha1(p[1],c[1],w[4],w[1]);
fa fa1(s[1],c[2],w[5],w[2],c[1]);
fa fa2(s[2],c[3],w[6],w[3],c[2]);
ha ha2(s[3],c[4],w[7],c[3]);
ha ha3(p[2],c[5],w[8],s[1]);
fa fa3(s[4],c[6],s[2],w[9],c[5]);
fa fa4(s[5],c[7],s[3],w[10],c[6]);
fa fa5(s[6],c[8],c[4],w[11],c[7]);
ha ha4(p[3],c[9],w[12],s[4]);
fa fa6(p[4],c[10],w[13],s[5],c[9]);
fa fa7(p[5],c[11],w[14],s[6],c[10]);
fa fa8(p[6],p[7],w[15],c[8],c[11]);
endmodule
```

**OUTPUT:**

![image](https://github.com/SwarnaMallikaPL/VLSI-LAB-EXP-3/assets/160829667/4aa1b7bc-3e8c-4a89-9232-48deef62a808)

**RESULT:**<br>
&emsp;&emsp;Thus the simulation and implementation of binary multipliers is done and the outputs are verified successfully.




