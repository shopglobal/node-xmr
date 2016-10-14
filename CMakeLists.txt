cmake_minimum_required(VERSION 3.0)
include(ExternalProject)

project(node-xmr)
ExternalProject_Add(Monero
                    SOURCE_DIR ${CMAKE_SOURCE_DIR}/src/contrib/monero-0.10.0
                    DOWNLOAD_COMMAND ""
                    UPDATE_COMMAND ""
                    CMAKE_ARGS
                       -DCMAKE_INSTALL_PREFIX=<INSTALL_DIR>
                       -DCMAKE_BUILD_TYPE=${CMAKE_BUILD_TYPE}
                    INSTALL_COMMAND "")

file(GLOB SOURCE_FILES "src/*.cpp" "src/*.h")
add_library(${PROJECT_NAME} SHARED ${SOURCE_FILES})

set_target_properties(${PROJECT_NAME} PROPERTIES PREFIX "" SUFFIX ".node")

target_include_directories(${PROJECT_NAME} PRIVATE ${CMAKE_JS_INC})
target_link_libraries(${PROJECT_NAME} ${CMAKE_JS_LIB})