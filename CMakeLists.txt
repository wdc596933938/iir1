cmake_minimum_required(VERSION 3.5)
project(iir VERSION 1.0.0 LANGUAGES CXX)
include(GNUInstallDirs)
add_library(iir
  SHARED
  iir/Bessel.cpp
  iir/Biquad.cpp
  iir/Butterworth.cpp
  iir/Cascade.cpp
  iir/ChebyshevI.cpp
  iir/ChebyshevII.cpp
  iir/Custom.cpp
  iir/Elliptic.cpp
  iir/Legendre.cpp
  iir/PoleFilter.cpp
  iir/RBJ.cpp
  iir/RootFinder.cpp
  iir/State.cpp)
target_include_directories(iir PRIVATE iir)
list(APPEND MYHEADERS
  iir/Bessel.h
  iir/Biquad.h
  iir/Butterworth.h
  iir/Cascade.h
  iir/ChebyshevI.h
  iir/ChebyshevII.h
  iir/Common.h
  iir/Custom.h
  iir/Elliptic.h
  iir/Layout.h
  iir/Legendre.h
  iir/MathSupplement.h
  iir/PoleFilter.h
  iir/RBJ.h
  iir/RootFinder.h
  iir/State.h
  iir/Types.h
  iir/Utilities.h)
set_target_properties(iir PROPERTIES
  SOVERSION 1
  VERSION ${PROJECT_VERSION}
  PUBLIC_HEADER Iir.h
  PRIVATE_HEADER "${MYHEADERS}")
install(TARGETS iir
  LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
  ARCHIVE DESTINATION ${CMAKE_INSTALL_LIBDIR}
  PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
  PRIVATE_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/iir)
configure_file(iir.pc.in iir.pc @ONLY)