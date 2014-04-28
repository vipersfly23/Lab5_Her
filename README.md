Lab5_Her
========

PRISM implementation on FPGA
========

#### 1st Program Discussion

The purpose of this program is to keep adding 1 until the number in the accumulator is no longer negative. if the number is negative the program jumps back to the operation in which one is added to the accumulator. Once the number in the accumulator is no longer negative, it ends.

#### Program 1 Controller States.

(note: Starting at 35ns, since 0-30ns is given).

  ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/1.gif?raw=true "Control State 1 of 4")
  
  Step 1: Fetching the new Instruction
    - note irld is high, and so is pcld.
  Step 2: Decodes it, and receives the instruction to add the number 1.
  Step 3: Immediate Execute State. 
    - addition is done, accumulator is reloaded.
    -PCLD and ACCLD are both high.
  Step 4: New instruction is fetched
  
  ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/2.gif?raw=true "Control State 2 of 4")
  
  Step 1: Decode state.  instruction output is obtained.
    - IRld and PCld are both high.
  Step 2: Decode LoAddr state. Output is chosen
    - PCld High, MARlo high.
  Step 3: Direct I/O Execute: Value is output.
  Step 4: Fetch State.
  
  ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/3.gif?raw=true "Control State 3 of 4")
  
  Step 1: Decode state.  instruction jump negative is obtained.
    - IRld and PCld are both high.
  Step 2: Decode LoAddr state
    - PCld high, and MARlo High.
      - Lo 4 bit address is obtained
  Step 3: Decod HiAddr state
    -PCld highm MARhi High
      - high bit address is obtained
  Step 4: Jump is executed.
    
  ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/4.gif?raw=true "Control State 4 of 4")
  
  Step 1: Fetch State happened before.
  Step 2: Decode state, Jump instruction is obtained.
    - IRld and PCld are both high.
  Step 3: Decode LoAddr state
    - PCld high, and MARlo High.
      - Lo 4 bit address is obtained
  Step 4: Decod HiAddr state
    -PCld highm MARhi High
      - high bit address is obtained
  Step 5: Jump is executed.
  Step 6: Program repeatedly jumps to this same address. Thus program is complete.
  
          

#### Answers to Questions

1.	When the controller’s current state is “FETCH,” what is the status of the following control lines:

a.	PCLd-  high

b.	IRLd- high

c.	ACCLd- low

2.	The current state is Decode LoAddr and the IR contains “OUT.”  What are the control signals are asserted, and what will the next state be?

Controls signal asserted: marlold, pcld, memsel_l, and alesszero_int
Next State: Direct I/O Execute

3.	What are the three status signals sent from the PRISM datapath to the PRISM controller?

AeqZero_int, AlessZero_Int, and IR.

4.	Why is it important that ACCLd signal be active during the execute state for the ADDI instruction?
Accld must be active during the execution of ADDI because the number in the operand is being added to the number
in the accumulator, and loaded back into the accumulator, thus it must be active to load the sum.


5.	What changes are necessary to the PRISM datapath to add another instruction (SUBI, which would subtract an immediate value from the accumulator) to the instruction set?
The required addition is a method that stores the value in the accumulator, followed by an instruction that loads an operand into the accumulator (LDAI), followed by negating it (NEG), then ADDD, which adds the stored value to the current value in the accumulator, which would result in subtraction.


##Required Functionality:

  1st program Demo on FPGA [COMPLETED]
  
  2nd program Demo in PRISM [COMPLETED] *image below*
  
  
   ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/Program_2_PRISM.GIF?raw=true "PRISM SNIP")
  
  
  2nd program Demo in FPGA [COMPLETED] *image below*
  
  
   ![alt text](https://github.com/vipersfly23/Lab5_Her/blob/master/FPGA.GIF?raw=true "FPGA SNIP")
 
 
  

  
