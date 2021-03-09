# mqttbroker-rpi-install

This repository describe how to use a Raspberry-Pi to install a local MQTT Broker, use it and test it by using a Python script. You will find here a procedure to install a local MQTT BRoker on your raspberry Pi using [mosquitto](https://mosquitto.org) and running a Python sample that you can edit with text editor like Notepad or [Notepad++](https://notepad-plus-plus.org/downloads/) or IDE like [Visual Studio Code](https://code.visualstudio.com/download) or other. 

- [Prerequist](#prerequist)
- [Mosquitto](#mosquitto)
- [Sample](#sample)

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

# Mosquitto
Eclipse Mosquitto is an open source (EPL/EDL licensed) message broker that implements the MQTT protocol. To install Mosquitto on a raspberry device, you can follow the following procedure. To proceed:
```bash
  sudo apt update
  sudo apt install -y mosquitto mosquitto-clients
```

Accept and ENTER Yes / Y if the installation program ask your agreement. Then, to start the program at each startup, you can use systemctl to proceed by enterring the following command:
```bash
  sudo systemctl enable mosquitto.service
```

To test the installation, just enter the following command to get the version :
```bash
  mosquitto -v
```
# Sample
To test the broker, you can use the python file **testmqtt.py** to subscribe to a general topic and display the information received form the Broker. This program instanciate a MQTT Client on topic "#" and print the information received. The default address in the program is the localhost IP Adress, but you can chane it if you install **Mosquitto** on another device on your network.

The main program is here to check your input parameter and run the MQTT client using **Paho.MQTT**. The following python lines are necessary to create your MQTT Client, associate the callback function, and connect ti the broker:
```python
  #
  client = mqtt.Client()
  client.on_connect = on_connect
  client.on_message = on_message

  client.connect("127.0.0.1", 1883, 60)
```

We subscribe to the "#" topic, this mean that all message received from the broker will be visible in the **on_message** function. This subscribtion append in the **on_connect** function:
```python
  # Subscribing in on_connect() means that if we lose the connection and
  # reconnect then subscriptions will be renewed.
  client.subscribe("#")
```

Now you can use directly your temrminal and Mosquitto to publich something on your broker. To proceed, enter the following command line to Publish directly on your broker and then, the result will display in the reveive part of your **testmqtt.py** program.
