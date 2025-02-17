# ======================================================================== #
# Copyright 2020-2020 Ingo Wald                                            #
#                                                                          #
# Licensed under the Apache License, Version 2.0 (the "License");          #
# you may not use this file except in compliance with the License.         #
# You may obtain a copy of the License at                                  #
#                                                                          #
#     http://www.apache.org/licenses/LICENSE-2.0                           #
#                                                                          #
# Unless required by applicable law or agreed to in writing, software      #
# distributed under the License is distributed on an "AS IS" BASIS,        #
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. #
# See the License for the specific language governing permissions and      #
# limitations under the License.                                           #
# ======================================================================== #

set(OpenGL_GL_PREFERENCE "LEGACY")
find_package(OpenGL REQUIRED)

find_package(Qt5Widgets REQUIRED)
set(CMAKE_AUTOMOC ON)

add_library(qtOWL STATIC)
target_sources(qtOWL PRIVATE
  OWLViewer.cpp
  InspectMode.cpp
  FlyMode.cpp
  Camera.cpp
  CameraManip.cpp

  AlphaEditor.h
  AlphaEditor.cpp
  XFEditor.h
  XFEditor.cpp

  ColorMaps.h
  ColorMaps.cpp
)
target_link_libraries(qtOWL PUBLIC owl::owl Qt5::Widgets stb_image OpenGL::GL)
target_include_directories(qtOWL PUBLIC ${CMAKE_CURRENT_LIST_DIR}/..)
