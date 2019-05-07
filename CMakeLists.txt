cmake_minimum_required(VERSION 2.8.9)
project(cpuloadProfiling)

set(CMAKE_CXX_FLAGS  "${CMAKE_CXX_FLAGS} -std=c++0x -Wall -Wextra -fPIC -O2 -DPLAT_LINUX")
set(CMAKE_BUILD_TYPE Debug)


include_directories(${PCL_INCLUDE_DIRS} "/usr/include/eigen3" "include")
link_directories(${PCL_LIBRARY_DIRS})
add_definitions(${PCL_DEFINITIONS})

#find_package(Qt5Core REQUIRED)
#find_package(Qt5Gui)
#find_package(Qt5Widgets)


#https://stackoverflow.com/questions/28815024/how-to-port-a-qmake-project-to-cmake?noredirect=1&lq=1
set ( CMAKE_BUILD_TYPE Release )


#set(QT5_LIBRARIES Qt5::Widgets)

include_directories(incl)
include_directories(bltincl)


#For the shared library:
set ( PROJECT_LINK_LIBS /home/hut/mlxtofTest/mlxPCL_BltPCData/lib/libbta.so )
link_directories( /lib )


#add_executable(EVK_BLT_PCL_Viewer src/mlxPCL_Viewer.cpp src/PCLViewer.cpp)
add_executable(EVK_BLT_PCL_Viewer src/mlxPCL_Viewer.cpp )
#target_include_directories(EVK_BLT_PCL_Viewer PUBLIC ${PCL_INCLUDE_DIRS} ${EIGEN_INCLUDE_DIRS})
target_link_libraries(EVK_BLT_PCL_Viewer ${PROJECT_LINK_LIBS} ${PCL_COMMON_LIBRARIES} ${PCL_IO_LIBRARIES} ${PCL_VISUALIZATION_LIBRARIES} ${QT5_LIBRARIES})



#file(GLOB SOURCES "src/*.cpp")

#set(UI_SOURCES
#    incl/MainWindow.ui
#)

#https://gist.github.com/Univan-Ahn/19d8bd04ad08889e1208
#qt5_wrap_ui(UI_GENERATED_HEADERS incl ${UI_SOURCES})








#set_target_properties(mlxETHGUI PROPERTIES 
#                      VERSION ${VOXEL_VERSION} 
#                      SOVERSION ${VOXEL_ABI_VERSION})

