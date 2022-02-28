cmake_minimum_required(VERSION 3.0.0)
project(vscode_cmake_windows VERSION 0.1.0)

#define CMAKE values
set( IMGUI_DIR ${CMAKE_CURRENT_SOURCE_DIR}/3rdparty/imgui )

set( SOURCE # project source files
    ${IMGUI_DIR}/imgui.cpp
    ${IMGUI_DIR}/imgui_demo.cpp
    ${IMGUI_DIR}/imgui_draw.cpp
    ${IMGUI_DIR}/imgui_tables.cpp
    ${IMGUI_DIR}/imgui_widgets.cpp
    ${IMGUI_DIR}/backends/imgui_impl_glfw.cpp
    ${IMGUI_DIR}/backends/imgui_impl_opengl3.cpp   
)

#added include directories
include_directories( 
    ${IMGUI_DIR}
    ${IMGUI_DIR}/backends
    ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/include/
)

#set project library path
if(WIN32) # if Windows
    if(CMAKE_CL_64) # if 64bit windows
        set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/lib-vc2010-64)
    else() # if 32bit windows
        set(LIB_DIR ${CMAKE_CURRENT_SOURCE_DIR}/libs/glfw/lib-vc2010-32)
    endif()
elseif(UNIX) # else if Linux
    add_compile_options(-g -Wall -Wextra)
endif()

add_executable(${PROJECT_NAME}
    ${CMAKE_CURRENT_SOURCE_DIR}/src/main.cpp
    ${SOURCE}
)

if(WIN32) # if Windows
    target_link_libraries(${PROJECT_NAME}
        PUBLIC
        ${LIB_DIR}/glfw3.lib
        opengl32.lib
        gdi32.lib
    )
elseif(UNIX) # else if Linux
target_link_libraries(${PROJECT_NAME}
    PUBLIC
    GL
    glfw
)
endif()