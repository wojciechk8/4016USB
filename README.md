## What is it?
USB connected NES/Famicom controller port interface. It allows to use
NES/Famicom peripherals on a PC. The hardware is flexible enough to
handle other retro controllers as well (see the
[list](#supported-peripherals) below). Also, there is an ability to
capture controller inputs while playing on a real console (useful e.g.
during streaming).

The name of this project (4016) comes from the address of the I/O port
in the NES CPU.


## Features
* Full (extended<sup>1</sup>) NES/Famicom controller port interface
* 2 controllers handling (2 players allowed)
* Slave mode: the controller could be connected both to the device and
  to the console
* 5V/3.3V selectable interface voltage (allows handling newer
  controllers, e.g. PSX)
* 16 input data lines, 5 input/output control lines

<sup>1</sup> NES provides 5 data lines per port ($4016, $4017); this
             device has 8 data lines per port.

### Supported peripherals
*NOTE: Consoles support depends on hardware (a proper connector board,
 interface capability) and firmware, while console's peripherals support
 depends only on firmware.*

Console      | Peripheral          | Notes
------------ | ------------------- | -------
NES/Famicom  | Standard controller |
...          |                     |

## Hardware
The design is divided into two modules: *main* and *connector*. The main
module contains all the electronics (or most part of it), and the
connector module is a mechanical interface to a controller port of
a specific console. The connector module is then a replaceable part of
the device.

The interface consists of 16 input lines (8 can be read at a time, since
they are multiplexed) and 5 input/output lines. The output voltage on
the 5 i/o lines can be set to 3.3V or 5V. The voltage and the direction
is controlled by the MCU. All these lines are named after NES/Famicom
controller interface, and extended to 8 data lines instead of 5.

The connector module can be equipped with an I2C EEPROM providing
information about console type. This identification allows automatically
load the proper firmware for a specific controller type. *NOTE: A game
console could have different controllers/peripherals connected to the
same port. The ID ROM could only provide information about connector
type, not a peripheral itself.*

### Schematic/PCB
The schematic was created with [gschem](http://www.geda-project.org/)
and the pcb layout with [pcb-rnd](http://repo.hu/projects/pcb-rnd/).


## Firmware
The firmware repository of this project is located [here](_TODO_).


## License
This design is licensed under CERN OHL v.1.2. See the LICENSE file for
the full text of the license.
