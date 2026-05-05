cmake_minimum_required(VERSION 3.6)
set(PROJECT_NAME "serialport")
project(${PROJECT_NAME} LANGUAGES C)

set(SOURCE_PATH "../../third_party/libserialport")

add_library(${PROJECT_NAME} SHARED
  "${SOURCE_PATH}/linux.c"
  "${SOURCE_PATH}/linux_termios.c"
  "${SOURCE_PATH}/serialport.c"
  "${SOURCE_PATH}/timing.c"
)

target_compile_options(${PROJECT_NAME} PRIVATE
  -std=c99 -Wall -Wextra -pedantic -Wmissing-prototypes -Wshadow)
target_compile_definitions(${PROJECT_NAME} PRIVATE LIBSERIALPORT_ATBUILD)
target_include_directories(${PROJECT_NAME} PRIVATE
  "${CMAKE_CURRENT_SOURCE_DIR}"
  "${CMAKE_CURRENT_SOURCE_DIR}/${SOURCE_PATH}")

# Align ELF LOAD segments to 16 KB so the .so loads on Android 15+ devices
# configured with 16 KB memory pages (mandatory from Android 16). Default
# behavior for NDK r27+ — set explicitly so older NDKs also produce
# 16 KB-aligned binaries.
if(ANDROID)
  target_link_options(${PROJECT_NAME} PRIVATE "-Wl,-z,max-page-size=16384")
endif()
