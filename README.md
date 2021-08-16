This package provides an abstraction layer and API engine for the [RPi.GPIO](https://pypi.org/project/RPi.GPIO/) package for python, which allows for multi-process and **non-blocking** control of GPIO pins.
With this package you can start the GPIO Engine, and control the output pins for relay control/ actuation using a json configuration files, while your code performs other
operations. This allows for relative _real time control*_ of the GPIO pins(~<1s scale). This package also provides real-time api of the status for external logging or
communication.Using the JSON protocol for the api we can allow for user control and information logging. For now this package only handles GPIO output but will feature
input control in the near future.

___*Note:___ while this package provides multi-process control of the GPIO pins for near real-time control, jitter can vary considerably due to the nature of Linux OS and
python's garbage collection. For now refresh rate is by default set to 1 second to mitigate issue of jitter to a known scale, but we cannot guarantee performance if  refresh rate is set to 0.

- Documentation: *Coming soon*
- [GitLab](https://gitlab.com/moha7108/rpi-control-center)


## Installation
- pip
```shell
pip install rpi_control_center
```
- source
```shell
git clone https://gitlab.com/moha7108/rpi-control-center.git
cd rpi-control-center
pip install -r requirements.txt
```
## Example Usage

```python
import time
from rpi_control_center import GPIO_engine

control_box = GPIO_engine()

control_box = BulkUpdater(
                            config_file = './relay_config.json',
                            default_config = default_relay_config ,
                            refresh_rate = 1
                          )
control_box.start()

######### You can put any code because this function is non-blocking
try:
    while True:
        time.sleep(5)
except:
    control_box.stop()
```

## Feedback

All kinds of feedback and contributions are welcome.

- [Create an issue](https://gitlab.com/moha7108/rpi-control-center/-/issues)
- Create a pull request
- reach out to @moha7108

## Contributors

- Mohamed Debbagh
  - [GitLab](https://gitlab.com/moha7108/), [Github](https://github.com/moha7108/), [Twitter](https://twitter.com/moha7108), [Intsagram](https://www.instagram.com/moha7108/)


## Change Log

### 0.1.0
-
-
-
-


## Hardware and drivers

### Hardware

- Raspberrypi 3B+

### System Libraries

[waveshare guide](https://www.waveshare.com/wiki/Libraries_Installation_for_RPi)]
``` shell
cd
sudo apt update
sudo apt list --upgradeable
sudo apt ugrade
sudo apt autoremove

sudo apt-get install wiringpi
wget https://project-downloads.drogon.net/wiringpi-latest.deb
sudo dpkg -i wiringpi-latest.deb
gpio -v
sudo apt-get install libopenjp2-7 -y
sudo apt-get install libatlas-base-dev -y
sudo apt install libtiff -y
sudo apt install libtiff5 -y
sudo apt-get install -y i2c-tools
```
## Issues
- MQTT communication for UI control

### resolved
- Service file
- json files for api
- Logging over print statements (log files)
- Turn this into a class structure for replicability/ abstraction (objectify)
- Nonblocking starting functionality for module
- error handling
- add liscence
