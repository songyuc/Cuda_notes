cmake_minimum_required(VERSION 3.23)

set(CMAKE_CUDA_COMPILER "/home/songyuc/software/python/anaconda/anaconda3/bin/nvcc")
# NECESSARY: need to specify the CUDA_COMPILER explicitly.

if (NOT DEFINED CMAKE_CUDA_ARCHITECTURES)
    set(CMAKE_CUDA_ARCHITECTURES "75;80;86") # native is supported in version 3.24
endif ()
# Note: This variable is used to initialize the CUDA_ARCHITECTURES property on all targets.

project(Cuda_notes LANGUAGES CUDA CXX C)
include_directories(SYSTEM "${CMAKE_CUDA_TOOLKIT_INCLUDE_DIRECTORIES}")
# Note: This should be declared after the CUDA language has been enabled.

set(CMAKE_CXX_STANDARD 23)

set(CMAKE_CUDA_STANDARD 17) # nvcc11.8 doesn't support CUDA_STANDARD higher than 17
set(CMAKE_CUDA_STANDARD_REQUIRED ON)

include_directories("${CMAKE_SOURCE_DIR}/cuda-samples/Common")
include_directories(.)

add_executable(Cuda_notes deviceQuery.cu)
target_link_libraries(Cuda_notes cudart)


