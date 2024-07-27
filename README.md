# _NASSCOM_VSD_SOC_Design
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
![aurdino image](https://github.com/user-attachments/assets/934167cc-feb3-4af0-bec9-a891b39d8f1c)

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

  


 
 
 




