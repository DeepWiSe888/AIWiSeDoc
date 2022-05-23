---
sort: 2
---

# Sleep-Tracker
## 1 Introduction
Track your sleep accurately without the discomfort of a wristband or electrode wires.
* Some Problem  
  CDC has recently classified insufficient sleep as a public health problem. Sleepiness is the root cause of increasing the risk of accidents and other occupational errors. It can also cause health concerns such as diabetes, depression and high blood pressure.
  According to a recent survey by the National Sleep Foundation and the Consumer Electronics Association, more than 60% of sleep tracking technology owners are more aware of their sleep patterns after sleep tracking. 51% of sleep tracking technology owners say they’re sleeping better knowing the technology is helping them and 49% say they feel healthier since they started using the technology.
  Although most of the sleep tracking technologies are non-invasive devices such as watches and bands, they still require huge amounts of daily maintenance for hygiene and constant battery charging. The discipline of frequent charging and hygiene maintenance using the wearable device has turned a lot of people away from using them.
* The Solution  
  Using Sleep-Tracker, we can build a non-invasive sleep tracking system that's always on. This way the User does not have to worry about charging their wearables, washing for hygiene and still be able to track a good night's sleep.

## 2 Hardware components
* **Raspberry Pi 3B+**
* **UWB Radar Module**

We provide hardware package.[Contact Us](https://www.wirush.ai/aiwise-contact)

## 3 Quick Started guide
If you are using the hardware package provided by us,to to [3.3](#33-connect-the-device-to-the-pc) 

#### 3.1 Connect your device
Connect the device as shown:
<div align=center>
<img src="https://raw.githubusercontent.com/DeepWiSe888/AIWiSeDoc/main/img/sleepTracker1.png" width="320" height="250"/> 
</div>
<center>Figure 1. Device Connection</center>



  
#### 3.2 Installation SDK on Raspberry Pi
Skip this step if you are using the hardware package provided by us  because it already has SKD installed.
If you buy equipment by yourself,you need to install the radar SDK on Raspberry Pi. To do this you first grab the installer for Raspberry Pi from [this page](https://github.com/DeepWiSe888/X4DriverForRaspberryPi).Then follow the [readme](https://github.com/DeepWiSe888/X4DriverForRaspberryPi/blob/main/Readme.md) found on this page in order to run it and complete the installation of the radar SDK:

```shell
git clone https://github.com/DeepWiSe888/X4DriverForRaspberryPi.git
make 
./Runme
```
Now,radar data will be printed out.

#### 3.3 Connect the device to the PC
* Use USB-to-Ethernet to connect Raspberry PI to PC
* Change the IP address of the network adapter:
  ```
  192.168.1.111
  ```
<div align=center>
<img src="https://raw.githubusercontent.com/DeepWiSe888/AIWiSeDoc/main/img/sleepTracker2.jpg" width="405" height="455"/> 
</div>
<center>Figure 2.IP Address</center>

#### 3.4 Building the development environment and Run the demo
* Pull the code
  ```shell
  git clone https://github.com/DeepWiSe888/Sleep-Tracker.git
  ```
* Install dependent libraries(python 3.6+):
  ```shell
  pip install -r requirements.txt -i https://pypi.mirrors.ustc.edu.cn/simple/
  ```
* Run plot data program in terminal:
  ```shell
  python sleep-tracker.py
  ```
Figure.3 is a simulation of the process From waking to deep sleep, waking from deep sleep.
<div align=center>
<img src="https://raw.githubusercontent.com/DeepWiSe888/AIWiSeDoc/main/img/sleepTracker3.jpg" width="785" height="950"/> 
</div>
<center>Figure 3.Sleep-Tracker</center>

## 4 Challenges and Future Work
Accuracy needs improvement.

## 5 Code
All of the project code can be found on GitHub :[Sleep-Tracker](https://github.com/DeepWiSe888/Sleep-Tracker).

