### Half Adder

Verilog

```verilog
module halfadder(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule
```

TestBench
```verilog
module halfadder_tb;
reg a;
reg b;
wire sum;
wire carry;
halfadder uut (
.a(a),
.b(b),
.sum(sum),
.carry(carry) );
 initial begin
a = 0; b = 0; #100;
a = 0; b = 1; #100;
a = 1; b = 0; #100;
a = 1; b = 1; #100;
 end
endmodule
```

### Half subtractor 

Verilog

```verilog
module HS(a,b,diff,borrow);
input a,b;
output diff,borrow;
assign diff=a^b;
assign borrow=!(a)&b;
endmodule
```

TestBench
```verilog
module HS_tb;
reg a;
reg b;
wire diff;
wire borrow;
HS uut (
.a(a),
.b(b),
.diff(diff),
.borrow(borrow) );
 initial begin
 a = 0; b = 0; #100;
 a = 0; b = 1; #100;
 a = 1; b = 0; #100;
 a = 1; b = 1; #100;
 end
endmodule
```

### Full Adder

Verilog

```verilog
module FA(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=(a&b)||(b&c)||(c&a);
endmodule
```

TestBench
```verilog
module FA_tb;
reg a;
reg b;
reg c;
wire sum;
wire carry;
FA uut (
.a(a),
.b(b),
.c(c),
.sum(sum),
.carry(carry) );
initial begin
a = 0;b = 0;c = 0;#100;
a = 0;b = 0;c = 1;#100;
a = 0;b = 1;c = 0;#100;
a = 0;b = 1;c = 1;#100;
a = 1;b = 0;c =0;#100;
a = 1;b = 0;c = 1;#100;
a =1;b = 1;c = 0;#100;
a = 1;b = 1;c = 1;#100;
end
endmodule
```


### Full Subtractor 

Verilog

```verilog
module FS(a,b,c,diff,borrow);
input a,b,c;
output diff,borrow;
assign diff=a^b^c;
assign borrow=((!a)&b)|(b&c)|((!a)&c);
endmodule
```

TestBench
```verilog
module FS_tb;
reg a;
reg b;
reg c;
wire diff;
wire borrow;
FS uut (
.a(a),
.b(b),
.c(c),
.diff(diff),
.borrow(borrow) );
initial begin
a = 0;b = 0;c = 0;#100;
a = 0;b = 0;c = 1;#100;
a = 0;b = 1;c = 0;#100;
a = 0;b = 1;c = 1;#100;
a = 1;b = 0;c = 0;#100;
a = 1;b = 0;c = 1;#100;
a = 1;b = 1;c = 0;#100;
a = 1;b = 1;c = 1;#100;
end
endmodule
```


### 2:1 MUX

Verilog

```verilog
module two_one(i1,i2,s,y);
input i1,i2,s;
output y;
assign y = s?i2:i1;
endmodule
```

TestBench
```verilog
module top;
reg i1,i2,s;
wire y;
two_one(i1,i2,s);
initial begin
s=0;
i1=0;i2=1;#100;
s=1;
end
endmodule
```


### 4:1 MUX

Verilog

```verilog
module four_to_one_MUX
(I1,I2,I3,I4,S1,S2,Y);
 input I1,I2,I3,I4;
 input S1,S2;
 output Y;
 
assign 
Y=((!S1)&(!S2)&I1)|((!S1
)&(S2)&I2)|(S1&(!S2)&I3
)|(S1&S2&I4);
endmodule
```

TestBench
```verilog
module four_to_one_MUX_tb;
reg I1;
reg I2;
reg I3;
reg I4;
reg S1;
reg S2;
wire Y;
four_to_one_MUX uut (
.I1(I1),
.I2(I2),
.I3(I3),
.I4(I4),
.S1(S1),
.S2(S2),
.Y(Y) );
 initial begin
I1 = 0;I2 = 0;I3 = 0;I4 = 1;
S1 = 0;S2 = 1; #100;
end
endmodule
```



### 8:1 MUX

Verilog

```verilog
module eight_to_one_MUX
(I1,I2,I3,I4,I5,I6,I7,I8,S1,S2,S3,Y);
 input I1,I2,I3,I4,I5,I6,I7,I8;
 input S1,S2,S3;
 output Y;
assign Y=((!S1)&(!S2)&(!S3)&I1)
|((!S1)&(!S2)&S3&I2)|((!S1)&S2&
(!S3)&I3)|((!S1)&S2&S3&I4)|(S1
&(!S2)&(!S3)&I5)|(S1&(!S2)&S3
&I6)|(S1&S2&(!S3)&I7)|(S1&S2&
S3&I8);
endmodule
```

TestBench
```verilog
module eight_to_one_MUX1;
reg I1;
reg I2;
reg I3;
reg I4;
reg I5;
reg I6;
reg I7;
reg I8;
reg S1;
reg S2;
reg S3;
wire Y;
eight_to_one_MUX uut (
.I1(I1), .I2(I2), .I3(I3), .I4(I4),
.I5(I5), .I6(I6), .I7(I7), .I8(I8),
.S1(S1), .S2(S2), .S3(S3),
.Y(Y) );
 initial begin
I1 = 1;I2 = 1;I3 = 1; I4 = 1;I5 = 
1;I6 = 0;I7 = 1;I8 = 1;
S1 = 1; S2 = 0; S3 = 1; #100;
 end 
endmodule
```

### BCD 

Verilog

```verilog
module deciadder(a,b,carry_in,sum,carry);
//declare the inputs and outputs of the module with their sizes.
 input [3:0] a,b;
 input carry_in;
 output [3:0] sum;
 output carry;
 //Internal variables
 reg [4:0] sum_temp;
 reg [3:0] sum;
 reg carry; 
//always block for doing the addition
 always @(a,b,carry_in)
 begin
 sum_temp = a+b+carry_in; //add all the inputs
 if(sum_temp > 9) 
begin
 sum_temp = sum_temp+6; //add 6, if result is more than 9.
 carry = 1; //set the carry output
 sum = sum_temp[3:0]; 
end
 else 
begin
 carry = 0;
 sum = sum_temp[3:0];
 end
 end 
endmodule
```

TestBench
```verilog
module deciadder_tb;
reg [3:0] a;
reg [3:0] b;
reg carry_in;
wire [3:0] sum;
wire carry;
deciadder uut (.a(a), .b(b), .carry_in(carry_in), .sum(sum), .carry(carry));
initial begin
// Initialize Inputs
a = 9;
b = 6;
carry_in = 0;
#100;
end
endmodule
```






