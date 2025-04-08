#used to build header only entt library
#this is cmakelists for entt that 

# extern/entt/CMakeLists.txt
# EnTT header-only library

# Define interface library
add_library(EnTT INTERFACE)
add_library(EnTT::EnTT ALIAS EnTT)  # Create namespaced alias

# Set include directories
target_include_directories(EnTT INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/single_include>
    $<INSTALL_INTERFACE:include>
)

