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

#### **Aspect Ratio = (Height of the core / Width of the core)**
![Screenshot (51)](https://github.com/user-attachments/assets/b869917d-fe89-4724-96de-cfcb96cff284)

#### **Utilisation Factor = (4 sq units)/(4sq units) = 1**
#### **Aspect Ratio = (2 units)/(2 units) = 1 i.e core has Square Shape**


      



 
 
 




