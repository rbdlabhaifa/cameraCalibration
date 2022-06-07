cmake_minimum_required(VERSION 3.22)
project(calibration)

set(CMAKE_CXX_STANDARD 17)
find_package(Threads REQUIRED)
find_package(nlohmann_json 3.2.0 REQUIRED)

find_package(OpenCV 3.0 QUIET)
add_executable(cameraCalibration
        calibration.cpp)
target_link_libraries(cameraCalibration nlohmann_json::nlohmann_json ${OpenCV_LIBS})

add_executable(telloCalibration
        telloCalibration.cpp)
target_link_libraries(telloCalibration nlohmann_json::nlohmann_json ${OpenCV_LIBS} ctello)