cmake_minimum_required(VERSION 3.0)
project(WeTronMqttBackend)

include(ExternalProject)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11")

set(EXTERNAL_INSTALL_LOCATION ${CMAKE_BINARY_DIR}/external)

ExternalProject_Add(paho.mqtt.c
    GIT_REPOSITORY https://github.com/eclipse/paho.mqtt.c
    GIT_TAG develop
    CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${EXTERNAL_INSTALL_LOCATION} -DPAHO_BUILD_STATIC=TRUE -DPAHO_WITH_SSL=ON
)

ExternalProject_Add(paho.mqtt.cpp
    GIT_REPOSITORY https://github.com/eclipse/paho.mqtt.cpp
    CMAKE_ARGS -DCMAKE_INSTALL_PREFIX=${EXTERNAL_INSTALL_LOCATION} -DPAHO_BUILD_STATIC=TRUE -DPAHO_WITH_SSL=ON -DPAHO_MQTT_C_PATH=${EXTERNAL_INSTALL_LOCATION}
)

add_dependencies(paho.mqtt.cpp
    paho.mqtt.c
)

include_directories(${EXTERNAL_INSTALL_LOCATION}/include)
link_directories(${EXTERNAL_INSTALL_LOCATION}/lib)

# async_consume
add_executable(async_consume
    samples/async_consume.cpp
)
add_dependencies(async_consume
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(async_consume
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# async_publish
add_executable(async_publish
    samples/async_publish.cpp
)
add_dependencies(async_publish
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(async_publish
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# async_subscribe
add_executable(async_subscribe
    samples/async_subscribe.cpp
)
add_dependencies(async_subscribe
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(async_subscribe
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# data_publish
add_executable(data_publish
    samples/data_publish.cpp
)
add_dependencies(data_publish
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(data_publish
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# pub_speed_test
add_executable(pub_speed_test
    samples/pub_speed_test.cpp
)
add_dependencies(pub_speed_test
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(pub_speed_test
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# ssl_publish
add_executable(ssl_publish
    samples/ssl_publish.cpp
)
add_dependencies(ssl_publish
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(ssl_publish
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# sync_consume
add_executable(sync_consume
    samples/sync_consume.cpp
)
add_dependencies(sync_consume
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(sync_consume
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# sync_publish
add_executable(sync_publish
    samples/sync_publish.cpp
)
add_dependencies(sync_publish
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(sync_publish
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)

# sync_subscribe
add_executable(sync_subscribe
    samples/sync_subscribe.cpp
)
add_dependencies(sync_subscribe
    paho.mqtt.c
    paho.mqtt.cpp
)
target_link_libraries(sync_subscribe
    libpaho-mqttpp3-static.a
    libpaho-mqtt3as-static.a
    pthread
    ssl
    crypto
)
