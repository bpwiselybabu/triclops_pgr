cmake_minimum_required(VERSION 2.8)
project(triclops)

set(CMAKE_BUILD_TYPE Debug)

#for install

set(TRICLOPS_MAJOR_VERSION 3)
set(TRICLOPS_MINOR_VERSION 3)
set(TRICLOPS_PATCH_VERSION 0)
set(TRICLOPS_VERSION
  ${TRICLOPS_MAJOR_VERSION}.${TRICLOPS_MINOR_VERSION}.${TRICLOPS_PATCH_VERSION})

set(DEF_INSTALL_CMAKE_DIR lib/CMake/triclops)
set(INSTALL_CMAKE_DIR ${DEF_INSTALL_CMAKE_DIR} CACHE PATH
  "Installation directory for CMake files")
 
# Make relative paths absolute (needed later on)
foreach(p LIB BIN INCLUDE CMAKE)
  set(var INSTALL_${p}_DIR)
  if(NOT IS_ABSOLUTE "${${var}}")
    set(${var} "${CMAKE_INSTALL_PREFIX}/${${var}}")
  endif()
endforeach()



#dependencies
list(APPEND CMAKE_MODULE_PATH ${CMAKE_CURRENT_SOURCE_DIR}/cmake)
find_package(DC1394 REQUIRED)

#set the default path for built executables to the "bin" directory
set(EXECUTABLE_OUTPUT_PATH ${CMAKE_BINARY_DIR}/bin)
#set the default path for built libraries to the "lib" directory
set(LIBRARY_OUTPUT_PATH ${CMAKE_SOURCE_DIR}/lib)

#set the default path for includes

include_directories(${PROJECT_SOURCE_DIR}/include APPEND	
		    ${DC1394_INCLUDE_DIRS})

ADD_SUBDIRECTORY(pre_lib)
LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/pre_lib)
ADD_SUBDIRECTORY(src)
ADD_SUBDIRECTORY(example)

#setting up the install

#INSTALL(DIRECTORY include DESTINATION ${CMAKE_INSTALL_PREFIX}/triclops/include FILES_MATCHING PATTERN "*.h" )

# Add all targets to the build-tree export set
#export(TARGETS triclops 
#  FILE "${PROJECT_BINARY_DIR}/triclopsTargets.cmake")
 
#export(PACKAGE triclops)
 
#file(RELATIVE_PATH REL_INCLUDE_DIR "${INSTALL_CMAKE_DIR}"
#   "${INSTALL_INCLUDE_DIR}")

#set(CONF_INCLUDE_DIRS "${PROJECT_SOURCE_DIR}/include" "${PROJECT_BINARY_DIR}")
#configure_file(cmake/triclopsConfig.cmake.in
#  "${PROJECT_BINARY_DIR}/triclopsConfig.cmake" @ONLY)

#set(CONF_INCLUDE_DIRS "\${TRICLOPS_CMAKE_DIR}/${REL_INCLUDE_DIR}")
#configure_file(cmake/triclopsConfig.cmake.in
#  "${PROJECT_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/triclopsConfig.cmake" @ONLY)

#configure_file(cmake/triclopsConfigVersion.cmake.in
#  "${PROJECT_BINARY_DIR}/triclopsConfigVersion.cmake" @ONLY)

#install(FILES
#  "${PROJECT_BINARY_DIR}${CMAKE_FILES_DIRECTORY}/triclopsConfig.cmake"
#   "${PROJECT_BINARY_DIR}/triclopsConfigVersion.cmake"
#   DESTINATION "${INSTALL_CMAKE_DIR}" COMPONENT dev)
 
#install(EXPORT triclopsTargets DESTINATION
#  "${INSTALL_CMAKE_DIR}" COMPONENT dev)
