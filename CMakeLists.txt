cmake_minimum_required(VERSION 3.16)

project(imgui LANGUAGES CXX)

add_library(${PROJECT_NAME} STATIC)

#FILES
target_sources(${PROJECT_NAME} PRIVATE 
                                    imconfig.h
                                    imgui.h
                                    imgui.cpp
                                    imgui_draw.cpp
                                    imgui_internal.h
                                    imgui_widgets.cpp
                                    imstb_rectpack.h
                                    imstb_textedit.h
                                    imstb_truetype.h
                                    imgui_demo.cpp)

#INCLUDE DIRS
target_include_directories(${PROJECT_NAME} PUBLIC "${PROJECT_SOURCE_DIR}")

#LINKING

#DEFINITIONS
#target_compile_definitions(${PROJECT_NAME} PRIVATE|PUBLIC|INTERFACE )

set_target_properties(${PROJECT_NAME}
  PROPERTIES
  CXX_STANDARD              17
)

if (WIN32)
    set_target_properties(${PROJECT_NAME} PROPERTIES MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
elseif(UNIX)
endif()

set_property(TARGET ${PROJECT_NAME} PROPERTY POSITION_INDEPENDENT_CODE ON)