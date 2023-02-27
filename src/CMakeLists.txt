project(
  test_cJSON
  VERSION 1.0.0
  DESCRIPTION "test_cJSON")

add_executable(test_cJSON test_cJSON.c)
target_link_libraries(test_cJSON cJSON)
add_test(NAME test_cJSON COMMAND $<TARGET_FILE:test_cJSON>)
