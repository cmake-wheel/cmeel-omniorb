cmake_minimum_required(VERSION 3.20)

set(NAME omniorb)
set(VERSION 4.3.1)
set(EXT tar.bz2)
set(SHA1 b6581c9b6a956c1d442c442767b5a58899a09513)

project(cmeel-${NAME} VERSION ${VERSION})

include(ExternalProject)
ExternalProject_Add(
  ${NAME}
  URL "http://downloads.sourceforge.net/${NAME}/omniORB-${VERSION}.${EXT}"
  URL_HASH "SHA1=${SHA1}"
  DOWNLOAD_EXTRACT_TIMESTAMP ON
  BUILD_IN_SOURCE ON
  CONFIGURE_COMMAND "./configure" "--prefix=${CMAKE_INSTALL_PREFIX}"
  BUILD_COMMAND "make"
  #TEST_COMMAND "make" "check"
  INSTALL_COMMAND "make" "install")

# dummy file for install target
install(FILES README.md DESTINATION share/cmeel-${NAME}/)
