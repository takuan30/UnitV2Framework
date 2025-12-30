cmake_minimum_required(VERSION 3.5)
project(example C CXX)

# ===== クロスコンパイル =====
set(CMAKE_C_COMPILER arm-linux-gnueabihf-gcc)
set(CMAKE_CXX_COMPILER arm-linux-gnueabihf-g++)

# ===== Build type =====
if(NOT CMAKE_BUILD_TYPE)
    set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_CXX_FLAGS_DEBUG   "-O0 -Wall -g")
set(CMAKE_CXX_FLAGS_RELEASE "-O3 -Wall")

# ===== 出力 =====
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_SOURCE_DIR}/bin)

# ===== OpenCV =====
set(OpenCV_DIR "/workspaces/opencv/build-armhf/install/lib/cmake/opencv4")
find_package(OpenCV REQUIRED)

# ===== ncnn =====
set(NCNN_ROOT "/workspaces/ncnn/build-armhf/install")
set(NCNN_INCLUDE_DIR ${NCNN_ROOT}/include/ncnn)
set(NCNN_LIB ${NCNN_ROOT}/lib/libncnn.a)

include_directories(${NCNN_INCLUDE_DIR})

# ===== include paths =====
include_directories(
    ${OpenCV_INCLUDE_DIRS}
    ${NCNN_INCLUDE_DIR}
    ${PROJECT_SOURCE_DIR}/include
)

# ===== Framework sources =====
file(GLOB_RECURSE FRAMEWORK_SRC
    "${PROJECT_SOURCE_DIR}/src/*.cpp"
)

add_library(mainlib ${FRAMEWORK_SRC})

target_link_libraries(mainlib
    ${NCNN_LIB}
    -fopenmp
)

# ===== main =====
add_executable(example
    ${PROJECT_SOURCE_DIR}/test/main.cpp
)

target_link_libraries(example
    mainlib
    ${OpenCV_LIBS}
)