# extern/CMakeLists.txt
# External dependencies management

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
        SOURCE_SUBDIR SDL  # Corrected: SDL2’s root folder is "SDL", not "SDL2"
    )
    FetchContent_GetProperties(SDL2)
    if(NOT sdl2_POPULATED)
        FetchContent_Populate(SDL2)
        add_subdirectory(${sdl2_SOURCE_DIR} ${sdl2_BINARY_DIR})
    endif()
endif()

# Check if SDL2::SDL2 exists and use it directly; no need to redefine an alias
if(TARGET SDL2::SDL2)
    # Use SDL2::SDL2 as-is without creating a redundant alias
    set(SDL2_TARGET SDL2::SDL2)
else()
    message(FATAL_ERROR "SDL2 could not be found or built; SDL2::SDL2 target is missing")
endif()

#---------------------------------------------------------------
# EnTT subdirectory
add_subdirectory(entt)

#---------------------------------------------------------------
# Interface library for external dependencies
add_library(app_external_depend INTERFACE)
target_link_libraries(app_external_depend INTERFACE
    ${SDL2_TARGET}  # Use the resolved target name
    EnTT::EnTT      # Using proper target name from EnTT
)
