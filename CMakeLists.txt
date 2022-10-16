cmake_minimum_required(VERSION 3.23)

project(rapidjson VERSION 1.0.0
            LANGUAGES CXX)

#include(FetchContent)
#FetchContent_Declare(
#  catch
#  GIT_REPOSITORY https://github.com/catchorg/Catch2.git
#  GIT_TAG        v2.13.6
#)
#FetchContent_MakeAvailable(catch)


# The compiled library code is here
#add_subdirectory(src/main)
# STATIC, SHARED, MODULE, INTERFACE
add_library(rapidjson STATIC
        ./src/main/rapidjson/pointer.h
        ./src/main/rapidjson/allocators.h
        ./src/main/rapidjson/stream.h
        ./src/main/rapidjson/filereadstream.h
        ./src/main/rapidjson/writer.h
        ./src/main/rapidjson/internal/stack.h
        ./src/main/rapidjson/internal/itoa.h
        ./src/main/rapidjson/internal/diyfp.h
        ./src/main/rapidjson/internal/meta.h
        ./src/main/rapidjson/internal/regex.h
        ./src/main/rapidjson/internal/biginteger.h
        ./src/main/rapidjson/internal/strtod.h
        ./src/main/rapidjson/internal/pow10.h
        ./src/main/rapidjson/internal/dtoa.h
        ./src/main/rapidjson/internal/swap.h
        ./src/main/rapidjson/internal/strfunc.h
        ./src/main/rapidjson/internal/ieee754.h
        ./src/main/rapidjson/schema.h
        ./src/main/rapidjson/istreamwrapper.h
        ./src/main/rapidjson/rapidjson.h
        ./src/main/rapidjson/reader.h
        ./src/main/rapidjson/error/error.h
        ./src/main/rapidjson/error/en.h
        ./src/main/rapidjson/fwd.h
        ./src/main/rapidjson/memorystream.h
        ./src/main/rapidjson/encodings.h
        ./src/main/rapidjson/stringbuffer.h
        ./src/main/rapidjson/encodedstream.h
        ./src/main/rapidjson/ostreamwrapper.h
        ./src/main/rapidjson/filewritestream.h
        ./src/main/rapidjson/document.h
        ./src/main/rapidjson/prettywriter.h
        ./src/main/rapidjson/dummy.cpp
        ./src/main/rapidjson/memorybuffer.h
        ./src/main/rapidjson/msinttypes/inttypes.h
        ./src/main/rapidjson/msinttypes/stdint.h
)

target_include_directories(rapidjson PUBLIC ./src/main)
target_compile_features(rapidjson PUBLIC cxx_std_11)
set_property(TARGET rapidjson PROPERTY POSITION_INDEPENDENT_CODE ON)

install(TARGETS rapidjson
        EXPORT rapidjson-export
        LIBRARY DESTINATION lib
        ARCHIVE DESTINATION lib
)

install(EXPORT      rapidjson-export
        FILE        rapidjsonTargets.cmake
        NAMESPACE   rapidjson::
        DESTINATION lib/cmake
)

install(FILES ${CMAKE_CURRENT_SOURCE_DIR}/rapidjsonConfig.cmake
        DESTINATION "lib/cmake"
)

