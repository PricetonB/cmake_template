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
        SOURCE_SUBDIR SDL2  # Optional: explicitly point to the root where CMakeLists.txt is
    )
    # Fetch and add SDL2 as a subdirectory to use its own CMakeLists.txt
    FetchContent_GetProperties(SDL2)
    if(NOT sdl2_POPULATED)
        FetchContent_Populate(SDL2)
        add_subdirectory(${sdl2_SOURCE_DIR} ${sdl2_BINARY_DIR})
    endif()
endif()

# Create an alias for consistency, whether found or fetched
if(TARGET SDL2::SDL2)
    add_library(sdl2 ALIAS SDL2::SDL2)
else()
    message(FATAL_ERROR "SDL2 could not be found or built; SDL2::SDL2 target is missing")
endif()

#---------------------------------------------------------------
# EnTT subdirectory (keeping your original structure)
add_subdirectory(entt)

#---------------------------------------------------------------
# Interface library for external dependencies
add_library(app_external_depend INTERFACE)
target_link_libraries(app_external_depend INTERFACE
    sdl2        # Using the alias we defined
    EnTT::EnTT  # Using proper target name from EnTT
)
