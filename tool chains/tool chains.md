# Tool chains for LilyGo T-ZigBee

The T-ZigBee module contains a ESP32-C3 and a TLSR8258 microcontroller. Each microcontroller requires its own tool chain. 

## Tool chain for programming the ESP32-C3

Adoucette described how he got a tool chain up and running for programming the ESP32-C3 in [issue 21](https://github.com/Xinyuan-LilyGO/T-ZigBee/issues/21#issuecomment-1566196339).

1. Install Visual Studio Code
2. Install Platformio extension in VS Code (press Ctrl + Shift +X to bring up the Extensions window, then search for PlatformIO)
3. Install C/C++ Extension Pack in VS Code (as above)
4. Install Git Extension Pack in VS Code (as above)
5. Install the drivers for the T-U2T. The T-U2T contains the CH9102 chip. The driver can be downloaded from LilyGo [CH9102_driver](https://github.com/Xinyuan-LilyGO/CH9102_Driver).
6. Now you will (finally) be able to connect the device via USB-C cable and LilyGo's "T-U2T" adapter. Ensure the device shows up in device manager (if not you may be a using bad USB cable - trust me and try different cables). When connected, note the COM port number.



## Tool chain for programming the TLSR8258

Telink provides a tool chain and IDE for creating firmware for the TLSR8258. In the release notes of the SDK there is a link where the preferred IDE for the relaese can be downloaded. For Version 3.7.1.1 it is Telink IoT Studio: [TelinkIoTStudio_V2024.8](https://wiki.telink-semi.cn/tools_and_sdk/Tools/IoTStudio/TelinkIoTStudio_V2024.8.zip).


## updating firmware of ESP32-C3
A [burning guide](https://zbhci.readthedocs.io/en/latest/user-guide/burning.html) is available. 

## updating firmware of TLSR8258

**Powering the TLSR8258**
The ESP32-3C is controlling the power of the TLSR8258 through GPIO0 (pin 4). Before the firmware of the TLSR8258 can be update the ESP32-3C should be loaded with firmware that enable the power. LilyGo suggest to flash the `factory test example` to the ESP for this purpose. However a simpler program setting:
```
pinMode(0, OUTPUT);
digitalWrite(0, HIGH);
```
should be sufficient.

**TlsrComSWireWriter**

[TlsrComSwireWriter](https://github.com/pvvx/TlsrComSwireWriter) can be used to burn firmware of the TLSR8258.  

The TlsrComSwireWriter simulates Telink SWIRE on a com port. 

![SCH](https://github.com/pvvx/TlsrComSwireWriter/blob/master/schematicc.gif)




