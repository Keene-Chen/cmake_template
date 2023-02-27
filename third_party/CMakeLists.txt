project(
  test_3rd
  VERSION 1.0.0
  DESCRIPTION "test_3rd")

add_library(cJSON SHARED "")
target_sources(
  cJSON
  PRIVATE ${CMAKE_CURRENT_LIST_DIR}/cJSON/cJSON.c
  PUBLIC ${CMAKE_CURRENT_LIST_DIR}/cJSON/cJSON.h)
target_include_directories(cJSON PUBLIC ${CMAKE_CURRENT_LIST_DIR}/cJSON)
message(STATUS "${BoldMagenta}>>> cJSON.so >>>${ColourReset}")

add_library(cJSON_Utils SHARED "")
target_sources(
  cJSON_Utils
  PRIVATE ${CMAKE_CURRENT_LIST_DIR}/cJSON/cJSON_Utils.c
  PUBLIC ${CMAKE_CURRENT_LIST_DIR}/cJSON/cJSON_Utils.h)
target_include_directories(cJSON_Utils PUBLIC ${CMAKE_CURRENT_LIST_DIR}/cJSON)
message(STATUS "${BoldMagenta}>>> cJSON_Utils.so >>>${ColourReset}")

add_library(inih SHARED "")
target_sources(
  inih
  PRIVATE ${CMAKE_CURRENT_LIST_DIR}/inih/ini.c
  PUBLIC ${CMAKE_CURRENT_LIST_DIR}/inih/ini.h)
target_include_directories(inih PUBLIC ${CMAKE_CURRENT_LIST_DIR}/inih)
message(STATUS "${BoldMagenta}>>> inih.so >>>${ColourReset}")

add_library(log SHARED "")
target_sources(
  log
  PRIVATE ${CMAKE_CURRENT_LIST_DIR}/log.c/src/log.c
  PUBLIC ${CMAKE_CURRENT_LIST_DIR}/log.c/src/log.h)
target_include_directories(log PUBLIC ${CMAKE_CURRENT_LIST_DIR}/log.c/src)
target_compile_definitions(log PRIVATE -DLOG_USE_COLOR)
message(STATUS "${BoldMagenta}>>> log.so >>>${ColourReset}")
