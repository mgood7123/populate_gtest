# include FetchContent
# this is a CMAKE MODULE and is internal to cmake
# cmake will find this module and include it if it exists
# if already included in a parent then nothing will happen
include(FetchContent)

# declare googletest
# if already declared in a parent then nothing will happen
FetchContent_Declare(
        googletest
        GIT_REPOSITORY https://github.com/google/googletest.git
        GIT_TAG        master
)

FetchContent_GetProperties(googletest)
if(NOT googletest_POPULATED)
    # populate googletest
    # if already populated in a parent then nothing will happen
    FetchContent_Populate(googletest)
    # Prevent overriding the parent project's compiler/linker
    # settings on Windows
    set(gtest_force_shared_crt ON CACHE BOOL "" FORCE)
    # Add googletest directly to our build. This defines
    # the gtest and gtest_main targets.
    add_subdirectory(${googletest_SOURCE_DIR} ${googletest_BINARY_DIR})
    # The gtest/gtest_main targets carry header search path
    # dependencies automatically when using CMake 2.8.11 or
    # later. Otherwise we have to add them here ourselves.
    if (CMAKE_VERSION VERSION_LESS 2.8.11)
        include_directories("${gtest_SOURCE_DIR}/include")
    endif()
endif()