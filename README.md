# WeTron MQTT Backend

## Installation of dependencies

```bash
apt-get install build-essential gcc make cmake cmake-gui cmake-curses-gui
```

## Optional Installation of dependencies for documentation

```bash
apt-get install doxygen graphviz
```

## Installation of paho.mqtt.c and paho.mqtt.cpp

```bash
git clone https://github.com/eclipse/paho.mqtt.cpp
cd paho.mqtt.cpp
./install_paho_mqtt_c.sh
mkdir build
cd build
cmake -DPAHO_BUILD_DOCUMENTATION=TRUE -DPAHO_BUILD_SAMPLES=TRUE -DPAHO_MQTT_C_PATH=../../paho.mqtt.c ..
make
sudo make install

sudo ldconfig
```
