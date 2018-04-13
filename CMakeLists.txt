cmake_minimum_required(VERSION 2.8)
project(BUSE)

set(SOURCE_FILES buse.c buse.h)

add_library(buse SHARED ${SOURCE_FILES})
add_library(buse_Static STATIC ${SOURCE_FILES})
set_target_properties(buse_Static PROPERTIES OUTPUT_NAME buse)

add_executable(busexmp examples/busexmp.c)
target_link_libraries(busexmp buse)
add_executable(loopback examples/loopback.c)
target_link_libraries(loopback buse)

install(TARGETS buse buse_Static DESTINATION lib)
install(FILES buse.h DESTINATION include/)
