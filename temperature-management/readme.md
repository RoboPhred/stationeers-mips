# Temperature Management

## Description

Monitors the temperature of a gas sensor and mantains temperature through the use of coolers and heaters.

## Features

- Shmitt triggered
- Supports batch writers and direct wall heaters / wall coolers
- Optional external temperature control
- Status reports via Status output.

## Devices

### GasSensor

Type: _Gas Sensor_

The gas sensor to measure the temperature from

### Heater

Type: _Memory_ or _Wall Heater_

The device to turn on when the room needs to be heated.
For batch writer use, attach a memory cell, and attach the cell to a batch writer.

### Cooler

Type: _Memory_ or _Wall Heater_

The device to turn on when the room needs to be cooled.
For batch writer use, attach a memory cell, and attach the cell to a batch writer.

### DesiredTemperatureDevice (_optional_)

Type: _Memory_ or _Dial_

The external source to specify the temperature.
By default, this is Celcius, but can be Kelvin by a config option.

## Configuration

### `DesiredTemperature`

Default: _295.15 Kelvin, 22 Celcius_

The target temperature to mantain in Kelvin.

### `Threshold`

Default: _1 Kelvin / Celcius_

The offset in degrees Kelvin to allow the temperature to differ from
DesiredTemperature before trying to correct it.

### `ExternalDesiredTempUnits`

Default: _1_ (Celcius mode)

The units to expect the value from DesiredTemperatureDevice in.
If 1, use Celcius, if 0, use Kelvin.

### `CheckInterval`

Default: _1_

The time in seconds to wait between temperature checks.

## Status codes

- `-1`: Cooling
- `0`: Idle
- `1`: Heating

## Workshop Link

[Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=2000346947)

## Implementation notes

For some reason I used the stack to pass function vars instead of to preserve registers... Not ideal, but it works.
