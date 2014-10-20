CMAKE_MINIMUM_REQUIRED(VERSION 2.6) 
PROJECT(statismo-vtk-build-example)

FIND_PACKAGE(statismo REQUIRED)

FIND_PACKAGE(VTK REQUIRED)
include (${VTK_USE_FILE})
	

include_directories(${statismo_INCLUDE_DIRS}) 
link_directories( ${VTK_LIBRARY_DIRS} ${statismo_LIBRARY_DIRS})

add_executable (statismo-vtk-build-example src/buildshapemodel.cpp)
target_link_libraries (statismo-vtk-build-example ${VTK_LIBRARIES} ${statismo_LIBRARIES})

