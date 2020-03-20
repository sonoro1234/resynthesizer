project(libresynth)
cmake_minimum_required(VERSION 3.13)

#use cmake -DSYNTH_LIB_ALONE=yes for option
option(SYNTH_LIB_ALONE "Only build lib" ON)
if(${SYNTH_LIB_ALONE})
   add_compile_definitions(SYNTH_LIB_ALONE)
endif()

set(SRC  imageSynth.c engine.c glibProxy.c engineParams.c imageFormat.c progress.c)

add_library(libresynth MODULE ${SRC} )

#set CMAKE_INSTALL_PREFIX for that
install(FILES resynth.lua DESTINATION /lua)
install(TARGETS libresynth DESTINATION .)