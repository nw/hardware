#Hardware documentation
for Tessel v1.0

##Module Ports
Tessel is extensible via modules, which connect to the 10-pin, 0.1” (2.54 mm) right angle female headers on the main board. 

* All pins use 3.3V logic.
* Module bank names (A, B, C, and D) are located near the corners of the board. 
* Adjacent module ports are spaced apart by 0.3” (7.62 mm)
* In between module ports is a 0.13” (3.302 mm) diameter mounting hole with 0.2” (5.08 mm) diameter of route/plane keepout.
* Pins are located 0.1” (2.54 mm) from the board edge.

The following is the pinout for a module bank: 

Pin | Name | Notes
----|------|----
1 | GND  | Ground
2 | 3V3  |  3.3V power rail, marked with a box around the pin on the silkscreen. The onboard regulator is rated to 1 A
3 | SCL  | I2C clock line. Common for the entire board.
4 | SDA  | I2C data line. Common for the entire board.
5 | CLK  | SPI clock line. Common for the entire board
6 | MISO  | SPI master in/slave out. Common for the entire board.
7 | MOSI  | SPI master out/slave in. Common for the entire board.
8 | GPIO1  | User-configurable general purpose input/output. Unique to each module port.
9 | GPIO2  | User-configurable general purpose input/output. Unique to each module port.
10 | GPIO3  | User-configurable general purpose input/output. Unique to each module port.

##Module markings
All modules include a logo and the name of the module, used for installing via npm, in bold on the silkscreen. The second line includes the semantic version of the board and the module's peak (as opposed to average) current draw, expressed in milliamperes (mA). Note that the Tessel's onboard regulator is rated to 1A and that the base system requires beteween 300mA and 600mA depending on network usage and memory access.
 
 
##GPIO Bank

* The bank itself is marked by the letter “E.”
* The Pin numbers zig-zag. Pin 1 is located by the board edge near the “E.” Pin 2 is directly above Pin 1 and Pin 3 is directly to the right of Pin 1. 
* 2 x 10 (20 pins total). 
* 0.1” (2.54 mm) pin spacing
* All pins use 3.3V logic
* Although it is not recommended, the bottom row of the GPIO bank (nearest the board edge) can be used as a module port (port E).

Pin     |     Name  |  Notes  | Pin | Name | Notes
----|------|--------|---------|-----|------|------
1       |       GND  |    Ground. | 2      |       G6   |      GPIO6. User-configurable general purpose input/output. 
3       |       3V3    |    3.3V power rail, marked with a box around the pin on the silkscreen. The onboard regulator is rated to 1 A. | 4       |      G5      |    GPIO5. User-configurable general purpose input/output.
5         |     SCL      |   I2C clock line. Common for the entire board. | 6       |      G4       |   GPIO4. User-configurable general purpose input/output. 
7         |     SDA     |   I2C data line. Common for the entire board. | 8        |     A5       |    ADC5. 10-bit ADC. Reconfigurable as digital GPIO.
9         |     CLK      |   SPI clock line. Common for the entire board. | 10       |    A4        |   ADC4. 10-bit ADC, referenced to GND and 3.3V. Reconfigurable as digital GPIO.
11       |    MISO    |   SPI master in/slave out. Common for the entire board. | 12      |     A3       |    ADC3. 10-bit ADC, referenced to GND and 3.3V. Reconfigurable as digital GPIO.
13      |     MOSI    | SPI master out/slave in. Common for the entire board. | 14      |     A2      |     ADC2. 10-bit ADC, referenced to GND and 3.3V.  Reconfigurable as 10-bit DAC.
15     |     G1      |    GPIO1. User-configurable general purpose input/output. Also doubles as UART TX. | 16       |    A1      |     ADC1. 10-bit ADC, referenced to GND and 3.3V. Cannot function as anything else.
17      |    G2       |   GPIO2. User-configurable general purpose input/output. Also doubles as UART RX. | 18       |    A0       |    ADC0. 10-bit ADC, referenced to GND purpose input/output. Cannot function as anything else.
19       |    G3       |   GPIO3. User-configurable general purpose input/output. |20        |   5V        |   5V USB power. It is also the input to the onboard 3.3V regulator. Not recommended as source/sink of significant current.


















 
