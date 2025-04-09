

A C++ template using CMake to automate dependency management, automatically searches for libraries and fetches missing libraries from GitHub. It includes entt-confetti by Hexerei as an example.


Structure
    CMakeLists.txt: Includes src/ (source) and extern/ (dependencies).
    src/: Source files and dependency linking.
    extern/: Dependency setup (e.g., entt-confetti).

Prerequisites
    CMake 3.10+
    C++17 compiler (GCC, Clang, MSVC)
    Git
    Build tools: make (Linux) or Visual Studio (Windows)

Build Instructions
    git clone https://github.com/PricetonB/cmake_template.git && cd cmake_template 
    mkdir build && cd build
    cmake .. (Windows: cmake .. -G "Visual Studio 16 2019")
    cmake --build .
    Executable: build/src/showdown (Linux) or build/src/Debug/showdown.exe (Windows)


