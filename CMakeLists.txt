cmake_minimum_required(VERSION 3.16)

project (lib_async_xmodem VERSION 1.0.1 C ASM)
include(GNUInstallDirs)

add_library(lib_async_xmodem xmodem_server.c)

set_target_properties(lib_async_xmodem PROPERTIES 
    VERSION ${PROJECT_VERSION}
    PUBLIC_HEADER xmodem_server.h
)
configure_file(mylib.pc.in mylib.pc @ONLY)
target_include_directories(mylib PRIVATE .)

install(TARGETS mylib
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR})

install(FILES ${CMAKE_BINARY_DIR}/mylib.pc
    DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)