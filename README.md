# TEC Heat pump

Information about the TEC QRS11 heat pump and it's modbus connection. Not all values are know yet. USE AT YOUR OWN RISK.

## Wordlist

Some words are shortend to make it easer to read, here is the list of word

- Domestic Hot Water (DHW)

## RS-485 (modbus)

| Type     | Value |
| -------- | ----- |
| Baudrate | 9600  |
| Databits | 8     |
| Stopbits | 2     |
| Parity   | even  |

### Discrete output (coil / read-write)

| Address | Parameter | Value      |
| ------- | --------- | ---------- |
| 1       | DI4       | AC Switch  |
| 2       | DI5       | DHW Switch |

### Discrete input (read-only)

| Address | Parameter | Value                                                              |
| ------- | --------- | ------------------------------------------------------------------ |
| 1       | AL01      | Alarm: Low pressure                                                |
| 2       | AL02      | Alarm: High pressure                                               |
| 3       | AL03      | Alarm: Low outlet water temperature (ST < AR01)                    |
|         |           |                                                                    |
| 5       | AL05      | Alarm: High outlet water temperature (ST > AR03)                   |
| 6       | AL17      | Alarm: Water flow is short                                         |
| 7       | AL18      | Alarm: Low pressure alarms times within 24 hours is over the limit |
| 8       | AL19      | Alarm: High pressure alarms times within 24 is over the limit      |
| 9       | AL20      |                                                                    |
| 10      | AL21      |                                                                    |
| 11      | AL24      |                                                                    |
|         |           |                                                                    |
| 13      | AL37      |                                                                    |
| 14      | AL38      |                                                                    |
| 15      | AL71      |                                                                    |
| 16      | AL72      |                                                                    |
| 17      | AL73      |                                                                    |
| 18      | AL74      |                                                                    |
| 19      | AL75      |                                                                    |
| 20      | AL76      |                                                                    |
|         |           |                                                                    |
| 23      | AL78      |                                                                    |
|         |           |                                                                    |
| 25      |           | Secondary Pump                                                     |
|         |           |                                                                    |
| 27      |           | Primary Pump                                                       |
|         |           |                                                                    |
| 32      | NO4       | AC Heater                                                          |
|         |           |                                                                    |
| 36      | NO8       | DHW Heater                                                         |
|         |           |                                                                    |
| 39      | NO6       | Gas boiler                                                         |

### Input register (read-only)

| Address | Parameter | Value               | unit       |
| ------- | --------- | ------------------- | ---------- |
| 1       | B1        | Inlet Temperature   | 0.1°C      |
| 2       | B2        | Outlet Temperature  | 0.1°C      |
| 3       | T2        | Ambient Temperature | 0.1°C      |
| 4       | T4        | Suction             | 0.1°C      |
| 5       | T3        | Discharge           | 0.1°C      |
| 6       | B6        | Low Pressure Side   | 0.1 bar    |
| 7       | B7        | High Pressure Side  | 0.1 bar    |
| 8       |           | Flow                | 0.1 m3/h   |
| 9       |           | Room Temperature    | 0.1°C      |
|         |           |                     |            |
| 13      |           | Compressor          | 1 Hz       |
|         |           |                     |            |
| 17      | B4        | Hot Water           | 0.1°C      |
| 18      |           | Operating Hours     | 1 Hour     |
|         |           |                     |            |
| 20      |           | Unit State          | unit_state |

### Holding Register (read-write)


| Address | Parameter | Value                                                              | default | min  | max  | unit  | Access       |
| ------- | --------- | ------------------------------------------------------------------ | ------- | ---- | ---- | ----- | ------------ |
| 9       |           | Room Temperature                                                   |         |      |      | 0.1°C |              |
|         |           |                                                                    |         |      |      |       |              |
| 61      | ST01      | Temperature on cooling mode                                        | 13      | ST11 | ST12 | 0.1°C | User         |
| 62      | ST02      | Temperature on heating mode                                        | 35      | ST13 | ST14 | 0.1°C | User         |
| 63      | ST03      | Temperature difference on cooling mode                             | 1       | 1    | 10   | 0.1°C | User         |
| 64      | ST04      | Temperature difference on heating mode                             | 1       | 1    | 10   | 0.1°C | User         |
| 65      | ST06      | Compensation factor for heating curve                              | 0.6     | 0    | 3    | 0.1   | User         |
| 66      | ST07      | Ambient temperature condition for starting aux heat                | 0       | -10  | 20   | 0.1°C | User         |
| 67      | ST08      | Compensation factor for cooling curve                              | 0.6     | 0    | 3    | 0.1   | User         |
| 68      | ST11      | Minimum settable cooling temperature                               | 12      | 0    | ST12 | 0.1°C | Manufacturer |
| 69      | ST12      | Maximum settable cooling temperature                               | 40      | ST11 | 60   | 0.1°C | Manufacturer |
| 70      | ST13      | Minimum settable heating temperature                               | 20      | 0    | ST14 | 0.1°C | Manufacturer |
| 71      | ST14      | Maximum settable heating temperature                               | 50      | ST13 | 8    | 0.1°C | Manufacturer |
| 72      | ST15      | Minimum settable DHW temperature                                   | 20      | 0    | ST16 | 0.1°C | Manufacturer |
| 73      | ST16      | Maximum settable DHW temperature                                   | 65      | ST15 | 80   | 0.1°C | Manufacturer |
| 74      | ST17      | SG Function: Cooling/heating water temperature decrement/increment | 2       | 1    | 10   | 0.1°C | User         |
| 75      | ST18      | SG Function: DHW temperature increment                             | 5       | 1    | 10   | 0.1°C | User         |
|         |           |                                                                    |         |      |      |       |              |
| 77      | ST33      | DHW circulation pump off interval                                  | 15      | 0    | 180  | 1 min | User         |
| 78      | ST34      | DHW circulation pump running time                                  | 3       | 0    | 180  | 1 min | User         |
| 79      | ST09      | DHW temperature setup                                              | 50      | ST15 | ST16 | 0.1°C | User         |

### Convertion Tables

#### unit_state

| value | state      |
| ----- | ---------- |
| 1     | Heating    |
| 2     | Cooling    |
| 3     | antifreeze |
| 4     | Defrost    |
| 5     | Standby    |
| 6     | Off        |
| 7     | Starting   |
| 8     | On         |
| 9     | DHW        |
