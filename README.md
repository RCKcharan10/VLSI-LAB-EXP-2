# 2.SIMULATION AND IMPLEMENTATION OF  COMBINATIONAL LOGIC CIRCUITS

# AIM: 

To simulate ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.1.

# APPARATUS REQUIRED:

VIVADO 2023.1
  
# PROCEDURE:

1. Open Vivado: Launch Xilinx Vivado software on your computer.

2. Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

3. Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

4. Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

5. Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

6. Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

7. Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

8. Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

9. View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design.

# LOGIC DIAGRAM

ENCODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/3cd1f95e-7531-4cad-9154-fdd397ac439e)


DECODER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/45a5e6cf-bbe0-4fd5-ac84-e5ad4477483b)


MULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/427f75b2-8e67-44b9-ac45-a66651787436)


DEMULTIPLEXER

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/1c45a7fc-08ac-4f76-87f2-c084e7150557)


MAGNITUDE COMPARATOR

![image](https://github.com/navaneethans/VLSI-LAB-EXP-2/assets/6987778/b2fe7a05-6bf7-4dcb-8f5d-28abbf7ea8c2)


# VERILOG CODE

# 3to8 Decoder
```
module decoder(
   input [2:0] a,
   output [7:0] d );
assign d[0]=(~a[2])&(~a[1])&(~a[0]);
assign d[1]=(~a[2])&(~a[1])&(a[0]);
assign d[2]=(~a[2])&(a[1])&(~a[0]);
assign d[3]=(~a[2])&(a[1])&(a[0]);
assign d[4]=(a[2])&(~a[1])&(~a[0]);
assign d[5]=(a[2])&(~a[1])&(a[0]);
assign d[6]=(a[2])&(a[1])&(~a[0]);
assign d[7]=(a[2])&(a[1])&(a[0]);
endmodule
```

# Demultiplexer1to8
```
module demux(din,s,d);
input din;
input[2:0]s;
output [7:0]d;
assign d[0]=(din&~s [2]&~s[1]&~s[0]);
assign d[1]=(din&~s[2]&~s[1]&s[0]);
assign d[2]=(din&~s[2]&s[1]&~s[0]);
assign d[3]=(din&~s[2]&s[1]&s[0]);
assign d[4]=(din&s[2]&~s[1]&~s[0]);
assign d[5]=(din&s[2]&~s[1]&s[0]);
assign d[6]=(din&s[2]&s[1]&~s[0]);
assign d[7]=(din&s[2]&s[1]&s[0]);
endmodule
```

# Encoder8to3
```
module encoder_8_to_3(a0,a1,a2,d7,d6,d5,d4,d3,d2,d1,d0);
input d7,d6,d5,d4,d3,d2,d1,d0;
output a0,a1,a2;
or g1(a0,d1,d3,d5,d7);
or g2(a1,d2,d3,d6,d7);
or g3(a2,d4,d5,d6,d7);
endmodule
```
# Magnitude Comparator
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
if (a==b)
begin
eq = 1'b1;
lt = 1'b0;
gt = 1'b0;
end
else if (a>b)
begin
eq = 1'b0;
lt = 1'b0;
gt = 1'b1;
end
else
begin
eq = 1'b0;
lt = 1'b1;
gt = 1'b0;
end
end
endmodule
```

# Multiplexer8to1
```
module mux(a,s,y);
input [7:0]a;
input [2:0]s;
output y;
reg y;
always@({s ,a})
   begin
      case(s)
         3'b000: y=a[0];
         3'b001: y=a[1];
         3'b010: y=a[2];
         3'b011: y=a[3];
         3'b100: y=a[4];
         3'b101: y=a[5];
         3'b110: y=a[6];
         3'b111: y=a[7];
      endcase
   end
endmodule
```
# OUTPUT WAVEFORM

# Multiplexer

![Mux](https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/75ee160b-f792-4efe-858e-7ca4e9926b78)

# Magnitude Comparator

![Magnitude Comparator](https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/57cb0b12-6d67-4616-b9e9-a4cfb7cf00e8)

# Demultiplier

![Demux](https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/bc25a819-6920-48ea-a2c9-1681714ea38c)

# 8 to 3 Encoder

![8 to 3 Encoder](https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/aafc8e5d-90bb-4619-92ae-5a996f575cf9)

# 3 to 8 Decoder

![3 to 8 Decoder](https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/6e4f30fb-8da4-4f13-9096-d7aa9559baac)

# RTL Design

# Multiplexer

<img width="761" alt="8 to 1 Multiplexer" src="https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/85c03dbc-f941-4c48-9ddf-49f4ab5342c4">

# Magnitude Comparator

<img width="761" alt="Magnitude Comparator" src="https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/581f136c-8f0f-40aa-981b-b8299e269f9d">

# Demultiplier

<img width="767" alt="1 to 8 Demultiplier" src="https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/8e681a69-d96e-489a-bea1-b9e273d43b94">

# 8 to 3 Encoder

<img width="764" alt="8 to 3 Encoder" src="https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/08f3ff7c-b9e5-469b-8bb8-53c980cd1ca0">

# 3 to 8 Decoder

<img width="766" alt="3 to 8 Decoder" src="https://github.com/RCKcharan10/VLSI-LAB-EXP-2/assets/117891438/d3549f3d-02f0-47f0-ad57-e5022d165e3b">


# RESULT

Thus the Simulation and Implementaion of Combinational Logic Circuits is Verified


