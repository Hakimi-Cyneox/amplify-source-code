#
# Copyright (C) 2020 The Android Open Source Project
#
# Licensed under the Apache License, Version 2.0 (the "License"); you may not
# use this file except in compliance with the License. You may obtain a copy of
# the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
# License for the specific language governing permissions and limitations under
# the License.
#
project (liveness-native)

cmake_minimum_required(VERSION 3.4.1)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror")

add_library(
  liveness_opengl_renderer_jni SHARED
  liveness_jni_hooks.cpp
  liveness_opengl_renderer_jni.cpp)

find_library(log-lib log)
find_library(android-lib android)
find_library(opengl-lib GLESv2)
find_library(egl-lib EGL)


target_link_libraries(liveness_opengl_renderer_jni ${log-lib} ${android-lib} ${opengl-lib} ${egl-lib})