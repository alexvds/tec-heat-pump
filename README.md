# TEC Heat pump

Information about the TEC QRS11 heat pump.

## RS-485 (modbus)

| Type     | Value |
| -------- | ----- |
| Baudrate | 9600  |
| Databits | 8     |
| Stopbits | 2     |
| Parity   | even  |

### Discrete output (coil / read-write)

| Address | Value      |
| ------- | ---------- |
| 1       | A/C Switch |
| 2       | DHW Switch |

### Discrete input (read-only)

| Address | Value          |
| ------- | -------------- |
| 25      | Secondary Pump |
| 27      | Primary Pump   |
| 32      | A/C Heater     |
| 36      | DHW Heater     |
| 39      | Gas boiler     |

### Input register (read-only)

| Address | Value               | unit       |
| ------- | ------------------- | ---------- |
| 1       | Inlet Temperature   | 0.1°C      |
| 2       | Outlet Temperature  | 0.1°C      |
| 3       | Ambient Temperature | 0.1°C      |
| 4       | Suction             | 0.1°C      |
| 5       | Discharge           | 0.1°C      |
| 6       | Low Pressure Side   | 0.1 bar    |
| 7       | High Pressure Side  | 0.1 bar    |
| 8       | Flow                | 0.1 m3/h   |
| 9       | Room Temperature    | 0.1°C      |
| 13      | Compressor          | 1 Hz       |
| 17      | Hot Water           | 0.1°C      |
| 20      | Unit State          | unit_state |

### Holding Register (read-write)


| Address | Parameter | Value                                               | unit  |
| ------- | --------- | --------------------------------------------------- | ----- |
| 9       |           | Room Temperature                                    | 0.1°C |
| 61      | ST01      | Temperature on cooling mode                         | 0.1°C |
| 62      | ST02      | Temperature on heating mode                         | 0.1°C |
| 63      | ST03      | Temperature difference on cooling mode              | 0.1°C |
| 64      | ST04      | Temperature difference on heating mode              | 0.1°C |
| 65      | ST06      | Compensation factor for heating curve               | 0.1   |
| 66      | ST07      | Ambient temperature condition for starting aux heat | 0.1°C |
| 67      | ST08      | Compensation factor for cooling curve               | 0.1   |
| 79      | ST33      | DHW circulation pump off interval                   | 1 min |
| 79      | ST34      | DHW circulation pump running time                   | 1 min |
| 79      | ST09      | DHW Setup                                           | 0.1°C |

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
