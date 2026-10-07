# NaviLink Duo: Cardputer I2C Decoder for GNSS/GPS Module + Adafruit Quad Encoder

The **NaviLink Duo** is an open-source hardware expansion board and accompanying software suite designed for the M5Stack Cardputer. It integrates real-time GNSS/GPS tracking, quad-rotary encoder support, and dual serial breakouts, making it a highly capable tool for amateur radio operators and hardware hackers. 

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
*   **Pin Mapping Warning:** Pin numbers for the MiniDIN connectors differ between the Yaesu standard and the physical DIN-802 datasheet.
*   **Power Regulation:** Utilizes an onboard 3.3V LDO regulator (LP2985-33DBVR).
*   **RTC/Data Backup:** Supports an optional rechargeable lithium-manganese ML1220 backup battery with a 3V maximum. 
*   **Battery Safety:** Users must absolutely not use a 3.6V lithium-ion battery.
*   **Acquisition Speed:** The backup battery is not strictly required for operation, but without it, cold-start GNSS acquisition times will be longer because ephemeral satellite data will not be retained.
*   **Charge Control:** The board provides a 1.7mA charge rate to the battery, and users can cut jumper JP1 to stop the battery from charging entirely.
*   **Visual Indicators:** Features onboard LEDs for Power and PPS (Pulse Per Second) indication. 
*   **LED Routing:** Includes a jumper-selectable header to route the PPS signal to an offboard LED if desired.

## Software Features (Sample Development Code - Version 1.28.0 or higher)

*   **Zero-Flicker Double Buffering:** Utilizes the `M5Canvas` library to draw the entire UI in a hidden RAM sprite before pushing it to the LCD, achieving a buttery-smooth 20fps refresh rate without strobe effects.
*   **Phase-Locked Software PPS:** Calculates a predictive 850ms to 150ms window synchronized to the NMEA data arrival, generating a visual UI asterisk that perfectly brackets the physical hardware PPS LED flash.
*   **Dynamic Telemetry Terminal:** Replaces raw NMEA text dumps with a scrolling, 4-color rotating data feed (Yellow, Green, White, Cyan) that extracts real-time satellite SV#s, Constellations, and Signal-to-Noise Ratios (SNR).
*   **Polyphonic DTMF Audio:** Leverages the M5Unified I2S mixer to generate true Dual-Tone Multi-Frequency (DTMF) feedback. The 4 encoders and 3 actions (Up/Down/Click) are mapped to a standard telephone matrix. (Listen for the "VE5SAR" T9 boot tune!)
*   **Dynamic Hot-Swap:** Safely detects the presence of the Adafruit Seesaw I2C Quad-Encoder (`0x49`) and dynamically reinitializes the library if the board is unplugged and reconnected during operation.

## Dependencies

To compile the sample sketch, ensure the following libraries are installed in your Arduino IDE:
*   `M5Cardputer` (and by extension, `M5Unified`)
*   `Adafruit_seesaw` (for the I2C Quad Encoder)
*   `Wire` (Standard I2C library)

## License & Credits

*   **Author:** Jody Herperger, VE5SAR  
*   **AI Assistant:** Google Gemini (Code generation & logic structuring)  
*   **License:** MIT License  

*This project is open-source. You are free to use, modify, and distribute this software and hardware design in your own projects. Please retain the author attribution in derivative works.*
