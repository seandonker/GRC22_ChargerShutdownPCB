# GRC22 Charging Shutdown Board for Guelph's FSAE Club
This board lies inside the external charging enclosure and is responsible for processing certain safety signals.
It then determines if it is safe to activate the battery charger or not. 

**Schematic Theory**<br>
The board takes in three main safety signals: IMD Error, AMS Safety, and Charger Safety. IMD Error indicates the insulation in between the cells of the battery pack 
and the signal faults low when an error is detected. AMS Safety faults low as well when there is an issue with the voltage/temperature/current of any individual cell bank in the battery. Finally, 
charger safety sinks current when no error is present and is allowed to float when an error occurs. The latching logic is the core design challenge of this board. 
The FSAE rulebook has specific descriptions relating to the IMD and AMS signals as once an error is noticed, the output of the board must stay in the error state until 
manually reset (power cycled). This is why latches are required to save the error state. Two RS latches were implemented in combination with RC filters, AND gates, and inverters.
This was done to combat unknown input signal conditions on startup. A full input/output-state circuit trace can be seen in the provided files (ShutdownBoard_Latching_Logic_States).
The relay logic section acts as a chain of switches, so only if  the charge sink, IMD, AMS, E-stop, and interconnect states are all correct, will then the charger and accessories be provided power.

**Board Layout**<br>
The main requirement for the PCB layout was to be able to manufacture on a two layer PCB for cost reasons. The criteria for design were ease of assembly, connector and fuse access,
and the visibility of the indicator LEDs and silkscreen. 

![schematic_view](https://github.com/seandonker/GRC22_ChargerShutdownPCB/assets/121892380/c5509ead-92f0-48ef-ae6f-bcc06bd44765)

![3d_Viewer](https://github.com/seandonker/GRC22_ChargerShutdownPCB/assets/121892380/c06da93d-f1b3-417a-b285-1ea7e30684b8)

![PCB_Layout](https://github.com/seandonker/GRC22_ChargerShutdownPCB/assets/121892380/980a0588-6bd1-4636-a8bd-1b7a37d400d1)
