add_library(pnmutils STATIC IMPORTED)
set_property(TARGET pnmutils PROPERTY IMPORT_LOCATION  ${CMAKE_SOURCE_DIR}/pre_lib/libpnmutils.a)

add_library(triclops STATIC IMPORTED)
set_property(TARGET triclops PROPERTY IMPORT_LOCATION  ${CMAKE_SOURCE_DIR}/pre_lib/libtriclops.a)


