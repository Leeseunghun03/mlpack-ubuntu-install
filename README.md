# mlpack-ubuntu-install

Env: Ubuntu 20.04

## Install

```
wget http://www.mlpack.org/files/mlpack-3.2.2.tar.gz
cd ~
cd mlpack-3.2.2
mkdir build
cd build
cmake ../
make -j4
sudo make install
```

## Edit mlpack-config.cmake
   

```
sudo gedit /usr/local/lib/cmake/mlpack/mlpack-config.cmake
```

```
####### Expanded from @PACKAGE_INIT@ by configure_package_config_file() #######
####### Any changes to this file will be overwritten by the next CMake run ####
####### The input file was mlpack-config.cmake.in                            ########

get_filename_component(PACKAGE_PREFIX_DIR "${CMAKE_CURRENT_LIST_DIR}/../../../" ABSOLUTE)

macro(set_and_check _var _file)
  set(${_var} "${_file}")
  if(NOT EXISTS "${_file}")
    message(FATAL_ERROR "File or directory ${_file} referenced by variable ${_var} does not exist !")
  endif()
endmacro()

macro(check_required_components _NAME)
  foreach(comp ${${_NAME}_FIND_COMPONENTS})
    if(NOT ${_NAME}_${comp}_FOUND)
      if(${_NAME}_FIND_REQUIRED_${comp})
        set(${_NAME}_FOUND FALSE)
      endif()
    endif()
  endforeach()
endmacro()

####################################################################################

include(${CMAKE_CURRENT_LIST_DIR}/mlpack-targets.cmake)

set_and_check(MLPACK_INCLUDE_DIRS "${PACKAGE_PREFIX_DIR}/include")

set(MLPACK_LIBRARIES mlpack::mlpack)

```
