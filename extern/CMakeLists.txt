#extern
#this file will use add_subdirectory to add individual libraries as needed and 
#use add_library to define the rest of the libraries that are not handled with add_subdirectory
#in this example entt header only library will be implemented with add_subdirectoroy. 
#sdl2 will be implemented here.

# extern/CMakeLists.txt
# External dependencies management



#---------------------------------------------------------------
# SDL2 handling
find_package(SDL2 QUIET)
if(NOT SDL2_FOUND)
    include(FetchContent)
    FetchContent_Declare(
        SDL2
        GIT_REPOSITORY https://github.com/libsdl-org/SDL.git
        GIT_TAG release-2.30.1  # Use a specific stable version
    )
    FetchContent_MakeAvailable(SDL2)
endif()

# Create SDL2 target if not found by find_package
if(TARGET SDL2::SDL2)
    # If SDL2 was found via find_package
    add_library(sdl2 ALIAS SDL2::SDL2)
else()
    add_library(sdl2 INTERFACE)
    target_link_libraries(sdl2 INTERFACE SDL2)
    target_include_directories(sdl2 INTERFACE ${SDL2_SOURCE_DIR}/include)
endif()
#----------------------------------------------------------------


# EnTT subdirectory
add_subdirectory(entt)

#----------------------------------------------------------------



# Interface library for external dependencies
add_library(app_external_depend INTERFACE)
target_link_libraries(app_external_depend INTERFACE
    sdl2
    EnTT::EnTT  # Using proper target name from EnTT
)
