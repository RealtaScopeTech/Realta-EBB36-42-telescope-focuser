Todo: Better blurb at start

Todo: need to add #define FLASH_BANK_NUMBER	FLASH_BANK_1 to file C:\Users\willi\AppData\Local\Arduino15\packages\STMicroelectronics\hardware\stm32\2.3.0\variants\STM32G0xx\G0B1C(B-C-E)(T-U)_G0C1C(C-E)(T-U)\variant_EBB42_V1_1.h

Todo: Visual studio won't let you compile unless you right click two .resx and click "unblock".

Todo: Installing ASCOM driver

Todo: How to use with ASCOM.

Todo: Double check hex bolt sizes.


# Realta Scope Tech EBBfocuser

![EBB36 Focuser Case](Guide/Images/EBB36FinishedRCA.png)


## Project goals.

+ Truley open source code i.e. do what you want with it.
+ Using open hardware only i.e. schematic available.
+ Firmware created using Arduino IDE with full guide to get it working with the EBB.

## What you need to buy.

### Stepper motor

I have used a 23mm thick Nema 17 stepper motor like this 17HS4023. 

![Nema 17](Guide/Images/17HS4023.png)

However, any NEMA stepper motor thicker than this will work but you are limited to 1.5A per phase by the EBB36 stepper motor driver. Even thinner motors will work but you will have a hard time mounting them as the case will foul most mounting brackets. The FreeCAD file containing the parts is included in this repository so can be edited to provide a spacer to pad out the difference in width if needed. 

### BigTreeTech EBB36 

There are two versions of this, one with an accelerometer and one without, both will work but the accelerometer version is twice as expensive and no use of it is made in this project. 

![EBB36 Focuser PCB](Guide/Images/EBB36PCB.png)

### Note about the EBB42

Originallt this project was built around the EBB42 kit sold by big tree tech however we changed the design to use the EBB36 for two reasons; 

1) The PCB is smaller allowing for a smaller sized case and
2) The power connector while smaller is of a more common type so should be easier to source replacements for.

All of the software provided here will work just fine with the EBB42 but you will need to design your own case for it.

### M3 Hex bolts

To secure the EBB36 you will need 4 25mm long M3 bolts and 2 5mm M3 bolts while the ones for the stepper motor depend on how thick the one you buy is. The original bolts will not reach through the combined thickness of the case and motor so you will need 2 replacement ones. I found that for the 23mm thick motor I could use 22mm long bolts.  

### Optional: Crimping tools and ferrules

The EBB36 focuser comes with all the accessories you need to connect it up, it comes with all the cable fittings needed. However you will need to crimp these onto the wires yourself and a dupont or similar crimping tool greatly helps.

![Dupont crimping](Guide/Images/DuPontCrimping.png)

However it is possible to crimp using Needle Nose Pliers. 

[![Needle Nose Pliers](http://img.youtube.com/vi/JsoqBS1-k7M/0.jpg)](http://www.youtube.com/watch?v=JsoqBS1-k7M "Needle Nose Pliers")

It can also be a good idea to use ferrules for terminating the dew heater wires used in the screw terminals.

![Dupont crimping](Guide/Images/FerruleCrimping.png)

One kit will get you enough connectors to last a lifetime. 

## What you need to 3D print.

The parts are designed to be printed easily on a printer using a 0.8mm nozzle so should be easy prints on any printer using a smaller nozzle. 

![Printer](Guide/Images/3DPrintBed.png)

The bottom section of the case needs supports to print well, I used the support paint tool and the smart fill option to select the faces needing supports using Prusa Slicer.

![Needs supports](Guide/Images/NeedsSupports.png)

### Notes on filament type.

Stepper motors will get warm when operating and even when not moving they are being held in place by powered magnetic fields. They are designed to cope with very very high temperatures. The firmware provided does make use of the TMC2209's CoolStep technology which greatly lowers the current drawn when not moving however the motor will still get warm to the touch, around 40c to 50c is common. This means you really should think twice about using a filament such as PLA which will start going floppy around this temperature. PETG would be better but ABS or ASA would be best. 

## Assembling the case.

![Exploded](Guide/Images/EBB36Exploded.png)

In this section we will cover the step by step assembly of the motor and case

### Shorten the stepper motor wires

The stepper motor you purchased probably came with a four wire cable with red, blue, green and black cables. However this cable will be far too long. It needs to be shortened to 70mm and this will require either cutting and resoldering the wires or recrimpling the connectors, most motors that are available on the webb will either have fixed wiring at the motor end or use a wider 6 pin connector, in the case of two connector motors measure from the larger connector as the EBB36 PCB kit will come with spare connectors and housings.

Stepper motors like these are designed to work with four wire two phase motors. The phases for the motor will be named A and B and a pair of wires will be used with each phase, the documentation for your stepper motor will sometimes tell you which colour wires go with each phase but there appears to be no standard colours for wiring so you should test the wires to see which go together if possible. To do this you can use a multimeter as matching pairs will show continuity.

https://www.youtube.com/watch?v=UI86W26lgl0

If you can't test the wires its not the end of the world if they get mixed up the motor will just jitter around and move ineffectively and you just need to swapped two of the wires around in the connector housing.

![Printer](Guide/Images/MotorPinPhases.png)

The image above shows how the EBB36 PCB expects you to connect the phases, it doesn't matter that you connect AA from your motors documentation to AA on the header just that you keep both wires of each phase seperate from the others, swapping the order just reverses the direction of movement. The cables that came with my stepper motors had the pin order ABAB so I had to flip the two middle wires over.

### Remove two screws from the stepper motor

The case is mounted to the stepper motor using its own case mounting screws just using the longer replacement ones discussed earlier. The two screws that need removing are shown below. 

![Insert Nema 17](Guide/Images/RemoveStepperScrews.png)

### Insert NEMA 17 stepper motor

The stepper motor will fit into the bottom half of the case when inserted at an angle.

![Insert Nema 17](Guide/Images/InsertNema.png)

Make sure its wires are connected and to feed them through to the other side of the case.

Mount the case using the repacement bolts as shown below

![Screw Nema 17](Guide/Images/screwNema.png)

Do not over tighten these (or any other bolts) just a moderate hand tighting will do.

### Postion Face Plate

The case face plate needs to be positioned over the USB-C port and power connector before fitting to the case.

![Postion Face Plate](Guide/Images/FacePlate.png)

![Postion Face Plates](Guide/Images/FacePlate2.png)

### Fit EBB36 PCB

![Fit PCB](Guide/Images/ScrewPCB.png)

### Insert motor wire connector

The wire connector from the motor can now be connected to the PCB as shown below.

Todo: Picture goes here!

### Fit top of case

Use two 10 mm hex bolts to screw the PCB into position. Do not over tighten.

![Fit PCB](Guide/Images/ScewTopCase.png)

## Setting up the Arduino IDE for use with EBB36.

### Install the Arduino IDE.

The latest Ardunio IDE can be found here.

https://www.arduino.cc/en/software

When you start the IDE for the first time you will be asked to allow it access to the internet, please allow it to do this as it will download various drivers and you will need this functionality later on to install some libaries. 

### Add additional Boards Managers URLs

The EBB36 doesn't use a microcontroller of a type used by any of the boards supplier by Arduino so we need to download additional board definitions. This can be done using the Arduino IDE itself. 

Go to file -> preferences and add stm32duino

![Board manager](Guide/Images/ArduinoPreferences.png)

and add https://github.com/stm32duino/Arduino_Core_STM32/wiki/Getting-Started to the "additional Boards Managers" section at the bottom. Wait for the definitions to download

### Edit the configuration

As at the time of writing this guide (June 2024) the board definitions for the EBB36/42 do not allow you to use the micro controllers flash memory, not sure why this is as all thats needed is a simple configuration change. 

You need to use file explorer to go open a file in the following impossibly long directory

"%LocalAppData%\Arduino15\packages\STMicroelectronics\hardware\stm32\2.3.0\variants\STM32G0xx\G0B1C(B-C-E)(T-U)_G0C1C(C-E)(T-U)"

The file that needs editing is variant_EBB42_V1_1.h, its likely your PC doesn't have an application associated with this file type but its really just a text file so can be opened just fine in notepad.

![Board manager](Guide/Images/ChooseAnotherApp.png)

![Board manager](Guide/Images/NotePadSelect.png)

Once opened we need to add one line of text, #define FLASH_BANK_NUMBER	FLASH_BANK_1, as shown below.

![Board manager](Guide/Images/EEPROM_WORK.png)

Please note that forgetting this step will lead to some confusion later on as the arduino code will compile and upload just fine but will not work correctly in practice as it will never remember its position.

### User board manager to add stm32duino

Back in arduino IDE use the "tools" -> Board manager menu at the top to add the STM32 boards to the IDE.

![Board manager](Guide/Images/BoardsManager.png)

This opens a panel on the left hand side, in this search for "STM". 

![STM Search](Guide/Images/STMSearch.png)

### Select the and configure the board

Use the "tools" menu again to select "3D printer boards"; 

tools -> STM32 MCU based boards -> 3D printer boards

![Choose 3D Printers](Guide/Images/3DPrinterBoards.png)

Then use the newly added menus to select the board part number, the Big Tree Tech EBB42 uses all the same hardware and connections just on a slightly larger PCB. 

![Choose EBB42](Guide/Images/BoardPartNumber.png)

And upload method

![Choose Upload method](Guide/Images/UploadMethod.png)

Finally the board is ready to be used in Arduino IDE!

### Install STM32CubeProgrammer

We still aren't done installing software, when the Arduino IDE uploads the file to the EBB42 board it will first try to compile it and when it does that it reaches out to the STM32 compiler which wont exist yet on your computer! In order for this to work we need to install STM32CubeProgrammer which can be downloaded from.

https://www.st.com/en/development-tools/stm32cubeprog.html

### Adding in required libraries.

In order to comunicate with the TMC2209 stepper driver on the EBB36 PCB we need computer code, we didn't write this fully ourselves we got some help and used a library that was written by teemuatlut, here's a link to his projects github https://github.com/teemuatlut/TMCStepper however you won't need to download anything from there as we can do that via the Arduino IDE itself. 

To do this we use the manage libraries function from the Sketch menu option

![Choose manage libraries](Guide/Images/ManageLibraries.png)

Type TMCStepper into the search box and then install the latest version.

![Search for TMXStepper](Guide/Images/TMCStepperLibrary.png)

The console in the bottom right will show success when installation is successful. 

![Console shows success](Guide/Images/ConsoleSuccess.png)

Now arduino IDE is fully ready to be used to program the EBB36!

### Download and Unzip Realta EBB42 telescope focuser repository

Now we need to download the code and other files in this repository, on the main page there is a green "<> Code" button.

![GITHub download link](Guide/Images/CodeDownloadZIP.png)

clicking it will give you the oprion to download a zip file, click that. This will result in a zip folder appearing in your downloads folder, right click on that an choose "Extract All..."

![Extract All](Guide/Images/DownloadedZip1.png)

This will show a dialog box asking you where to unzip the file, leave the defaults but do click the "Shpw extracted files when complete" and click the "Extract" button

![Save it where?](Guide/Images/DownloadedZip2.png)

This should open a window showing a file structure similar to the image below.

![here are the folders](Guide/Images/UnzippedFolder.png)

### Compiling and uploading source files using Ardunio IDE.

Go to the folder 

"%UserProfile%\Downloads\Realta-EBBfocuser-main\Realta-EBBfocuser-main\Arduino\EBB42TelescopeFocuser and double click EBB42TelescopeFocuser.ino"

![EBB42TelescopeFocuser.ino](Guide/Images/OpenArduinoCodeFile.png) 

We are now ready to upload the arduino code to the EBB36 however we must first put the EBB36 into upload mode. Connect the EBB36 to your computer using a suitable cable and connect it to a 12v power source. You should here your computer beep when its connected. 

Once this id done the EBB36 can be put into upload mode by pressing two buttons on the PCB, you can do this either by removing the case or using two tooth picks and a little trial and error.

![click hold click](Guide/Images/PutPCBintoUploadModee.png) 

You need to press and hold the button closest to the port panel and then click the other button once and release both. You should here a beep again as the device disconnects again.

Now that is done back in Arduino IDE we need to click the "upload" arrow button in the top left.

![upload arrow](Guide/Images/uploadbutton.png)

Once clicked the arduino code will be first compiled and then uploaded to the focuser. The first time you do this it can take a while as the STM32CubeProgrammer from earlier is silently opened in the background. 

When the code is successfully uploaded you will get an output at the bottom of the arduino window something like below.

![success](uploadSuccessful.png)

## Compiling ASCOM driver from source code.

### Download Visual Studio Community

Visual studio comunity is a free version of visual studio

https://visualstudio.microsoft.com/downloads/

Clicking the "Free download" button will take you to another site that will automatically start downloading the application. As its a ".exe" file your web browser might ask for your permission.

When VS studio Community starts to install it will ask you questions about what you want to use it for, answer x, y, x

### Run as administator

Explain its a DLL and need to be admin to register it in windows

### Open project

In the earlier step you downloaded the Realta EBB42 telescope focuser repository, the VS project is located in that repository in folder XYZ, open the file named todo_file_name.

### Configure for "Any CPU"

Who how to change to "Any CPU" compiler. Todo need to check this actually works for a fresh install otherwise ask to compile for x64 unless they know they are running an older CPU. 

### Rebuild project

Show screen shots of rebuilding.

### Alternatively using pre-compiled ASCOM driver installer.

## How to use ASCOM driver (Using N.I.N.A).

## Notes about INDI linux driver.

Lol I don't know how!
