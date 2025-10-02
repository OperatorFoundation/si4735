project(si4735-arduino)
set(SI4735_ARDUINO_EXAMPLES_DIR ${SI4735_ARDUINO_DIR}/examples)
set(SI4735_ARDUINO_EXAMPLE_DIR ${SI4735_ARDUINO_EXAMPLES_DIR}/si4735-arduino)
set(SI4735_ARDUINO_SOURCE_DIR ${SI4735_ARDUINO_DIR}/src)
set(IOTA_CPP_SOURCE_DIR ${IOTA_CPP_DIR}/src)
set(IOTA_ARDUINO_SOURCE_DIR ${IOTA_ARDUINO_DIR}/src)
set(ION_CPP_SOURCE_DIR ${ION_CPP_DIR}/src)
set(ION_ARDUINO_SOURCE_DIR ${ION_ARDUINO_DIR}/src)
set(TRANSMISSION_CPP_SOURCE_DIR ${TRANSMISSION_CPP_DIR}/src)

include_directories(${SI4735_ARDUINO_SOURCE_DIR} ${SI4735_DIR}/src ${IOTA_CPP_SOURCE_DIR} ${IOTA_ARDUINO_SOURCE_DIR} ${ION_CPP_SOURCE_DIR} ${ION_ARDUINO_SOURCE_DIR} ${TRANSMISSION_CPP_SOURCE_DIR})

# Define your sketch file
set(SKETCH_FILE ${SI4735_ARDUINO_EXAMPLE_DIR}/si4735-arduino.ino)
set(BOARD "esp32:esp32:esp32s3")
set(PORT "/dev/cu.usbmodem1101")
set(OUTPUT_DIR ${CMAKE_BINARY_DIR}/arduino/si4735-arduino)

file(GLOB_RECURSE SI4735_FILES ${SI4735_ARDUINO_SOURCE_DIR}/*.cpp)

add_custom_target(build_si4735_arduino ALL
        COMMAND arduino-cli compile
            --fqbn ${BOARD}
            --output-dir ${OUTPUT_DIR}
            --build-property "compiler.cpp.extra_flags=-std=c++17 -D_BSD_SOURCE -D_DEFAULT_SOURCE"
            --library ${SI4735_DIR}
            --library ${IOTA_CPP_DIR}
            --library ${IOTA_ARDUINO_DIR}
            --library ${ION_CPP_DIR}
            --library ${ION_ARDUINO_DIR}
            --library ${TRANSMISSION_CPP_DIR}
            --library ${SI4735_ARDUINO_DIR}
            ${SKETCH_FILE}
        WORKING_DIRECTORY ${SI4735_ARDUINO_SOURCE_DIR}
        COMMENT "Building si4735-arduino with arduino-cli"
)

add_custom_target(upload_si4735_arduino
        COMMAND arduino-cli upload
        -p ${PORT}
        --fqbn ${BOARD}
        ${SI4735_ARDUINO_EXAMPLE_DIR}
        COMMENT "Uploading si4735-arduino with arduino-cli"
)

add_dependencies(upload_si4735_arduino build_si4735_arduino)
