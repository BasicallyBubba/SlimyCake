![Intro-GIF](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro-GIF.gif) 

# SlimyCake
Very delicious Cheesecake. Designed by [Sorakage](https://github.com/Sorakage033/SlimeVR-CheeseCake) <br>
Repo tidied up and reworded a bit by BasicallyBubba
<br>
# OverView
CheeseCake is a Lighter, smaller, prettier, and better IMU-based full-body tracking solution based on SlimeVR 
With 8-port charging dock, eliminating wiring and storage troubles!
Designed by Sorakage 
<br>
 
# CAUTION：   <br>
**When you place an order in JLCPCB, remember change the PCB thickness to 1mm!**    
    
**Before flashing the firmware, the board must be connected to the battery.**    
This design removes the protection diode (to prevent Li-po battery overcharged while uploading firmware), and USB-5V is supplied to the battery via the on-board charging chip TP4057.    
**The on-board charger will not output voltage without connected to the battery.**    

## Extra Info:      
Modifications are welcome and encouraged!         
If you do, it would be great if you can credit the creator with [\[This LOGO\]](999-PictureFiles/SK-LOGO.png)     


## Index
- [Components](#Components)
- [Versions](#Versions)
- [Printing](#Printing)
- [Assembly](#Assembly)
- [Support Link](#Support)



## Components 
For the CheeseCake you will need the following components:   
- PCB produced by JLC PCBA   
- 3D Printed Parts   
- 38 or 40mm straps   
-   Li-po Battery (803035 800/900mAh or 903035 1000/1200mAh are ideal)
    -   **If you use a different cell, ensure the battery is no larger than 9mm in depth, 30mm in width, and 35mm in height to fit the case.**
    -   **Verify the battery dimensions with the seller before purchase. Some sellers list 803035 batteries that go very slightly over the listed dimensions.**
- Pogo Pins (For trackers with no AUX port) [\[More Info\]](001-‘’Cheese‘’/POGOPIN%20purchase%20Link.txt)
- Soldering Iron/Station 



## Versions
There are 4 different flavors of tracker in this project:  
- [Cheese](#Cheese)
- [Choco](#Choco)
- [Blueberry](#Blueberry)
- [RareCheese](#RareCheese)


### Cheese
This tracker has two variants:
The original BMI160 variant
And a slightly revised version designed for the BMI270

Both of these variants include gerbers for the regular tracker, as well as versions that include an AUX header.

<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro-3D_160.png?raw=true" width="30%">   


### Choco
This is a variant of the Cheese that expands it slightly to fit a BNO 085 module
This includes both the regular tracker and a version that includes the AUX header.


<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro-3D_Special%20remake.png?raw=true" width="30%">    



### ChocoRemix  
This is a version of the Choco that includes a DC-DC buck converter
This includes a regular tracker and a version with the AUX header

NOTE: This version does not have PoGo Pins!

<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro-3D_Special%20remake_DCDC.png?raw=true" width="30%">      

This might be the best CheeseCake ever. To extend the battery life, it have some magic in it:    
DC-DC Buck Power Supply, which can save up to 18% of power consumption (in 4.2V,LDO need 90mA, but DC-DC only need 74mA).    
And in order to improve signal quality over long distances, leave some Keep-out area at ESP-12F's antenna.    
While using this version, the code in ``define.h`` must be change to:      
```
    #elif BOARD == BOARD_NODEMCU || BOARD == BOARD_WEMOSD1MINI
      #define PIN_IMU_SDA D2
      #define PIN_IMU_SCL D1
      #define PIN_IMU_INT D5
      #define PIN_IMU_INT_2 D6
      #define PIN_BATTERY_LEVEL A0
      #ifndef BATTERY_SHIELD_RESISTANCE
        #define BATTERY_SHIELD_RESISTANCE 0
      #endif
      #ifndef BATTERY_SHIELD_R1 
        #define BATTERY_SHIELD_R1 10
      #endif
      #ifndef BATTERY_SHIELD_R2
        #define BATTERY_SHIELD_R2 47
      #endif    
```      


### Blueberry
This is a variant that uses an LSM6DSV16XTR tracker
This provides better performance than a BNO while being slightly cheaper than a BNO 085

<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro-3D_LSM6DSV%20‘’Blueberry‘’.png?raw=true" width="30%">      


### RareCheese
This is a variant that uses an ICM-42688 tracker 
This is mostly experimental from Bubba's understanding
This has an external oscillator, an AUX header, and a DC-DC buck converter
<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_ICM42688“RareCheese”.png?raw=true" width="30%">          

All Japanese love Rare CheeseCake a lot, I love it too.      
And I hope you can also like it.    



### AUX MODULE - SK-MOD       

<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_SK-BMI270.png" width="30%"><img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_LSMMOD.png" width="30%"><img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_ICMMOD.png" width="30%">      
Including 3 different MOD: BMI series, LSM6DSV series and ICM-42688(with External Clock)

```
In SK-BMI MOD, the default IMU on BMI MOD is BMI270, but you can change it to BMI160/BMI323 or other IMUs at PCBA page.
```
It can be soldered on 「Choco」SpecialRemake directly or connect to the AUX port through ``JST 1.25mm 5pin`` like pic below:      
Note: the two connectors are MIRROR      
<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_CONN_sample.png?raw=true" width="100%">       
- **Notice:If you want to use it both solder it on Choco-SpecialRemake and use as AUX, I recommend order JST connector separately and soldering them on by yourself.**       
- **With AUX connector it too thick to fix acrylic top lid, or you need to carve a groove in the corresponding position of the 3D print top lid.**    

And the DEG of this module is fixed to ``DEG_0`` when installed on 「Choco」SpecialRemake or Y axis towards up.        

Also, if you want to upgrade your SlimeVR but not using 「Choco」SpecialRemake, it has a smaller version of SK-BMI270:     
<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_SK-BMI270_Smol.png?raw=true" width="25%">
<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_LSMMOD_Smol.png?raw=true" width="25%">
<img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_3D_ICMMOD_Smol.png?raw=true" width="25%">      
Though it has a smaller size, if it was soldered on 「Choco」SpecialRemake, it looks a little bit unbalance.      


## 3D Printing for SlimeVR-CheeseCake

This repository contains various 3D printed components required to assemble the SlimeVR-CheeseCake. Below are the necessary files and instructions.


### CheeseCake Case
- **Main Case**: [CheeseCake Case with AUX](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/001.2-Chocolate-Case-With-AUX.stl) - Recommended design compatible with any 3D filament.
- **Alternative Designs**:
  - [Case with USB Port Only](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/001.3-Chocolate-Case_TypeC-Only.stl)
  - [Case with Pogo Pins Cutout](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/001.1-Chocolate-Case.stl)    
- If you want a larger battery, you can use the [803040-case](https://github.com/Sorakage033/SlimeVR-CheeseCake/tree/main/004-3D%20Print%20Model/000.1-Blue-Compact-Case-For-803040-Bat) modified by Blu3u.


### Top Lid
- **3D Printed Option**: [3D Printed Top Lid](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/002-Cake-Top.stl)
- **Acrylic Option**: For a 4mm transparent acrylic lid, use the dimensions provided in [this file](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/AcrylicTop-CutSize-Thickness4mm.png).


### Essential Component
- **Switch Component**: [Switch for Case](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/003-SW.stl) - This part is crucial for the assembly.
- Note: If it's hard to assemble, you can try narrowing the switch by scaling down the Z-axis.


### Holders (Recommended to Print in PETG Filament)
- [Clamp Holder](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/004-''CLAMP''Holder.stl)
- [GoPro Chest Harness Compatible Clamp Holder](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/004-1-''CLAMP''GoPro_Holder.stl) - For GoPro chest harness compatibility.
- [Slide Holder](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/005-''SLIDE''Holder.stl)


### Charging Dock (Recommended to Build the Type-C ChargeDock)

- **8-Tracker Type-C ChargeDock**     
  <img decoding="async" src="https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/999-PictureFiles/Intro_Type-c%20Charging%20Dock.png?raw=true" width="40%">
  - [Top Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-8port-Typec-Top.stl)
  - [Bottom Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-8port-Typec-Bottom.stl)
    
- **8-Tracker ChargeDock**:
  - [Top Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-8port-Top-Optimized.stl)
  - [Bottom Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-8port-Bottom-Optimized.stl)
    
- **6-Tracker ChargeDock**:
  - [Top Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-6port-Top.stl)
  - [Bottom Part](https://github.com/Sorakage033/SlimeVR-CheeseCake/blob/main/004-3D%20Print%20Model/ChargeDock-6port-Bottom.stl)


## Assembly    
    
1.  Apply about 2cm foam tape on the inner side of the case (with M2*7mm hexagonal spacers installed by a HAMMER or whatever)      
<img decoding="async" src="https://raw.githubusercontent.com/Sorakage033/SlimeVR-CheeseCake/main/999-PictureFiles/A-01.png" width="80%">     
2.  Place the switch part in position and affix the battery to the case.
<img decoding="async" src="https://raw.githubusercontent.com/Sorakage033/SlimeVR-CheeseCake/main/999-PictureFiles/A-02.png" width="80%">    
3.  Bend the battery wire to ensure it can be tucked into the reserved gap during installation.    
<img decoding="async" src="https://raw.githubusercontent.com/Sorakage033/SlimeVR-CheeseCake/main/999-PictureFiles/A-03.png" width="80%">    
4.  When installing the PCB, put the switch to the "UP" position, tilt it towards the side with the switch. Fit it into the reserved slot on the 3d printing part.    
<img decoding="async" src="https://raw.githubusercontent.com/Sorakage033/SlimeVR-CheeseCake/main/999-PictureFiles/A-04.png" width="80%">    
5.  Tilt the board slightly towards the USB-C side, push the PCB at the side away from the switch.    
<img decoding="async" src="https://raw.githubusercontent.com/Sorakage033/SlimeVR-CheeseCake/main/999-PictureFiles/A-05.png" width="80%">     
6.  Press the whole PCB at position, screw on M2*5mm screws.      

      
## Support
If this project can help you I would be very happy!      
And also, if you want to give me some support, you can support me on [BOOTH](https://sorakage033.booth.pm/items/4859476)!


## Tier List
Generally speaking, BNO and LSM are the best tracker modules
BMI 270 is the good middle-of-the-road option as it is cheaper and better than the BMI160


From: menacingexiler on Discord

My tier list for best IMU

-------------------------
No magnetometer best quality tier list
S tier: LSM6DSV ¹ ², BNO085
A Tier: BMI270 ¹ ² ³
B Tier: BMI160 ³
C Tier: BMI323 ¹ ², BNO055
D Tier: ICM-20948
E Tier: MPU6050/MPU6500, MPU9250/GY-87
Unknown (Experimental): ICM-42688¹ ²


--------------------------
No magnetometer best value tier list
S tier: BMI270¹ ² ³
A Tier: BMI160³, LSM6DSV¹ ²
B Tier: BNO085
C Tier: BMI323¹ ², ICM-20948
D Tier: MPU6050/MPU6500, BNO055, MPU9250/GY-87
Unknow: ICM-42688¹ ²


Reference: Mocopi uses BMI270. SlimeVR and HaritoraX uses BNO085.

Note:
    1. No breakout board.
    2. Experimental
    3. Manual calibration results

