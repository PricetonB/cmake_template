#extern
#this file will use add_subdirectory to add individual libraries as needed and 
#use add_library to define the rest of the libraries that are not handled with add_subdirectory
#in this example entt header only library will be implemented with add_subdirectoroy. 
#sdl2 will be implemented here.


#try to find sdl2 on computer
find_package()

#if its not found use fetch_content and put it in directory CMAKE_CURRENT_SOURCE_DIR

#finish implementing sdl2 with these if needed so it can be used in target link libraries at the bottom of this document
add_library()
target_link_libraries()
target_include_directories()


add_subdirectory(entt)

add_library(app_external_depend INTERFACE)

target_link_libraries(app_external_depend INTERFACE
	sdl2
	entt
)



