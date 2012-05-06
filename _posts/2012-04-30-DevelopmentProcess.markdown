---
layout: post
title :  Development Process
---

As mentioned before, the development will be done on <a href="http://www.st.com/internet/evalboard/product/252419.jsp"> STM32F4DISCOVERY </a> kit. Previously the plan was to develop on LPC1768 Philips ARM Cortex M3 microcontroller. But the STM32Discovery kit contains much more powerful controller. The details about the controller in the STM32F4DISCOVERY will be discussed later.

On the kit, initially a serial port will be setup. The serial port will be used to controll the CAN controller. The serial port can also be used for debugging purpose. Once the CAN communication is running with serial communication (only slow speed CAN communication), the USB port will be enabled. CAN data rates of 1Mbits/Sec will be made possible to exchange towards PC (Host) side using USB port. Initially to test USB, a sample LED control can be developed. Using libusb, the host controll software for the hardware will be written using C (Python will be supported in future).

By this time the STM32Discovery kit has been proved for the project and a parallel development of the hardware will be done. The schematics of the implementation done on STM32Discovery kit will be still available so that the user who has access to the STM32Discovery kit can modify and make CANsniff.

Along with this additional features such as standalone operation will be developed. In standalone mode, the CANsniff hardware can be used to sniff the protocol and store it into SD card. For this an FAT filesystem might be needed to be implemented. FAT filesystem are already available for the STM32 controllers which can be used for the project. The user initially connects the CANsniff board on to the PC. If there are any settings to be done on the hardware for the standalne mode, it can be configured and if needed can be stored to the EEPROM. User can now remove the hardware from PC and connect it to the real automotive network. The CANsniff board will be powered from the automotive battery. User can initiate and end the measurement by pressing switch. Autobaud rate detection, and other features if any are needed will also will be enabled.

The STM32F4DISCOVERY kit contains two CAN ports and one LIN port. Using these gateway functionality can be made possible i.e changing the baud rate from one CAN port to another or even change the protocol(from CAN to LIN or LIN to CAN).

If the functionality in the hardware is needed to be controlled using an RTOS, already existing RTOS such ad FreeRTOS or ChibiOS will be used. Aslo ethernet port will be enabled. Through this user can controll the CANsniff by wireless router.
