cmake_minimum_required(VERSION 3.13)

# initialize the SDK based on PICO_SDK_PATH
# note: this must happen before project()
include(pico_sdk_import.cmake)

project(my_project)

# initialize the Raspberry Pi Pico SDK
pico_sdk_init()

# rest of your project

add_executable(Inclinometer
    Inclinometer.cpp
)

# Add pico_stdlib library which aggregates commonly used features
target_compile_options(Inclinometer PUBLIC -O2 -Wall)

target_link_libraries(Inclinometer pico_stdlib hardware_i2c)

pico_enable_stdio_usb(Inclinometer 1)
pico_enable_stdio_uart(Inclinometer 0)

# create map/bin/hex/uf2 file in addition to ELF.
pico_add_extra_outputs(Inclinometer)
