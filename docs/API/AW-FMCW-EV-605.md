---
sort: 4
---
# AW-FMCW-EV-605 API

## 1 Usb serial communication

1. Transmission mode: serial USB.  
2. 1 packet per second.  
3. Description of packet content and format(json):  

Each frame contains 1124 bytes, and each field is sequentially concatenated  

| NO   | field    | data type | data type size | packet size                                                  | value | description               |
| ---- | -------- | --------- | -------------- | ------------------------------------------------------------ | ----- | ------------------------- |
| 1    | flage    |           |                |                                                              |       |                           |
| 2    | sec      | long      | 8              | 8                                                            |       | integral oart of second   |
| 3    | usec     | long      | 8              | 8                                                            |       | fractional part of second |
| 4    | rx no    | int       | 4              | 4                                                            |       | rx antenna no default 1   |
| 5    | tx no    | int       | 4              | 4                                                            |       | tx antenna no default 1   |
| 6    | frame no | int       | 4              | 4                                                            |       | frame no                  |
| 7    | adc      | float     | 4              | num_tx * num_rx * num_chirps_per_frame * num_samples_per_chirp * 4 |       | adc data                  |


#### [AW-FMCW-EV-605 Toolbox](https://github.com/DeepWiSe888/AW-FMCW-EV-605)