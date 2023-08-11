

if (CMAKE_VERSION VERSION_GREATER 3.12)
 
project(camvid_sender)			
set(CMAKE_CXX_STANDARD 11)

# set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_BUILD_TYPE RelWithDebInfo)
set(CMAKE_CXX_FLAGS_DEBUG  "-g")


message(STATUS "$CMAKE_CXX_FLAGS = ${CMAKE_CXX_FLAGS}")

message(STATUS "CMAKE SOURCE DIR = ${CMAKE_SOURCE_DIR}")


set(SOURCE_EXE )
set(SOURCE_LIB_GLFW ${CMAKE_SOURCE_DIR}/camvid_sender/lib/glfw3/glfw3.lib)

include_directories(${CMAKE_SOURCE_DIR}/camvid_sender/include)

add_executable(main ${SOURCE_EXE}  "main.cpp" "video_reader.cpp") 

list(APPEND SOURCE_AV
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/avcodec.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/avdevice.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/avfilter.lib 
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/avformat.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/avutil.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/postproc.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/swresample.lib
    ${CMAKE_SOURCE_DIR}/camvid_sender/lib/swscale.lib
)


target_link_libraries(main ${SOURCE_LIB_GLFW} opengl32.dll ${SOURCE_AV})


endif()