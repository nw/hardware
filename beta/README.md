#Hardware documentation

for Tessel Beta (TM-00-00 and TM-00-02)

## Custom modules

Thinking of rolling your own module or Tessel-compatible microcontroller? Drop us a line at [team@technical.io](mailto:team@technical.io). We'd love to talk!

## Physical layout

![Tessel (TM-00-00) with parts labeled](https://github.com/technicalmachine/tessel-design-docs/blob/master/images/TM-00-00-ports.png?raw=true)

Note that the locations and dimensions of things such as buttons and mount holes may change. There are also multiple debug headers on the current board that may be removed in production versions.

##Module Ports

Tessel is extensible via modules, which connect to the 10-pin, 0.1” (2.54 mm) right angle female headers on the main board. 

* All pins use 3.3V logic.
* Module bank names (A, B, C, and D) are located between the module headers.
* Adjacent module ports are currently spaced apart by 0.3” (7.62 mm).
* Pins are located 0.089” (2.22 mm) from the board edge.
* There are four 0.13" (3.3 mm) diameter mounting holes in the corners of the board, each 0.1" (2.54 mm) in from the edges. They are 2.359" (59.92  mm) and 1.375" (34.93 mm) apart in the horizontal and vertical dimensions, respectively.

The following is the pinout for a module bank: 

Pin | Name | Notes
----|------|----
1 | GND  | Ground
2 | 3V3  |  3.3V power rail, marked with a box around the pin on the silkscreen. The onboard regulator is rated to 1A.
3 | SCL  | I2C clock line. On TM-00-00, this bus is shared board-wide. On TM-00-02, ports A and B share a common I2C bus, as do ports C and D.
4 | SDA  | I2C data line. On TM-00-00, this bus is shared board-wide. On TM-00-02, ports A and B share a common I2C bus, as do ports C and D.
5 | SCK  | SPI clock line. Common for the entire board.
6 | MISO  | SPI master in/slave out. Common for the entire board.
7 | MOSI  | SPI master out/slave in. Common for the entire board.
8 | GPIO1 / UART TX  | User-configurable general purpose input/output. Unique to each module port. / UART serial transmit
9 | GPIO2 / UART RX  | User-configurable general purpose input/output. Unique to each module port. / UART serial recieve
10 | GPIO3  | User-configurable general purpose input/output. Unique to each module port.

*Note:* For TM-00-02, module ports A, B, and D have hardware UART. UART for Port C is done is software. TM-00-00 supports software UART only. Software UART is much slower than hardware UART.

## Using modules

Any module can be plugged into any module port and installed using Node Package Manager via the command line. Once physically attached, the module can be attached in software in a similar manner. Each module provided by Technical Machine for use with the Tessel is documented within this repository.
Although modules may occupy more than one physical port (such as the RFID module), they typically only use the electrical conenctions on one port. The other should be broken out to another header bank on the board.

##Module markings

![A Tessel (TM-00-00) "fully loaded" with four modules: top ](https://github.com/technicalmachine/tessel-design-docs/blob/master/images/TM-00-00-fullyloaded-top.jpg?raw=true)


The module name is the top of board, usually in the upper left corner (with the pin headers facing left). This is what is installed with npm and is usually the name of the corresponding repository on GitHub. The specific formatting of the module name may change.


![A Tessel (TM-00-00) "fully loaded" with four modules: bottom](https://github.com/technicalmachine/tessel-design-docs/blob/master/images/TM-00-00-fullyloaded-bottom.jpg?raw=true)

The bottom silkscreen has, from top to bottom/left to right:

* The module's symbol, used to identify it at a glance
* The module name (same as on the top)
* The module model number
* The module's peak (as opposed to average) current draw
* The URL for the [Tessel website](https://tessel.io) 

*Note:* the Tessel's onboard 3.3V regulator is rated to 1A and that the typical base system requires beteween 150mA and 600mA depending on network usage and memory access. Parts of the Tessel can also be powered off/put into sleep mode to reduce power consumption.
 

##GPIO Bank

* The bank itself is marked with "GPIO" on both ends.
* 2 x 10 (20 pins total).
* 0.1” (2.54 mm) pin spacing.
* All pins use 3.3V logic.
* Although it is not recommended, the bottom row of the GPIO bank (nearest the board edge) can be used as a module port (port E on the Tessel).

Pin     |     Name  |  Notes  | Pin | Name | Notes
----|------|--------|---------|-----|------|------
1       |  GND     |   Ground                                                                                           | 2     |     5V   |   This is the input to the onboard 3.3V regulator, and typically comes either from USB or an external battery. As such, it may not be exactly 5V, especially if the Tessel is not powered off USB. Not recommended as source/sink of significant current.
3       |  3V3     |   3.3V power rail, marked with a box around the pin on the silkscreen. The onboard regulator is rated to 1A.                                                                                                            | 4     |     A1   |   ADC1. 10-bit ADC, referenced to GND and 3.3V. Cannot function as anything else.
5       |  SCL     |   I2C clock line. Common for the entire board.                                                     | 6     |     A0   |   ADC0. 10-bit ADC, referenced to GND purpose input/output. Cannot function as anything else.
7       |  SDA     |   I2C data line. Common for the entire board.                                                      | 8     |     A5   |   ADC5. 10-bit ADC. Reconfigurable as digital GPIO
9       |  SCK     |   SPI clock line. Common for the entire board.                                                     | 10    |     A4   |   ADC4. 10-bit ADC, referenced to GND and 3.3V. Reconfigurable as digital GPIO.
11      |  MISO    |   SPI master in/slave out. Common for the entire board.                                            | 12    |     A3   |   ADC3. 10-bit ADC, referenced to GND and 3.3V. Reconfigurable as digital GPIO.
13      |  MOSI    |   SPI master out/slave in. Common for the entire board.                                            | 14    |     A2   |   ADC2. 10-bit ADC, referenced to GND and 3.3V.  Reconfigurable as 10-bit DAC.
15      |  G1      |   GPIO1. User-configurable general purpose input/output. Also doubles as UART TX.                  | 16    |     G6   |   GPIO6. User-configurable general purpose input/output. 
17      |  G2      |   GPIO2. User-configurable general purpose input/output. Also doubles as UART RX.                  | 18    |     G5   |   GPIO5. User-configurable general purpose input/output.
19      |  G3      |   GPIO3. User-configurable general purpose input/output.                                           | 20    |     G4   |   GPIO4. User-configurable general purpose input/output. 

    
## Design philosophy

The module ports each include power, I2C, SPI, and three GPIO lines, which allows for the design of modules of arbitrary complexity. Note that the I2C and SPI busses are shared; as such, it is recommended that modules communicate over SPI and GPIO whenever possible. Doing so will mitigate the risks of I2C address conflicts and allow for multiple instances of the same kind of module.

Modules should be devices with clear-cut functionality. That is to say, they should have a single, well-defined purpose or a set of closely related functions, rather than an eclectic mix of capabilities onboard. This requirement is designed to reduce complexity, cost, and power consumption and maximize reusability in hardware and software.


## Future directions/to do
In the future, this repository will include schematic and layout templates for Modules in Diptrace. Versions in EAGLE and Upverter are also planned.
Please note that the hexagon logo on each of the first-party modules is a trademark of Technical Machine. Although Technical Machine is still formulating thrid-party branding documentation and standards, at this time we request that our community reserves the hexagon for first-party and/or approved hardware.

## License
Designed by [Technical Machine](http://technical.io/) and shared under a [Creative Commons Attribution ShareAlike license](http://creativecommons.org/licenses/by-sa/3.0/). All license text and links must be included in any redistribution.













 
