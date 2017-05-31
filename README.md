# wetron-mqtt-backend

## Installation of paho.mqtt.c and paho.mqtt.cpp

git clone https://github.com/eclipse/paho.mqtt.cpp
cd paho.mqtt.cpp
./install_paho_mqtt_c.sh
mkdir build
cd build
cmake -DPAHO_BUILD_DOCUMENTATION=TRUE -DPAHO_BUILD_SAMPLES=TRUE -DPAHO_MQTT_C_PATH=../../paho.mqtt.c ..
make
sudo make install

sudo ldconfig
