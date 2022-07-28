---
sort: 2
---
# FMCW Software

## 1 &emsp;Basic radar parameters

| Parameter       | Value   | Unit | Comment                                                      |
| --------------- | ------- | ---- | ------------------------------------------------------------ |
| C               |   3*10<sup>8<sup>     |  m/s    | Speed of light                                               |
| sweep_time      | 0.0005  | s    | Sweep time                                                   |
| Sweep Frequency | 2~4 or 5.2~8.2	 | GHz  |                                                              |
| B               | 2 or 3       | GHz  | Bandwidth                                                   |
| S               |      |      | S = B / sweep_time                                           |
| IF              | 1       | MHz  | adc sample,IF frequency                                      |
| maximum range   |       | m    | IF / 2 * c / (2 * S), according to the Nyquist theorem,so IF / 2 |
| if_offset       |      | KHz  | Zero point estimation, due to the influence of signal cable length |

## 2 &emsp;Operations before power-on

* The transmitter antenna and receiver antenna are connected to the corresponding ports of the device.
* The transmitter must not be empty before powered on.
* Check whether the control bus is connected.
* Check whether the synchronization signal cable is connected.
* Check whether  the IF signal line is connected.
* Check whether the VGA voltage control is connected.
* Power on FPGA(must be power on before radar, because the output VGA voltage is unstable when it is just powered on).  
* Power on Radar.
* Use the Ethernet cables to connect FPGA with computer.

## 3 &emsp;Packet Parsing

Each frame contains flag、tx no、rx no、frame no adc data.

| No   | field       | data type          | packet size | description                                                  |
| ---- | ----------- | ------------------ | ----------- | ------------------------------------------------------------ |
| 1    | packet flag |                    | 12          | The flag of each packet                                      |
| 2    | timestamp   | unsigned long long | 8           | The timestamp,if you parse packet from a file,otherwise,the field is None |
| 3    | tx          | unsigned short     | 2           | The transmitter antenna No                                   |
| 4    | rx          | unsigned short     | 2           | The receiver antenna No                                      |
| 5    | frame no    | unsigned long      | 4           | The frame No                                                 |
| 6    | adc data    | unsigned char      | 1           | adc data                                                     |

## 4 &emsp;Process Parameters

| Parameter          | Value | Unit | Comment                                   |
| ------------------ | ----- | ---- | ----------------------------------------- |
| num_tx             |       |      | the number of tx                          |
| num_rx             |       |      | the number of rx                          |
| loop_size          |       |      | data size after traversing each antenna   |
| num_loop_per_frame |       |      | the number of loops each  frame           |
| frame_size         |       |      | the data length of each processing window |
| num_range_nfft     | 512   |      | the number of points of range fft         |
| num_doppler_nfft   | 64    |      | the number of points of doppler fft       |
| num_angle_nfft     | 180   |      | the number of points of angle fft         |



## 5 &emsp;About the repository

#### 5.1 Install Dependencies

   ```shell
   pip install -r requirements.txt -i https://pypi.mirrors.ustc.edu.cn/simple/
   ```

#### 5.2 Changing the  IP Address

   * The FPGA default IP address is  "192.168.0.2",default port is 5000;By default ,it send to the IP address "192.168.0.3" and port 6000.
   * So modify the localhost IP address to "192.168.0.3".


#### 5.3 Select the antenna number you want to use by modifying txs list and rxs list

   ```python
   local_udp_ip = "192.168.0.3"
   local_udp_port = 6000
   fpga_udp_ip = "192.168.0.2"
   fpga_udp_port = 5000
   
   # FPGA use antenna no
   txs = [3,4]
   rxs = [1,2,3,4,5,6,7,8,9,10]
   
   r = Receive(local_udp_ip,local_udp_port,fpga_udp_ip,fpga_udp_port)
   msg,result = r.setting(txs,rxs)
   ```

#### 5.4 Plot data real time

   ```shell
   python plot_data_real_time.py
   ```

#### 5.5 Save raw data to file,

   * You can run the following script if you want to save the data locally,and the file will be saved in './data/'.

      ```shell
      python receiving_data_and_save.py
      ```

   * This script saves the local time for easy time synchronization.


#### 5.6 Plot data from file

   ```shell
   python plot_data_from_file.py
   ```

## 6 &emsp;Algorithm processing flow

1. Range FFT
2. Remove DC
3. Doppler FFT
4. Angle FFT
5. Find the target
6. Point cloud
7. Point cloud clustering

## 7 &emsp;FQA

1. How does the antenna switch work?

   If the working tx antennas is [1,2],rx antennas is [1,2,3,4,5], and the switching order is:tx1,rx1,rx2,rx3,rx4,rx5,tx2,rx1,rx2,rx3,rx4,rx5.

