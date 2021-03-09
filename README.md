# mqttbroker-rpi-install

This repository describe how to use a Raspberry-Pi to install a local MQTT Broker, use it and test it by using a Python script. You will find here a procedure to install a local MQTT BRoker on your raspberry Pi using [mosquitto](https://mosquitto.org) and running a Python sample that you can edit with text editor like Notepad or [Notepad++](https://notepad-plus-plus.org/downloads/) or IDE like [Visual Studio Code](https://code.visualstudio.com/download) or other. 

# Prerequist
Before starting to use the program, it's necessary to install the requiered components to start your integration for this example and get data from Blue MESH tags. You need:
- Python 3.7
- git
- paho-mqtt

First of all be sure that your raspberry is up to date by executing the following commands:
```bash
   sudo apt-get update
```

## Install Python
Then install python 3.7; you may need to use pip3:
```bash
   sudo apt-get install python3-pip libglib2.0-dev
```

## Install Git
If you have not yet install git, please do it by enterring the following command line:
```bash
   sudo apt-get install git
```

## Install Paho MQTT
The latest stable version is available in the Python Package Index (PyPi) and can be installed using:
```bash
  pip3 install paho-mqtt
```

To obtain the full code, including examples and tests, you can clone the git repository:
```bash
  git clone https://github.com/eclipse/paho.mqtt.python
```

Once you have the code, it can be installed from your repository as well:
```bash
  cd paho.mqtt.python
  python setup.py install
```

There, you're ready to use the MQTT tools and start to develop your project wit the Paho Mqtt layer.
