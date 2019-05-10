# JinouBLEBeacons

Reverse engineered descriptions of Jinou BLE Beacons.

## General GATT Vendor Characteristics

Found under 0000XXXX-0000-1000-8000-00805f9b34fb.

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |
| 0x2A00 | RW | Device Name                                |
| 0x2A01 | R  | Appearance                                 |
| 0x2A04 | R  | Peripheral Preferred Connection Parameters |
| 0x2AA6 | R  | Central Address Resolution                 |
| 0x2A29 | R  | Manufacturer Name String                   |
| 0x2A24 | R  | Model Number String                        |
| 0x2A25 | R  | Serial Number String                       |


### Device Name (0x2A00)

> 00002a00-0000-1000-8000-00805f9b34fb 4A-69-6E-6F-75-5F-42-65-61-63-6F-6E "Jinou_Beacon"

A string that identifies the device.

### Appearance (0x2A01)

> 00002a01-0000-1000-8000-00805f9b34fb 00-00

External appearance of the device (icon).  Set to None.

### Peripheral Preferred Connection Parameters (0x2A04)

> 00002a04-0000-1000-8000-00805f9b34fb 10-00-28-00-00-00-90-01

### Central Address Resolution (0x2AA6)

> 00002aa6-0000-1000-8000-00805f9b34fb 01 (address resolution supported)

### Manufacturer Name String (0x2A29)

> 00002a29-0000-1000-8000-00805f9b34fb 4A-69-6E-6F-75 "Jinou"

### Model Number String (0x2A24)

> 00002a24-0000-1000-8000-00805f9b34fb 4A-4F-2D-30-36-31-38 "JO-0618"

### Serial Number String (0x2A25)

> 00002a25-0000-1000-8000-00805f9b34fb 30-31-3A-32-33-3A-34-35-3A-36-37-3A-38-39-3A-41-42 "01:23:45:67:89:AB" 

Device serial number and public MAC address.


## iBeacon GATT Vendor Characteristics

Available on models that support iBeacon.

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |

## Eddystone™ GATT Vendor Characteristics

Available on models that support Eddystone™.

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |



## Models

| Model Number | Chip     | Beacons             | Form  | Description                   |
| ------------ | -------- | ------------------- | ----- | ----------------------------- |
| JO-0618      | nRF52810 | iBeacon, Eddystone™ | Puck  | Replaceable CR2032 battery    |

