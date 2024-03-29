---
sort: 1
---
# AW-UWB-EV-01 API

## 1 Usb serial communication

1. Transmission mode: serial USB.  
2. 1 packet per second.  
3. Description of packet content and format(json):  

| NO   | Field   | Type         | Length |Value   | Description                   |
| ---- | ------- | ------------ | -----  | ----- | -------------------------------|
| 1    | deviId  | string       | --     |       | Device id                      |
| 2    | version | string       | --     |       | Device version                 |
| 3    | t       | string       | --     |       | Timestamp                      |
| 4    | e       | int          | 1      | 0/1   | Existential state              |
| 5    | d       | float        | --     |       | Distance                       |
| 6    | fm      | float        | --     | 0~100 | Fast motion quantization       |
| 7    | sm       | float       | --     | 0~100 | Slow motion quantization       |
| 8    | r       | float        | --     |       | Respiration per minute         |
| 9    | b       | float        | --     |       | Heart beats  per minute       |
| 10   | rw      | [float,....] | 20*17  |       | Raw waveform,20s,fps=17        |
| 11   | rcw     | [float,....] | 20*17  |       | Respiration wavefoem,20s,fps=17|


## 2 Websocket communication
1. Transmission mode: websocket.  
2. 1 packet per second.  
3. Description of packet content and format(json): 

| NO   | Field           | Type             | Description                     |
| ---- | -------         | ------------     | ------------------------------- |
| 1    | cmd             | string           | UpdateDashboard                 |
| 2    | respirationRate | int              | Respiration per scecond         |
| 3    | heartRate       | int              | Heart beats per scecond         |
| 4    | time            | long             | The timestamp of the last valid data |
| 5    | deviceName      | string           | Device name                     |
| 6    | fastmove        | float            | Fast motion quantization        |
| 7    | slowmove        | float            | Slow motion quantization        |
| 8    | range           | float            | Distance                        |
| 9    | exist           | bool             | Existential state               |
| 10   | deviceid        | string           | Device id                       |

#### [AW-UWB-EV-01 Toolbox](https://github.com/DeepWiSe888/AW-UWB-EV-01)