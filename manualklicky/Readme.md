## manualklicky for Flatpack

**manualklicky** for Flatpack is a project i designed, to NOT lose any space in the already small buildvolume of flatpack.  
Problem being of course, that this has a manual component; it is still technically ABL though.  
(ABL = automated bed leveling)  
The idea was of course 100% influenced by Klicky, but shares no parts with it. (because it wont fit. ;) )  
THIS IS STILL A WIP !!! THE PART MISSING IS ADDING THE PROBE TO THE FIRMWARE !!!
  
### Description:  
- on the proper klicky you have to move your printhead outside your buildvolume to get to the klickyprobe  
- on flatpack, we use every mm of our buildvolume, and i decided to not give that away for a ABL probe  
- so, you can start the ABL-probing, but have to remember to add the probe before you do that, AND have to remember to take it off after probing  
- the idea behind klicky is that the magnets job is not only to connect the probe in place, but to also provide the electric connection for the actual probe. This is ofc here exactly the same.
#### Note:  
- if you dislike any manual interaction for ABL-probing, you can use **Klicky for flatpack**,which Awesomeka designed and provided for the GitHub, and which you find here under the folder with the same name   
  
### 1. Printed Parts  
- you need to switch out one part, and print two new parts  
- the part you have to switch out, is the **hotendfan+partcoolingassembly vx.3mf"** for the variant with "manualklicky-" in front  
- apart from that you have to print two new parts: **manualklicky-mount.3mf", which is the magnetic mount or dock, you have to install on the front of the printer, and  
**manualklicky-main.3mf**, which is the part that holds the actual probe  

### 2. BOM  
You need:  
- 7x 6x2 neodym magnets  
- 4x heated inserts in M3 (M3 X D4.6 X L3.0 is ideal, just like on the main BOM), all needed for the **hotendfan+partcoolingassembly** part you switch out  
- 1x Omron D2F-5 (or any other microswitch that has the same measurements)  
- wires ofc  
- glue for glueing the magnets to the plastic. I also like to give the cables a dot or two so they stay where they are  
- 1x M3x5 or M3x6 screw  
- 1x M3 T-Nut for 1515, OR 1x M3 Nut  
- a roughly 2mm thick self-adhesive feltpad; this is used for gliding along the x-axis and making sure the probe transfer all forces to the x-extrusion on every probing

### 3. Assembly
- if you have already printed the **hotendfan+partcoolingassembly.3mf**, you need to reprint the "manualklicky-" version, and add the heated inserts to that
- after you have done that, you want to add 3 6x2mm neodym magnets, maybe with glue if that doesnt hold well
- two of the 6x2 magnets need you to add wire to the back, you know which by the channels in the back
- print the **manualklicky-main.3mf**, screw the omron microswitch to it, and add the magnets. Again, for two of the three magnets you need to connect wire to the magnets
- the Probe has a mount designed to be docked/mounted on the front right. Print that, put the magnets in, and simply screw it onto the front top extrusion. The probe is hold  
in place there by magnets, just like on the head.

### 4. Instructions
- i dont have any instructions on how to add this to Marlin or Klipper yet. 

### Screenshots
![image](https://github.com/eponra/flatpack/assets/66600478/78b35a6e-ea56-4f63-98cc-964a63751631)
![image](https://github.com/eponra/flatpack/assets/66600478/ace18b7e-3422-4c96-8d8c-15b54a02445f)
![image](https://github.com/eponra/flatpack/assets/66600478/618e20a7-8edf-43ca-bfca-28c1676c793a)
![image](https://github.com/eponra/flatpack/assets/66600478/9e9ecbf9-37b7-4a25-8b06-40abed9198a3)
![image](https://github.com/eponra/flatpack/assets/66600478/bd96024e-af9e-48c1-81dc-a8b8d6352a87)

