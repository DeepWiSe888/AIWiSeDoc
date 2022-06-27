---
sort: 2
---
# AW-UWB-EV-02 API

## 1 Usb serial communication

1. Transmission mode: serial USB, Ethernet.  
2. Each frame contains 1124 bytes, and each field is sequentially concatenated. 
3. Description of packet content and format(json):  

| NO   | Field                 | Type         | Data Length   |Packet Size    | Description                  |
| ---- | ----------------------| ------------ | -----------   | --------------| -----------------------------|
| 1    | sec                   | int          | 4             | 4             | integral part of second      |
| 2    | usec                  | int          | 4             | 4             | fractional part of second    |
| 3    | tx no                 | int          | 4             | 4             | tx antenna no default 0      |
| 4    | rx no                 | int          | 4             | 4             | rx antenna no default 0      |
| 5    | frame no              | int          | 4             | 4             | frame no                     |
| 6    | I channel signal      | float        | 4             | 138 * 4       | i data                       |
| 7    | Q channel signal      | float        | 4             | 138 * 4       | q data                       |

#### [AW-UWB-EV-02 Toolbox](https://github.com/DeepWiSe888/Toolbox)