project(linenoise)
cmake_minimum_required(VERSION 3.22)

add_library(linenoise STATIC src/linenoise.c)
target_include_directories(linenoise PUBLIC include)
target_compile_options(linenoise PRIVATE -O3 -flto)
set_target_properties(linenoise PROPERTIES LINKER_LANGUAGE CXX)

if(LINENOISE_EXAMPLE)
    add_executable(linenoise_example example/example.c)
    target_link_libraries(linenoise_example PRIVATE linenoise)
    target_compile_options(linenoise_example PRIVATE -O3 -flto)
    set_target_properties(linenoise_example PROPERTIES LINKER_LANGUAGE CXX)
endif()
