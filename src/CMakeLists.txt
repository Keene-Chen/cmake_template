#[[
# Author : KeeneChen
# Date   : 2023.09.04-11:50:36
]]

project(test_cJSON DESCRIPTION "test_cJSON")

add_executable(test_cJSON test_cJSON.c)
target_link_libraries(test_cJSON cJSON)
add_test(NAME test_cJSON COMMAND $<TARGET_FILE:test_cJSON>)
