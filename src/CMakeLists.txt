#this file will create executable and link interface of project libraries

add_executable(${PROJECT_NAME} main.cpp)


target_link_libraries(${PROJECT_NAME} PRIVATE app_external_depend)


