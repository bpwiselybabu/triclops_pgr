add_executable(simplegrab simplegrab.cpp)
target_link_libraries(simplegrab pgrlibdcstereo ${DC1394_LIBRARIES} pnmio pnmutils triclops pthread dl m pnmio )

