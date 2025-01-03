# Copyright 2025 Dalton Prokosch

# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at

#     http://www.apache.org/licenses/LICENSE-2.0

# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

cmake_minimum_required(VERSION 3.14)
project(SVector VERSION 0.1.0)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

set(GOOGLE_TEST_VERSION 1.15.2)
set(LIBRARIES
    sVector
    gtest_main
)

# Installs google test
include(FetchContent)
FetchContent_Declare(
    googletest
    URL https://github.com/google/googletest/archive/refs/tags/v${GOOGLE_TEST_VERSION}.zip 
    FIND_PACKAGE_ARGS ${GOOGLE_TEST_VERSION}
)
FetchContent_MakeAvailable(googletest)

add_subdirectory(sVector)

add_executable(sVectorTests tests/sVectorTests.cpp)
target_link_libraries(sVectorTests PUBLIC ${LIBRARIES})

target_compile_options(sVectorTests PUBLIC -std=c++20 -Wall -Wextra -O3)