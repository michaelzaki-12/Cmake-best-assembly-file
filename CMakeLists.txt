cmake_minimum_required(VERSION 3.14)
project(assembly ASM_NASM)

set(CMAKE_ASM_NASM_LINK_EXECUTABLE "ld <CMAKE_ASM_NASM_LINK_FLAGS> <LINK_FLAGS> <OBJECTS>  -o <TARGET> <LINK_LIBRARIES>")

set(CMAKE_ASM_NASM_OBJECT_FORMAT elf64)

enable_language(ASM_NASM)

enable_language(CXX)
set(CMAKE_CXX_STANDARD 17)
set(CMAKE_ASM_NASM_COMPILE_OBJECT "<CMAKE_ASM_NASM_COMPILER> <INCLUDES> <FLAGS> -o <OBJECT> <SOURCE>")


add_compile_options(
    "$<$<COMPILE_LANGUAGE:ASM_NASM>:-f $<IF:$<BOOL:$<TARGET_PROPERTY:NASM_OBJ_FORMAT>>, \
    $<TARGET_PROPERTY:NASM_OBJ_FORMAT>, ${CMAKE_ASM_NASM_OBJECT_FORMAT}>>"
)
#add_executable(yourcode)


#set_target_properties(assembly PROPERTIES NASM_OBJ_FORMAT elf64)   uncomment it when using the file


set(CMAKE_ASM_NASM_FLAGS_DEBUG "-g -Fdwarf")
