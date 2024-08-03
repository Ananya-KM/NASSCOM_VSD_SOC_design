# _DIGITAL_VSD_SOC_Design
## PHYSICAL DESIGN IN VLSI
</P> Physical design in VLSI is the process of converting a circuit's high-level description into a detailed physical layout on silicon. It involves steps like partitioning, floorplanning, placement, routing, and verification to optimize performance, area, power, and manufacturability. The goal is to create a layout that can be fabricated into a functional chip.

## WORKSHOP CONTENTS
1.Introduction to open source eda tool(openlane) and PDK(skywater130nm).

2.Floorplan and Powerplan.

3.Cell design using Magic Layout and Ngspice characterization.

4.Pre-layout timing analysis and importance to good clock tress(i.e minimum skewness).

5.Final steps for RTL2GDS flow.

# DAY 1
## INTERACTION WITH COMPUTERS
![Screenshot (46)](https://github.com/user-attachments/assets/86c2fab4-2904-4b7c-8a68-ff1daae728ba)

The Arduino Uno board features a processor as the primary component of interest. The physical design will focus on the macro within the processor, implementing a block-level design.
The image below displays the microcontroller board or PCB with various components arranged on it.

![Screenshot (45)](https://github.com/user-attachments/assets/edd5523f-5b91-4793-b312-5a36bff1cca2)

## IC Design components and terminolgies

![Screenshot (37)](https://github.com/user-attachments/assets/2b31eba4-ccfe-4397-aece-9a10dcd2eec3)  ![Screenshot (38)](https://github.com/user-attachments/assets/ad9b3a63-0283-4b48-b4b8-902a8b44e191)

</p> 1. CORE : The core is the section of the chip where the fundamental logic of the design is placed.

</p> 2.DIE :The die is a segment of a chip that includes the core and I/O pads. To enhance production efficiency and yield, several copies of the die are patterned across the silicon wafer.

</p> 3.IO PADS: I/O pads are the pins that facilitate communication between the core and the external environment. These pads are positioned around the rectangular metal areas where external connections are made. They include input pads, output pads, and power pads.

 </p> 4.IPs : Foundry IPs, such as SRAM, ADC, DAC, and PLLs, are typically designed with significant human involvement. They require manual design and engineering expertise to define and create. These IPs are essential components that integrate into a chip, and their design often involves customizing and optimizing them for specific applications and performance requirements.</p>
 
 </p> 5.PDKs : PDKs (Process Design Kits) serve as a bridge between foundries and design engineers. They provide essential files and models for IC design tools, covering aspects like device models, DRC, LVS, physical extraction, layers, LEF, standard cell libraries, and timing libraries. In this workshop, the SkyWater 130nm PDK, specifically sky130_fd_sc_hd, is used, and the openLANE toolchain is built around this PDK.

 ## SIMPLIFIED RTL TO GDS FLOW 
 </p> The simplified RTL to GDS Flow is given in the image below
 
 ![Screenshot (41)](https://github.com/user-attachments/assets/c8295493-1777-47b5-8249-ef97c545dd9f)

 ## SOC DESIGN AND OPENLANE 
 
 </p> OpenLANE is an open-source EDA toolchain designed for digital ASIC design and optimization. It integrates various tools and flows to streamline the design process from RTL to GDSII. OpenLANE leverages the SkyWater 130nm PDK for standard cell libraries and design rules. It automates key steps such as synthesis, placement, and routing, enhancing design efficiency. The toolchain is tailored for academic and research purposes, facilitating open access to advanced ASIC design methodologies. </p>
 
 ![Screenshot (43)](https://github.com/user-attachments/assets/2cd07053-ac6e-4fc1-8a80-524202b10a9a)

 # DAY 1 (LABS)
 ## Understanding the use of various linux commands :
 </p> Open the LINUX Terminal (in desktop directory)
 
![WhatsApp Image 2024-07-27 at 1 06 04 PM](https://github.com/user-attachments/assets/7f4da44d-13ed-42a7-a444-890eb4604b13)


 Important LINUX Commands
</p> 1. cd : It is used to change the current working directory.
</p> 2. ls : It lists the contents of a directory.
</p> 3.ls -ltr : It lists the contents of a directory in long format, sorted by modification time in reverse order (oldest first).
</p> 4.ls --help: It displays a help message with a list of options and usage information for the "ls" command. Note : You can give any command name and then type "--help" to get info about that command.</p>
</p> 5.cd : Using this command we can move in both ways in the directory tree.</p>
</p> 6.clear: It clears the terminal screen.

 ### **Now, moving to the work directory where all files related to the workshop are stored**,use the follwoing commands
    cd Desktop 
    cd work/tools/ 
    cd openlane_working_dir/
    cd openlane/
    
   ![WhatsApp Image 2024-07-27 at 1 06 04 PM (1)](https://github.com/user-attachments/assets/4ec71fc5-d882-4fe5-b0ec-c79724a908a4)

  ### To enter into bash while being in the openalne dircetory use the  following command
      docker
      ./flow.tcl -interactive

      
   ![WhatsApp Image 2024-07-27 at 1 06 04 PM (3)](https://github.com/user-attachments/assets/76f12cf7-421f-4260-8e0b-d7ab8e36e990)

      
   
###  Now, OPENLANE is opened, and we input the required packages using the following command:
     % package require openlane 0.9 
     
### In the 'designs' subdirectory, you will find various pre-built designs. For our purposes, we will focus on the "picorv32a.v" design to execute the RTL to GDS flow. The initial stage of this project involves synthesis. To begin the synthesis for this design, we need to set it up using the following command:
    prep -design picorv32a
   
   ![WhatsApp Image 2024-07-27 at 1 06 04 PM (3)](https://github.com/user-attachments/assets/fbadc046-cb84-4a6e-a4a2-87716d25e083)

   Once the preparation is finished, you'll notice a new directory named with today's date created inside the 'picorv32a' folder within the 'runs' directory.

   ![WhatsApp Image 2024-07-27 at 1 06 04 PM (2)](https://github.com/user-attachments/assets/e4addc8b-50a2-4ecb-b3c1-e71a71b9a50f)

###  A new directory structure is created to organize design files, with subdirectories for components like results and reports.

**LEF Merging**: The technology LEF (.tlef) and cell LEF (.lef) files are merged into a unified format, combining layer and cell information.

**Design Placement**: All design-related files are placed under the designs directory for organization and easy access during subsequent steps.
![WhatsApp Image 2024-07-27 at 1 06 04 PM (2)](https://github.com/user-attachments/assets/7af31805-654a-4947-8f8b-86f568e0c7b0)

![WhatsApp Image 2024-07-27 at 1 06 04 PM (5)](https://github.com/user-attachments/assets/d71596a2-325c-4d75-89da-a7fd86b81e69)

config.tcl -	contains the configurations used by openLANE </p>
src -	contains verilog files and constraints file 

![WhatsApp Image 2024-07-27 at 1 06 04 PM (7)](https://github.com/user-attachments/assets/3c480617-efc9-4f39-904f-6ab097ac5de0)

### Now, To perform synthesis on the design use the following command :
    % run_synthesis
    
![WhatsApp Image 2024-07-27 at 1 06 05 PM (1)](https://github.com/user-attachments/assets/74635651-ca47-415e-bbb3-6a333fa6b19d)

 ### next step is to find the flop ratio.

</p> formaula to find flop ratio is (number of D-ff/Total number of cells) </p>

</p> and to get the percentage(%) multiply it by 100

![WhatsApp Image 2024-07-27 at 1 06 05 PM (2)](https://github.com/user-attachments/assets/4d14b6c2-76bf-4fe0-aa50-a076571144ef)

![WhatsApp Image 2024-07-27 at 1 06 05 PM (3)](https://github.com/user-attachments/assets/be1112f6-489a-4c67-a7c4-723837b9f418)

### **Number of D-ff=1613 & Total number of cells=14876**

### **therefore,Flop ratio=(1613/14876)=0.1084296853993**

### **Flop ratio is %=10.84296853993%**

# DAY 2
## Floorplan & Powerplan
</p>  To determine the utilization factor and aspect ratio, we first need to calculate the height and width of the core and die. </p>

![Screenshot (47)](https://github.com/user-attachments/assets/f8329c03-6504-4f20-b87e-3a1bc5a8efa0)

</p> The dimensions of the core area are determined by the design's netlist, which depends on the number of components necessary to implement the logic. Consequently, the height and width of the die area are based on the dimensions of the core area. </p>

</p> For example, consider a netlist that includes two logic gates and two flip-flops. </p> 

![Screenshot (48)](https://github.com/user-attachments/assets/502854c1-bc84-40d1-941c-980384185f32)

</p> Now, if we consider each element having an area of 1 square unit, and the netlist contains 4 elements, the minimum total area required for the core area will be 4 square units.</p>

![Screenshot (49)](https://github.com/user-attachments/assets/2979870b-0016-4c3f-9b7d-d1aeaa63508e)

### Utilization Factor

The Utilization Factor is defined as the ratio of the core area occupied by the netlist to the total core area. In an effective floorplan, the Utilization Factor should not be 1. If the Utilization Factor reaches 1, there will be no available space for adding any additional logic, making it a poor floorplan.

![Screenshot (50)](https://github.com/user-attachments/assets/7cca3ad4-2d7c-4698-bcca-af969f21ad7b)

#### **Utilization Factor = (Area occupied by netlist / Total core area)**

### Aspect Ratio

The Aspect Ratio is defined as the ratio of the height of the core to its width. When the Aspect Ratio is 1, the core is considered square-shaped. If the Aspect Ratio is different from 1, the core will have a rectangular shape. 

</p> In the below case </p>

#### **Aspect Ratio = (Height of the core / Width of the core)**

![Screenshot (51)](https://github.com/user-attachments/assets/b869917d-fe89-4724-96de-cfcb96cff284)

#### **Utilisation Factor = (4 sq units)/(4sq units) = 1**
#### **Aspect Ratio = (2 units)/(2 units) = 1 i.e core has Square Shape**

</p> now if we take another case </p>

![Screenshot (52)](https://github.com/user-attachments/assets/065d20fc-3b52-460b-b664-e7c6b343f13d)

#### **Utilisation Factor = (4 sq units)/(8 sq units) = 0.5**
#### **Aspect Ratio = (2 units)/(4 units) = 0.5 i.e core has Rectangular Shape**

# DAY 2 (LABS)
## STEPS TO RUN FLOORPLAN USING OPENLANE
</p>To ensure a smooth floorplanning process, designers need to pay close attention to specific parameters, often referred to as switches, which can significantly influence the final floorplan when modified. Key examples of these switches include the utilization factor and the aspect ratio. It is essential for designers to confirm that these parameters meet the project requirements before beginning the floorplanning stage. The image below showcases various types of switches involved in this phase.</p>


####  To run the Floorplan Use the following command:
     % run_floorplan
![WhatsApp Image 2024-07-29 at 10 55 12 PM](https://github.com/user-attachments/assets/faa0d020-84ed-4e17-a42e-de22b69e8de1)

![WhatsApp Image 2024-07-29 at 10 55 14 PM](https://github.com/user-attachments/assets/fa83f05b-05b3-41e7-8a21-b7c8d81208d7)

![WhatsApp Image 2024-07-29 at 10 55 13 PM](https://github.com/user-attachments/assets/b58de510-cd1b-48ba-8df8-1c97da8b1287)



</p> After completing the floorplan, you can review the generated report to evaluate aspects such as die area. To visualize the design in a graphical user interface (GUI), the MAGIC tool should be used. </p>

 #### Now, to open this "def" file in magic , use the following command:
      magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.floorplan.def 
      

![WhatsApp Image 2024-07-29 at 10 55 15 PM](https://github.com/user-attachments/assets/462fbfa2-37f4-4148-add7-7f2cb5333c26)

 ![WhatsApp Image 2024-07-29 at 10 55 19 PM (2)](https://github.com/user-attachments/assets/79b26cf5-3b25-4340-81e3-926ff072e98a)
 
 Now, we can use 'Magic' tool to expllore the floorplan.</p>
 
![WhatsApp Image 2024-07-29 at 10 55 19 PM (1)](https://github.com/user-attachments/assets/26bf5c33-d69b-4924-a943-1334310f076b)

</p> THe DESIGN ALLIGNMENT INSTRUCTIONS ARE AS FOLLOWS: </p>

### Centering the Design:</p>
    Press S to select the entire design.</P>
    Press V to vertically align it to the middle of the screen.</p>
### Zooming In on a Specific Area:</p>
    Left-click and drag to select the desired region.</p>
    Right-click to bring up the context menu.</p>
    Press Z to zoom in on the selected area.</p>
### Getting Details of a Cell:</p>
    Move your cursor to the cell of interest.</p>
    Press S to select the cell.
### In the tkcon window, enter the command "what" to display cell details.</p>

![WhatsApp Image 2024-07-29 at 10 55 22 PM](https://github.com/user-attachments/assets/60445c80-2a2a-4145-acca-b2b00a2fbc0d)

![WhatsApp Image 2024-07-29 at 10 55 22 PM (1)](https://github.com/user-attachments/assets/11af4acb-eff2-4e02-b52e-9a27ebc66cb1)

## PERFORMING PLACEMENT IN OPENLANE
After successfully completing floorplanning, the design process progresses to the placement stage, which includes two main phases:

### Global Placement:
</p> During this phase, the tool determines the approximate locations for all the standard cells in the design.</p>

### Detailed Placement:
</P>  In this phase, the tool finalizes the exact positions for all the standard cells and ensures the placement is legal. Legalization involves verifying that no standard cells overlap and that they are all correctly positioned within the designated site rows.</P>

### To initiate the placement process, use the following command
    run_placement
    
   ![WhatsApp Image 2024-07-29 at 10 55 27 PM](https://github.com/user-attachments/assets/82b5c708-b4d5-4897-a488-f86696a07ebe)

   ![WhatsApp Image 2024-07-29 at 10 55 27 PM (1)](https://github.com/user-attachments/assets/b596055a-082d-4aae-b9c0-918d095b148c)

#### After the Placement is done , we can see 'picorv32a.placement.def' file , open it using MAGIC use the follwoing command:
     magic -T /home/vsduser/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic/sky130A.tech lef read ../../tmp/merged.lef def read picorv32a.placement.def

![WhatsApp Image 2024-07-29 at 10 55 26 PM (1)](https://github.com/user-attachments/assets/d5e6d0bf-3d73-44f9-a443-ab973843577f)

![WhatsApp Image 2024-07-29 at 10 55 26 PM](https://github.com/user-attachments/assets/f750f9c0-aaa0-4864-a137-be506021b8e9)

# DAY 3
### CREATION OF SPICE DECK FOR CMOS INVERTER
</p> A Spice deck essentially contains the netlist with connectivity information, the inputs to be provided, output tap points, and additional details. </p>

![Screenshot (59)](https://github.com/user-attachments/assets/98e6668c-a1a3-4c8e-8008-ff1a07aea726)

</p>  Nodes are required to define the netlist </p>

![Screenshot (61)](https://github.com/user-attachments/assets/d9421a81-dc9d-43c4-9d72-d26aa26ced43)
![Screenshot (62)](https://github.com/user-attachments/assets/082cd9a2-5d48-4cee-826f-c433a5db9aa4)

![Screenshot (63)](https://github.com/user-attachments/assets/e9e79c0e-9b1e-4a4a-af5f-17d89934ecf0)


## INVERTER CHARACTERISTICS
### STATIC CHARACTERISTICS

- **Switching Threshold (Vth)**: The voltage level at which the inverter switches from a high state (logic 1) to a low state (logic 0).
- **Input Low Voltage (Vil)**: The highest input voltage that is still interpreted as logic 0.
- **Input High Voltage (Vih)**: The lowest input voltage that is recognized as logic 1.
- **Output Low Voltage (Vol)**: The voltage level at which the output changes from a high state to a low state.
- **Output High Voltage (Voh)**: The voltage level at which the output changes from a low state to a high state.
- **Noise Margins**: The voltage ranges that define the tolerance for noise. The low noise margin is the range between Vil and Vol, while the high noise margin is the range between Vih and Voh.

### DYNAMIC CHARACTERISTICS

- **Propagation Delays**: The duration required for the output to respond after a change in the input.
- **Rise Time (tr)**: The time it takes for the output to move from the low voltage level (Vol) to the high voltage level (Voh).
- **Fall Time (tf)**: The time it takes for the output to move from the high voltage level (Voh) to the low voltage level (Vol).

  ## CMOS FABRICATION PROCESS
 ### Creating active reagion for transistors
![Screenshot (64)](https://github.com/user-attachments/assets/5f3f6044-7eaa-4f84-8e96-bde0493963d1)

  ### Formation of Nwell and Pwell
![Screenshot (65)](https://github.com/user-attachments/assets/3fff703e-0426-4c9f-b44f-c044a81d5a3d)

  ### Formation of 'gate' terminals
 ![Screenshot (66)](https://github.com/user-attachments/assets/d2450c55-6f64-4a55-a750-4b47b12e4c1f)

  ### Formation of LDD
 ![Screenshot (67)](https://github.com/user-attachments/assets/f86db4c6-ec68-43d6-b016-c8cb4477615f)

  ### Source and Drain formation
 ![Screenshot (68)](https://github.com/user-attachments/assets/a8d4f1a1-7f06-42b3-98e2-a0ee80df4103)

  ### Formation of contacts and interconnect
 ![Screenshot (69)](https://github.com/user-attachments/assets/d64a302d-e30d-4b85-a6a1-4431809cf5ea)

  ### higher level metal formation
 ![Screenshot (70)](https://github.com/user-attachments/assets/98e4c135-7f74-45bf-bdb9-4be24ffa44f4)

 # DAY 3 (Labs)
 </p> First, we modified the IO PINS of the macro in the floorplan DEF file as shown in the image below. Then, we reran the floorplan and observed the changes. </p>
 set ::env(FP_IO_MODE) 2
</p> after making changes in floorplan def file that the pins are no more equidistant. </p>

![Screenshot (77)](https://github.com/user-attachments/assets/039be199-08f0-4a88-8b68-32b81bf74b47)

 ## GIT CLONE THE "vsdstdcelldesign"
#### Go to Openlane directory and use the following command:
    git clone <url of the github repo you want to clone>
    git clone https://github.com/nickson-jose/vsdstdcelldesign.git
![WhatsApp Image 2024-08-02 at 11 30 50 PM](https://github.com/user-attachments/assets/fa084127-8b0f-4870-838c-587dbcd36f1c)

 ![WhatsApp Image 2024-08-02 at 11 30 51 PM (1)](https://github.com/user-attachments/assets/a01a873e-4723-4b57-b5f4-ffda9aa1bcac)
 ##### From the above image, we can see that the cloning was successful. Next, we will open the 'mag' file, which requires the 'tech' file located in the following directory:</p>
       vsduser@vsdsquadron:~/Desktop/work/tools/openlane_working_dir/pdks/sky130A/libs.tech/magic$ 
 ##### so first we copy that file here, by using the following command:
       cp sky130A.tech /home/vsduser/Desktop/work/tools/openlane_working_dir/openlane/vsdstdcelldesign
 ##### It is copied successfully. Now, open the mag file magic
       magic -T sky130A.tech sky130_inv.mag &
  
 ![WhatsApp Image 2024-08-02 at 11 30 51 PM (3)](https://github.com/user-attachments/assets/f9b8c54c-b388-45bb-a249-a80819ede81b)
 
  ![WhatsApp Image 2024-08-02 at 11 30 51 PM (2)](https://github.com/user-attachments/assets/d4d6c544-69dc-4085-81f6-7a3f87176eae)

## TO EXTRACT THE NETLIST IN MAGIC
    % extract all
    % ext2spice cthresh 0 rthresh 0
 
![WhatsApp Image 2024-08-02 at 11 30 51 PM (9)](https://github.com/user-attachments/assets/5bfedf57-7ec3-4c54-880a-ec6a2d5f17f0)

![WhatsApp Image 2024-08-02 at 11 30 51 PM (7)](https://github.com/user-attachments/assets/ec669143-01d9-42da-95f4-96a35cd09fae)

</p> Now, lets open the created spice file:

![WhatsApp Image 2024-08-02 at 11 30 52 PM (8)](https://github.com/user-attachments/assets/19abd143-750e-48d8-b612-2798c43adef1)

</p> Now the next step is to run the SPICE file in ngspice tool by using command ngspice sky130_inv.spice </p>

![Screenshot (73)](https://github.com/user-attachments/assets/0ea430ff-b34d-4ced-941e-ae8951f3687e)

#### Inverter Characterization using Sky130 Model Files
In this lab, we will characterize an inverter using ngspice and Sky130 model files, aiming to extract key parameters from the simulation results.

**Parameters to Characterize:**

1. **Rise Time:**
   - Definition: The time taken for the output waveform to transition from 20% to 80% of its maximum value.
   - Data Points: 
     - \( x_0 = 6.16138 \times 10^{-9} \) s, \( y_0 = 0.660007 \)
     - \( x_1 = 6.20366 \times 10^{-9} \) s, \( y_1 = 2.64009 \)
   - Calculation: 
     - Rise time \( = x_1 - x_0 = 0.0422 \) ns

2. **Fall Time:**
   - Definition: The time taken for the output waveform to transition from 80% to 20% of its maximum value.
   - Data Points: 
     - \( x_0 = 8.04034 \times 10^{-9} \) s, \( y_0 = 2.64003 \)
     - \( x_1 = 8.06818 \times 10^{-9} \) s, \( y_1 = 0.659993 \)
   - Calculation: 
     - Fall time \( = x_1 - x_0 = 0.0278 \) ns

3. **Propagation Delay:**
   - Definition: The time taken for a 50% transition at the output (0 to 1) corresponding to a 50% transition at the input (1 to 0).
   - Data Points: 
     - \( x_0 = 2.18449 \times 10^{-9} \) s, \( y_0 = 1.64994 \)
     - \( x_1 = 2.15 \times 10^{-9} \) s, \( y_1 = 1.65011 \)
   - Calculation: 
     - Propagation delay \( = x_1 - x_0 = 0.034 \) ns

4. **Cell Fall Delay:**
   - Definition: The time taken for a 50% transition at the output (1 to 0) corresponding to a 50% transition at the input (0 to 1).
   - Data Points: 
     - \( x_0 = 4.05432 \times 10^{-9} \) s, \( y_0 = 1.65 \)
     - \( x_1 = 4.05001 \times 10^{-9} \) s, \( y_1 = 1.65 \)
   - Calculation: 
     - Cell fall delay \( = x_1 - x_0 = 0.0043 \) ns
## INTRODUCTION TO SKY130 PDK
### Now us the follwoing command to download the Lab files while being in the home directory :
    sudo wget http://opencircuitdesign.com/open_pdks/archive/drc_tests.tgz

![WhatsApp Image 2024-08-02 at 11 30 52 PM (1)](https://github.com/user-attachments/assets/91f43ef9-04ba-4519-9b83-ba97fafe940c)

### Now that you have downloaded the zip file, use the following command to extract the lab files:
    sudo tar xfz drc_tests.tgz
    
![WhatsApp Image 2024-08-02 at 11 30 51 PM](https://github.com/user-attachments/assets/d2209281-c0ba-4461-83e7-38f8f70e8f00)




 


 

 








 
  





      



 
 
 




