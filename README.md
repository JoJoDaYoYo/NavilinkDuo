# NaviLink Duo: Cardputer GNSS + Serial Breakout Board, with demo code for an I2C decoder for GNSS/GPS Module + Adafruit Quad Encoder Board

The **NaviLink Duo** is an open-source hardware expansion board and accompanying software demo designed for the M5Stack Cardputer. The board integrates a GNSS/GPS module, has Qwiic ports for external quad-rotary encoder support, and has dual serial breakouts, making it a highly capable tool for amateur radio operators and hardware hackers. 

The board breaks out two serial ports. The first is the hardware-based UART functionality built into the Cardputer itself. This port is wired to two separate physical ports in parallel (one 3.5mm jack, in parallel with a Mini DIN-8 jack wired to be compatible with Yaesu amateur radio serial ports). The second serial port is a software port, wired to the Cardputer's SPI CS and MISO pins. This software serial is wired to 3.5mm and Mini DIN-8 jacks, similar to the UART serial. 

> **Important Usage Note:** The provided application code is strictly a sample intended for development, demonstration, and testing purposes. The NaviLink Duo is a versatile hardware platform, and developers are encouraged to use the board as a foundation for building their own custom projects and applications!

## Hardware Features (NaviLink Duo Board)

*   **Core GNSS:** Powered by the u-blox SAM-M8Q-0 module communicating over I2C at address `0x42`. 
*   **Power Efficiency:** Maximum current draw is approximately 31mA @ 5V during GNSS acquisition.
*   **Compatibility:** The board is compatible with both the Cardputer ADV and Cardputer Zero.
*   **Architecture Constraint:** The Raspberry Pi used in the Cardputer Zero offers less flexibility for reassigning pins to a second serial port compared to the simpler pin redefinitions of the Arduino-based ADV.
*   **Connectivity:** Features a 14-pin right-angle pin header (H1) for the main interface.
*   **Expansion:** Includes dedicated 3.3V I2C headers for attaching rotary encoders.
*   **Audio/Serial Jacks:** Equipped with 3.5mm audio jacks and 8-pin MiniDIN jacks.
*   **Radio Integration:** The Mini DIN-8 connectors are specifically wired for Yaesu ACC ports.
*   **Pin Mapping Warning:** Pin numbers for the MiniDIN connectors differ between the Yaesu standard and the physical DIN-802 datasheet normally used for other purposes.
*   **Power Regulation:** Utilizes an onboard 3.3V LDO regulator (LP2985-33DBVR).
*   **RTC/Data Backup:** Supports an optional rechargeable lithium-manganese ML1220 backup battery with a 3V maximum. 
*   **Battery Safety:** Users must absolutely not use a 3.6V lithium-ion battery.
*   **Acquisition Speed:** The backup battery is not strictly required for operation, but without it, cold-start GNSS acquisition times will be longer because ephemeral satellite data will not be retained.
*   **Charge Control:** The board provides a 1.7mA charge rate to the battery, and users can cut jumper JP1 to stop the battery from charging entirely.
*   **Visual Indicators:** Features onboard LEDs for Power and PPS (Pulse Per Second) indication. 
*   **LED Routing:** Includes a jumper-selectable header to route the PPS signal to an offboard LED if desired. This is useful if the PPS LED must be externally visible in an enclosure.

## Software Features - Cardputer ADV Version (GNSS/Encoder Arduino Sample Development Code)

*   GNSS satellite status, signal reports, and polar satellite map
*   Maidenhead grid calculation and RTC time sync from GNSS module to Cardputer clock
*   Encoder "dial" testing indicators, including pushbuttons
*   Dual serial "monitor" to display any incoming RX traffic on the two ports at a variety of Baud rates
*   Support for hot-swap of main module and/or encoder expansion modules
*   See the version release notes for full feature descriptions.

## Software Features - Cardputer ADV Version (I2C Bus Scanner Arduino Sample Development Code)

*   The I2C bus scanner is a diagnostic tool to help identify any I2C devices currently attached to the Cardputer ADV.
*   The NaviLink Duo board is NOT required for operation. However, when it IS attached, the GNSS module should appear, as well as any externally connected devices (like encoders) attached to the Qwiic connectors.
*   DTMF tones will sound when a device initially connects, and again when it disconnects.

## License & Credits

*   **Author / Hardware Developer:** Jody Herperger, VE5SAR  
*   **AI Assistant:** Google Gemini (Code generation & logic structuring)  
*   **License:** MIT License  

*This project is open-source. You are free to use, modify, and distribute this software and hardware design in your own projects. Please retain the author attribution in derivative works.*

<img width="576" height="768" alt="IMG_1179" src="https://github.com/user-attachments/assets/ce3254c2-6017-48be-bb55-012b9679b76e" />
<img width="1365" height="719" alt="image" src="https://github.com/user-attachments/assets/3cff0b69-59aa-4186-a3b4-589c6dffaad5" />
<img width="1586" height="346" alt="image" src="https://github.com/user-attachments/assets/7884c335-3934-4214-8883-067479a01315" />
<img width="1186" height="597" alt="image" src="https://github.com/user-attachments/assets/107d0ee3-682f-455e-824b-1bf3b1757b56" />

