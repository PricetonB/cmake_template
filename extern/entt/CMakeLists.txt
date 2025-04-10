
# EnTT header-only library handling

# Define interface library
add_library(EnTT INTERFACE)
add_library(EnTT::EnTT ALIAS EnTT)  # Create namespaced alias

# Set include directories
target_include_directories(EnTT INTERFACE
    $<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/single_include>
    $<INSTALL_INTERFACE:include>
)

