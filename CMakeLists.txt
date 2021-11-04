cmake_minimum_required(VERSION 3.22.0)

# set the project name
project("CMake-Triet")

# add the executable
add_executable("${PROJECT_NAME}" "main.cpp")

install(TARGETS "${PROJECT_NAME}" DESTINATION bin)  #$(CMAKE_INSTALL_PREFIX)/bin
install(FILES "main.cpp" DESTINATION src)			#$(CMAKE_INSTALL_PREFIX)/src
ENABLE_TESTING()
include(CTest)
add_test("test1" "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}")
add_test("test2" "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}" "somethingdumb")
set(CTEST_PROJECT_NAME "CMake-Triet")
set(CTEST_NIGHTLY_START_TIME "01:00:00 UTC")

set(CTEST_DROP_METHOD "https")
set(CTEST_DROP_SITE "my.cdash.org")
set(CTEST_DROP_LOCATION "/submit.php?project=CMake-Triet")
set(CTEST_DROP_SITE_CDASH TRUE)