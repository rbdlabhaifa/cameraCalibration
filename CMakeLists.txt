cmake_minimum_required(VERSION 3.16)
project(calibration)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall   -O3 -ltbb")

find_package(Threads REQUIRED)
find_package(nlohmann_json 3.2.0)

find_package(OpenCV 3.0 QUIET)
add_executable(cameraCalibration
        calibration.cpp)
target_link_libraries(cameraCalibration nlohmann_json::nlohmann_json ${OpenCV_LIBS} Threads::Threads)

add_executable(telloCalibration
        telloCalibration.cpp)
target_link_libraries(telloCalibration nlohmann_json::nlohmann_json ${OpenCV_LIBS} ctello Threads::Threads)
