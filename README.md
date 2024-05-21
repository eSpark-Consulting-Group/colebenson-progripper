# LSS Modular Variable Gripper
### Client Name: Cole Benson (Robotshop)

## Requirements
The product should be compatible with LSS PRO Servos PCB design (electrical and communication). The idea behind the product is to be able to create robotic fingers for controlling and picking things. Each finger will have two motors to allow both parallel and angular motion. Some of the core features of the product are:
* Microcontroller: STM32F407 (same as LYN PRO Servos). Debuggin over SWD (same as Lyn PRO) needs to be added.
* CAN chip (same as LYN PRO servos)
* Voltage regulation (ex. 36 -> 12V for motors). The max input voltage will be 36V.
* DC Motor Controllers
    * Current detection (ideally stall detection and within motor controller but accessible to microcontroller)
* Connector on the DC Motor is [ZHR-6](https://github.com/eSpark-Consultants/colebenson-progripper/files/14555300/0900766b81357f31.pdf). Their vertical counterparts need to be added and placement of connectors should be done according to provided frame dxf. There will be 10 x connectors in total. 2 for 2 motor drivers of one finger and the remaining 2 fingers to have 4 connectors each (8 connectors in total) in hot redundant topology.
* XT60 Connector (~30 to 36V input, perhaps a bit more for max). These should be same as LSS PRO Servos. This should be on top board.
* RJ45 Connector (same pinout as PRO servos). This should be on bottom board.
* USB for reprogramming and firmware updates. This should be exposed from bottom side of the bottom PCB. Preferred height around 7mm.
* RGB LED at 90 degrees and placed on top side of bottom PCB. Appropriate glass pipe should be selected to expose light from near the RJ45 connector.
* Button should be vertical type about ~ 6.5 - 7mm height and placed on bottom side of bottom PCB.
* All right angled peripherals being exposed from upper side of boards should be only 1.5mm outside the PCB edge.
* 
* Proposed Motor Driver chips
    * [DRV8214](https://www.ti.com/lit/ds/symlink/drv8214.pdf)
    * [DRV8234](https://www.ti.com/lit/ds/symlink/drv8234.pdf)
* When the traveler reaches either end of the lead screw, it will be physically stopped by the frame. The current will spike and it needs to automatically stop the motor. The microcontroller should not be needed for this.
* The microcontroller needs to read the current consumed by both motors in order to translate that to a force estimate acting on either motor. This should ideally be integrated into driver chip.
* Reading encoder position and/or the new method of ripple counting. The more that's done by the motor controller, the better. but traveler's absolute linear position will be required in the end (convert rotations to linear position)
* TI Article [Sensorless position and speed control](https://www.ti.com/lit/ab/slvafr5/slvafr5.pdf)
* The motor datasheet is pushed to docs folder. It also contains a more detailed PRD received from client!
* PCB mount temperature sensor on either top board or bottom board (depending on which board will have the MCU or most sensitive to heat circuitry). This sensor will be for measuring PCB temperature only.


## Nomenclature (Concept Image)
![image](https://github.com/eSpark-Consultants/colebenson-progripper/assets/76909080/5089d6a5-9739-4b5f-8e6c-280b75a84de4)
