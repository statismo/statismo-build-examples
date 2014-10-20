CMAKE_MINIMUM_REQUIRED(VERSION 2.6)
PROJECT(statismo-itk-build-example)

FIND_PACKAGE(statismo REQUIRED)

FIND_PACKAGE(ITK REQUIRED)
include (${ITK_USE_FILE})
	
# If you compiled statismo with your own (external) itk version, it might happen that there are conflicts with HDF5
# In this case uncomment the following lines to link to use the HDF5 Headers that are shipped with ITK
#
# find_path(ITK_HDF5_INCLUDE_DIR hdf5.h PATHS ${ITK_INCLUDE_DIRS} PATH_SUFFIXES itkhdf5 itkhdf5/cpp )
# find_path(ITK_HDF5_INCLUDE_DIR_CPP H5Cpp.h PATHS ${ITK_INCLUDE_DIRS} PATH_SUFFIXES itkhdf5 itkhdf5/cpp )
# set(ITK_HDF5_INCLUDE_DIRS ${ITK_HDF5_INCLUDE_DIR} ${ITK_HDF5_INCLUDE_DIR_CPP})
# include_directories(${ITK_HDF5_INCLUDE_DIRS})

include_directories(${statismo_INCLUDE_DIRS}) 
link_directories( ${ITK_LIBRARY_DIRS} ${statismo_LIBRARY_DIRS})

add_executable (statismo-itk-build-example src/buildshapemodel.cpp)
target_link_libraries (statismo-itk-build-example ${ITK_LIBRARIES} ${statismo_LIBRARIES})

