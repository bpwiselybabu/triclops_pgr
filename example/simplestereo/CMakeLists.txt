add_executable(simplestereo simplestereo.cpp)
add_executable(simplestereo-profile simplestereo-profile.cpp)

target_link_libraries(simplestereo pgrlibdcstereo ${DC1394_LIBRARIES} pnmio pnmutils triclops pthread dl m ) 

target_link_libraries(simplestereo-profile pgrlibdcstereo ${DC1394_LIBRARIES} pnmio pnmutils triclops pthread dl m )
