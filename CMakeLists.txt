cmake_minimum_required(VERSION 3.22)

#
# This file is generated only once,
# and is not re-generated if converter is called multiple times.
#
# User is free to modify the file as much as necessary
#

# Setup compiler settings
set(CMAKE_C_STANDARD 11)
set(CMAKE_C_STANDARD_REQUIRED ON)
set(CMAKE_C_EXTENSIONS ON)


# Define the build type
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE "Debug")
endif()

# Set the project name
set(CMAKE_PROJECT_NAME Discovery)

# Enable compile command to ease indexing with e.g. clangd
set(CMAKE_EXPORT_COMPILE_COMMANDS TRUE)

# Core project settings
project(${CMAKE_PROJECT_NAME})
message("Build type: " ${CMAKE_BUILD_TYPE})

# Enable CMake support for ASM and C languages
enable_language(C ASM)

# Create an executable object type
add_executable(${CMAKE_PROJECT_NAME})

# Add STM32CubeMX generated sources
add_subdirectory(cmake/stm32cubemx)

# Link directories setup
target_link_directories(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user defined library search paths
    ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/STM32_Audio/Addons/PDM/Lib
)

# Add sources to executable
target_sources(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user sources here
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/otm8009a/otm8009a.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/cs43l22/cs43l22.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/ft6x06/ft6x06.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/nt35510/nt35510.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_lcd.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_audio.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_sd.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_ts.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_eeprom.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_qspi.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery/stm32469i_discovery_sdram.c
    ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Log/lcd_log.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts/font8.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts/font12.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts/font16.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts/font20.c
    # ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts/font24.c
)
# Add include paths
target_include_directories(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user defined include paths
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/Common
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/otm8009a
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/cs43l22
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/ft6x06
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/nt35510
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/Components/n25q128a
    ${CMAKE_CURRENT_SOURCE_DIR}/Drivers/BSP/STM32469I-Discovery
    ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/STM32_Audio/Addons/PDM/Inc
    ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Log
    ${CMAKE_CURRENT_SOURCE_DIR}/Middlewares/ST/Fonts
)

# Add project symbols (macros)
target_compile_definitions(${CMAKE_PROJECT_NAME} PRIVATE
    # Add user defined symbols
)

# Remove wrong libob.a library dependency when using cpp files
list(REMOVE_ITEM CMAKE_C_IMPLICIT_LINK_LIBRARIES ob)

# Add linked libraries
target_link_libraries(${CMAKE_PROJECT_NAME}
    stm32cubemx

    # Add user defined libraries
)
