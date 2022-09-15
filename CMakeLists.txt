cmake_minimum_required(VERSION 3.5)

project(canary_vendor)

find_package(ament_cmake REQUIRED)

macro(build_canary)
  include(ExternalProject)

  externalproject_add(canary
    URL https://github.com/djarek/canary/archive/8f2a9612b197552afa3702422fc8521095ffb1bc.zip
    URL_HASH SHA256=e4ac33fb106568e5cc82e395cd873b8bb48b89e5708ffa24674bcae1a5666e5b
    BUILD_IN_SOURCE True
    DOWNLOAD_DIR ${CMAKE_CURRENT_SOURCE_DIR}
    SOURCE_DIR source
    CONFIGURE_COMMAND ""
    BUILD_COMMAND ""
    INSTALL_COMMAND ""
  )

  install(
    DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/source/include/
    DESTINATION include
  )
endmacro()

build_canary()

ament_export_include_directories(include)
# this ensures that the package has an environment hook setting the PATH
ament_package()
