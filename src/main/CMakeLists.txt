include(FetchContent)

file(GLOB_RECURSE ${PROJECT_NAME}_SRC ${CMAKE_CURRENT_SOURCE_DIR}/*.cpp)

add_library(${PROJECT_NAME} STATIC ${${PROJECT_NAME}_SRC})

add_library(${PROJECT_NAME}::${PROJECT_NAME} ALIAS ${PROJECT_NAME})

target_include_directories(${PROJECT_NAME} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

if(TARGET rapidjson)
  message(STATUS "Activated position-independet compilation for target 'rapidjson'!")
  set_property(TARGET rapidjson PROPERTY POSITION_INDEPENDENT_CODE ON)
else()
  message(WARNING "Target 'rapidjson' not found!")
endif()
