#the precompiled library seems to miss pnimo for some reason
add_library(pnmutils STATIC IMPORTED)
set_property(TARGET pnmutils PROPERTY IMPORT_LOCATION  ${CMAKE_SOURCE_DIR}/pre_lib/libpnmutils.a)

add_library(triclops STATIC IMPORTED)
set_property(TARGET triclops PROPERTY IMPORT_LOCATION  ${CMAKE_SOURCE_DIR}/pre_lib/libtriclops.a)

add_library (pnmio STATIC pgrpnmio.cpp )

add_executable(pnmutilsTest pnmutilsTest.cpp)

target_link_libraries(pnmutilsTest pnmio pnmutils triclops pthread dl m)
