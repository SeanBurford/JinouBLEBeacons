# JinouBLEBeacons

Reverse engineered descriptions of Jinou BLE Beacons.

GATT Characteristics and Services are found under 0000XXXX-0000-1000-8000-00805f9b34fb.

## Services

| Handle | P  | Description                                   |
| ------ | -- | --------------------------------------------- |
| 0x2A05 | I  | Service Changed                               |
| 0x2A19 | NR | Battery Level                                 |
| 0xF350 |    | ?                                             |
| 0xF3FF | N  | ?                                             |
| 8EC90003-F315-4F60-9FB8-838830DAEA50 | I W | Buttonless DFU |

### Battery Level (0x2A19)

> 00002a19-0000-1000-8000-00805f9b34fb 64 (100%)

## General GATT Vendor Characteristics

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |
| 0x2A00 | RW | Device Name                                |
| 0x2A01 | R  | Appearance                                 |
| 0x2A04 | R  | Peripheral Preferred Connection Parameters |
| 0x2AA6 | R  | Central Address Resolution                 |
| 0x2A29 | R  | Manufacturer Name String                   |
| 0x2A24 | R  | Model Number String                        |
| 0x2A25 | R  | Serial Number String                       |
| 0x2A27 | R  | Hardware Revision String                   |
| 0x2A26 | R  | Firmware Revision String                   |
| 0x2A28 | R  | Software Revision String                   |
| 0x2A23 | R  | System ID                                  |
| 0xF357 | RW | Password                                   |

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

Device serial number and public MAC address as a string.

### Hardware Revision String (0x2A27)

> 00002a27-0000-1000-8000-00805f9b34fb 56-31-2E-31 "V1.1"

### Firmware Revision String (0x2A26)

> 00002a26-0000-1000-8000-00805f9b34fb 56-31-35-2E-30-2E-30 "V15.0.0"

### Software Revision String (0x2A28)

> 00002a28-0000-1000-8000-00805f9b34fb 56-31-2E-30-2E-34 "V1.0.4"

### System ID (0x2A23)

> 00002a23-0000-1000-8000-00805f9b34fb 01-23-45-00-00-67-89-AB

Device serial number and public MAC address as binary with two bytes of zero in the middle.

### Password (0xF357)

> 0000f357-0000-1000-8000-00805f9b34fb 00-00-00-00

Password for binding with the beacon over BLE, as an integer.  Max length is 6 digits.

123456 would be 00-01-E2-40

## Beacon Control Characteristics

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |
| 0xF35C | RW | Beacon Mode Select                         |
| 0xF355 | RW | Transmit Power                             |
| 0xF354 | RW | Measured RSSI                              |
| 0xF35B | RW | Beacon Name                                |
| 0xF356 | RW | Beacon Interval                            |
| 0xF358 | RW | Current Time                               |
| 0xF359 | RW | Daily Turn On Time                         |
| 0xF35A | RW | Daily Turn Off Time                        |

### Beacon Mode Select (0xF35C)

> 0000f35c-0000-1000-8000-00805f9b34fb 00 iBeacon
> 0000f35c-0000-1000-8000-00805f9b34fb 01 Eddystone™

### Transmit Power (0xF355)

> 0000f355-0000-1000-8000-00805f9b34fb 01 (0dBm)

| TX Power | Measured RSSI | Value                        |
| --------:| -------------:| ----------------------------:|
| 0x01     | 0xBA          | default iBeacon power (?dBm) |
| 0x00     | 0x04          | 4dBm                         |
| 0x01     | 0x00          | 0dBm                         |
| 0x02     | 0xFA          | -6dBm                        |
| 0x03     | 0xE9          | -23dBm                       |

### Measured RSSI (0xF354)

[Measured RSSI](https://support.kontakt.io/hc/en-gb/articles/201621521-Transmission-power-settings).  Must be updated if transmit power is changed, otherwise distance calculations will be wrong.

iBeacon (@1m):

> 0000f354-0000-1000-8000-00805f9b34fb BA

Eddystone™ (@0m):

> 0000f354-0000-1000-8000-00805f9b34fb FA (-6dBm)

### Beacon Name (0xF35B)

> 0000f35b-0000-1000-8000-00805f9b34fb 4A-69-6E-6F-75-5F-42-65-61-63-6F-6E "Jinou_Beacon"

Name that is transmitted in beacon packets.

### Beacon Interval (0xF356)

> 0000f356-0000-1000-8000-00805f9b34fb 0C-80

Beacon interval in 5/8 of a millisecond (0.000625s).  Range 100 - 10,000.

| Decimal | Hex   | Interval    |
| -------:| -----:| -----------:|
| 100     | 00-64 | 0.06s       |
| 160     | 00-A0 | 0.1s        |
| 1,600   | 06-40 | 1.0s        |
| 3,200   | 0C-80 | 2.0s        |
| 10,000  | 27-10 | 6.25s       |

### Current Time (0xF358)

> 0000f358-0000-1000-8000-00805f9b34fb 07-E2-0B-1A-0E-39

Year (07-E2) = 2018
Month (0B) = 11
Day (1A) = 26
Hour:Min (0E-39) = 14:37

### Daily Turn On Time (0xF359)

> 0000f359-0000-1000-8000-00805f9b34fb 00-00-00-00-00-00-00-00-00-00-00-00-00-00

00:00 times 7

### Daily Turn Off Time (0xF35A)

> 0000f35a-0000-1000-8000-00805f9b34fb 18-00-18-00-18-00-18-00-18-00-18-00-18-00

24:00 times 7

## iBeacon GATT Vendor Characteristics

Available on models that support iBeacon.  iBeacon is selected by writing 0x00 to 0xF35C.

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |
| 0xF351 | RW | iBeacon UUID                               |
| 0xF352 | RW | iBeacon Major                              |
| 0xF353 | RW | iBeacon Minor                              |

### iBeacon UUID (0xF351)

> 0000f351-0000-1000-8000-00805f9b34fb 00-12-34-56-78-9A-BC-DE-F0-00-12-34-56-78-9A-BC

### iBeacon Major (0xF352)

> 0000f352-0000-1000-8000-00805f9b34fb 00-00

### iBeacon Minor (0xF353)

> 0000f353-0000-1000-8000-00805f9b34fb 00-00

## Eddystone™ GATT Vendor Characteristics

Available on models that support Eddystone™.  Eddystone™ is selected by writing 0x01 to 0xF35C.

| Handle | P  | Description                                |
| ------ | -- | ------------------------------------------ |
| 0xF35D | RW | Eddystone Frame Type                       |
| 0xF35E | RW | Namespace + Instance ID                    |
| 0xF35F | RW | URI                                        |

### Eddystone Frame Type

> 0000f35d-0000-1000-8000-00805f9b34fb 10

Selects broadcast of UUID (0x00) or URL (0x10).

### Namespace + Instance ID

Namespace + Instance ID to broadcast if frame type is 0x00.

> 0000f35e-0000-1000-8000-00805f9b34fb, value: (0x) 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00

### URI

URI to broadcast if frame type is 0x10.

> 0000f35f-0000-1000-8000-00805f9b34fb 00-6A-69-6E-6F-75-78-00 "http://www.jinoux.com"

[Online encoder](https://www.mkompf.com/tech/eddystoneurl.html) for the URI and measured RSSI level.

## Models

### JO-0618

| Model Number | Chip     | Beacons             | Form  | Description                   |
| ------------ | -------- | ------------------- | ----- | ----------------------------- |
| JO-0618      | nRF52810 | iBeacon, Eddystone™ | Puck  | Replaceable CR2032 battery    |

Hardware Rev: V1.1

Firmware Rev: V15.0.0 (nRF SDK version)

Software Rev: V1.0.4

### JO-0468-6

| Model Number | Chip     | Beacons             | Form  | Description                   |
| ------------ | -------- | ------------------- | ----- | ----------------------------- |
| JO-0468-6    | CC254x   | iBeacon             | Case  | Replaceable 2xAA battery      |

Hardware Rev: V2.0

Firmware Rev: V1.4.0

Software Rev: V0.2.5

