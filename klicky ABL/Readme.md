## Klicky On Flatpack

#### NOTES
- Since the Z on this printer moves, if you power off the printer at anywhere but Z0, the hotend wont be able to grab the probe  
as it uses it to home Z I havent found a solution yet so let me know if you have any ideas  
- You lose a tiny bit of build volume  


### 1. Printed Parts
 - You need 3 parts for this
 - The **duct**, the standard **probe holder**, and the **probe dock**
 - All 3 parts should be printed in asa or abs as they are near the hotend and bed  
  
    **Duct:**
    - The duct has 3 holes for magnets which you need to press wires into, just the 2 connected to the switch,  
and then you need to trim a hole in the duct for the wires to run out past the fan  
    - Then, you need to run the wires back to the motherboard using the cable sleeving  
    - The duct just mounts like normal with 2 M3 Screws  
    
    **Probe Holder:**
    - The probe holder is just the standard Klicky probe holder 
    - You screw the limit switch in and attach the 3 top magnets 
    - Do not attach the one on the side as its not needed because the probe docks backwards
    
    **Probe Dock:**
    - The probe dock uses 1 magnet and 2 m3 screws
    - It mounts on the 1515 extrusion that has the top y linear rail on it beside the bed
    - It is at X2 Y114 or Y0 (Depending on your setup) roughly
    
### 2. BOM
 What you will need:
 - 4 6x3 Magnets
 - 1 Omron D2F-5
 - 2 STEEL M2 Screws (They need to stick to the dock magnet as the probe is backwards)
 - Wire
 - Super Glue (If necessary)
 - 2 M3x8 Screws 
 - 2 M3 Nuts
 - 1 Heated Insert for Duct
 
 ### 3. Assembly
  - Assemble the Klicky probe by putting the 3 magnets in the top and screwing the limit switch in
  - Insert the 3 Magnets into the duct along with 2 wires on the left and right magnets so the switch can work (I recommend testing continuity with them)
  - Trim a small hole in the end of the duct to allow the wires to come out, on the right side of the fan
  - Route the wires to the motherboard and attach them to z stop or a probe pin (I use z stop)
  - Attach the one magnet into the probe dock and use the 2 M3 screws and nuts to attach it to the 1515 extrusion that is where the y belt tensioner is
  - Move flatpack manually until you find the coordinates of the klicky probe, Mark them down (For me they are Z12.62 Y6 X2)
  **Thats It!! Assembly for Klicky is done**
  
  ### 4. Firmware
Instructions based on Marlin 2.1.2.1
    If you are using Klipper, there are guides online  
    Used this as a reference https://www.youtube.com/watch?v=egWpvaTsl10  
    - **Configuration.h**  
        - Uncomment #define Z_MIN_PROBE_USES_Z_MIN_ENDSTOP_PIN  
        - Uncomment #define FIX_MOUNTED_PROBE  
        - Uncomment #define NOZZLE_TO_PROBE_OFFSET { 21.4, -11.4, -10.75} (Those are my offset values in order of XYZ)  
        - Set #define PROBING_MARGIN to 15  
        - Set #define Z_CLEARANCE_DEPLOY_PROBE 0 and #define Z_CLEARANCE_BETWEEN_PROBES 5  
        - Make sure #define Z_PROBE_LOW_POINT is set to -5   
        - Uncomment #define RESTORE_LEVELING_AFTER_G28  
        - Uncomment #define LCD_BED_LEVELING  
        - Uncomment #define Z_SAFE_HOMING  
        - Uncomment #define AUTO_BED_LEVELING_BILINEAR  
        - If you want, you can uncomment this to test your mesh #define G26_MESH_VALIDATION  
        - Set  #define GRID_MAX_POINTS_X to 5  
    - **Configuration_adv.h** 
        - These are all your macros for abl, you may have to change the values depending on where your mount is  
        - Here are my custom macros:   

> ; Macros
> ; M810 Home XY  and deploy probe
> M810 G28 XY|G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 Y25 Z12.62 F2400
>
> ; M811 Home XYZ and stow probe
> M811 G28 XYZ|G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 X50 Y6 Z12.62 F2400
> 
> ; M812 Stow probe without homing
> M812 |G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 X50 Y6 Z12.62 F2400
> 
> M117 Macros Loaded

- Uncomment #define STARTUP_COMMANDS and put your macros like this (in one line, seperated by \n and in quotes)
**"M810 G28 XY|G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 Y25 Z12.62 F2400**
>    \nM811 G28 XYZ|G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 X50 Y6 Z12.62 F2400
>    \nM812 |G1 Z12.62|G1 X2|G1 Y11 F2400|G1 X2 Y6 Z12.62 F1200|G1 X50 Y6 Z12.62 F2400"
   - Uncomment #define GCODE_MACROS
   - Set #define GCODE_MACROS_SLOT_SIZE to 150
   - Uncomment #define CUSTOM_MENU_MAIN 
   
## These are my menu Items :
> // Custom Menu: Main Menu
> #define CUSTOM_MENU_MAIN
> #if ENABLED(CUSTOM_MENU_MAIN)
> #define CUSTOM_MENU_MAIN_TITLE "Klicky Probe"
> //#define CUSTOM_MENU_MAIN_SCRIPT_DONE ""
> #define CUSTOM_MENU_MAIN_SCRIPT_AUDIBLE_FEEDBACK
> //#define CUSTOM_MENU_MAIN_SCRIPT_RETURN   // Return to status screen after a script
> #define CUSTOM_MENU_MAIN_ONLY_IDLE         // Only show custom menu when the machine is idle
>
> #define MAIN_MENU_ITEM_1_DESC "Deploy Probe"
> #define MAIN_MENU_ITEM_1_GCODE "M810"
> //#define MAIN_MENU_ITEM_1_CONFIRM          // Show a confirmation dialog before this action
>
> #define MAIN_MENU_ITEM_2_DESC "Stow Probe" 
> #define MAIN_MENU_ITEM_2_GCODE "M811"
>  //#define MAIN_MENU_ITEM_2_CONFIRM
>
> #define MAIN_MENU_ITEM_3_DESC "Stow Probe Without Homing"
> #define MAIN_MENU_ITEM_3_GCODE "M812"
> //#define MAIN_MENU_ITEM_3_CONFIRM
>
> #define MAIN_MENU_ITEM_4_DESC "Deploy and Home"
> #define MAIN_MENU_ITEM_4_GCODE "M810\nG28 Z"
> //#define MAIN_MENU_ITEM_4_CONFIRM
>
> #define MAIN_MENU_ITEM_5_DESC "Deploy and Probe Bed"
> #define MAIN_MENU_ITEM_5_GCODE "M810\nG28 Z\nG29"
> //#define MAIN_MENU_ITEM_5_CONFIRM
> #endif
        
   - You can also use an sd card to run the commands on startup, but I like to use eeprom to store them
   - I'd reccomend watching teaching techs video on this, as it goes into more detail
        
   **Thats all! You can now put these commands in your start gcode and it will probe automatically
   Message me if you have any questions :) **
   

Start Gcode:   

M810
G28
G29
M812
G1 Z+30 F1500
G1 Z15.0 F6000 ;Move the platform down 15mm
G92 E0

