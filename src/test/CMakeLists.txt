set(BINARY Test${CMAKE_PROJECT_NAME})

find_package( Threads )

add_executable(${BINARY}
    TestMain.cpp
    TestDASHTree.cpp
    TestHLSTree.cpp
    TestHelper.cpp
    ../parser/DASHTree.cpp
    ../parser/HLSTree.cpp
    ../parser/PRProtectionParser.cpp
    ../common/AdaptiveTree.cpp
    ../helpers.cpp
    ../oscompat.cpp
    )

target_link_libraries(${BINARY} PRIVATE ${EXPAT_LIBRARIES} ${GTEST_LIBRARIES} Threads::Threads ${CMAKE_DL_LIBS})

set(TEST_DATA_DIR "${CMAKE_SOURCE_DIR}/src/test/manifests")
add_test(NAME manifest_tests COMMAND ${BINARY} "${TEST_DATA_DIR}")
