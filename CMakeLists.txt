# main cmakelists.txt that sets up project and 
# uses add_subdirectory to run cmakelists.txt in src and extern(libraries)

cmake_minimum_required(VERSION 3.10)
project(Showdown)

add_subdirectory(src)
add_subdirectory(extern)
