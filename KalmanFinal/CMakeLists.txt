cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(my_project)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project

add_executable(Inverted_Pendulum_Kalman
    Inverted_Pendulum_Kalman.cpp
)

# Add pico_stdlib library which aggregates commonly used features
target_compile_options(Inverted_Pendulum_Kalman PUBLIC -O2 -Wall)

target_link_libraries(Inverted_Pendulum_Kalman pico_stdlib hardware_i2c hardware_pwm pico_multicore)

pico_enable_stdio_usb(Inverted_Pendulum_Kalman 0)
pico_enable_stdio_uart(Inverted_Pendulum_Kalman 1)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(Inverted_Pendulum_Kalman)
