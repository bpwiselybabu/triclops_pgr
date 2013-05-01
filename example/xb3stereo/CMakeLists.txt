add_executable(xb3stereo xb3stereo.cpp)

target_link_libraries(xb3stereo pgrlibdcstereo ${DC1394_LIBRARIES} pnmio pnmutils triclops pthread dl m)


