# src/CMakeLists.txt
#this file will create executable and link to interface of project libraries

# Create executable and link to interface target
add_executable(${PROJECT_NAME} 
    main.cpp
    Game.cpp    
    Scene.cpp   
)

# Link to the interface library from extern
target_link_libraries(${PROJECT_NAME} PRIVATE app_external_depend)

target_include_directories(${PROJECT_NAME} PRIVATE 
    ${CMAKE_CURRENT_SOURCE_DIR}/include
)

set_target_properties(${PROJECT_NAME} PROPERTIES
    CXX_STANDARD 17
    CXX_STANDARD_REQUIRED ON
    CXX_EXTENSIONS OFF
)
