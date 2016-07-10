cmake_minimum_required(VERSION 2.6)
list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake_modules")

project(ccl)

set(CMAKE_ECLIPSE_VERSION 4.5.2)
#include(UseCppUTest)
#add_definitions(-std=c99)


set(CMAKE_C_FLAGS "-Wall -Wpedantic -Wno-pointer-sign -Werror")
add_definitions(-DUNIX)
enable_language(C)

#enable_unit_testing()

# The version number
set (project_name_VERSION_MAJOR 0)
set (project_name_VERSION_MINOR 1)

# output directories
set (CMAKE_RUNTIME_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/bin)
set (CMAKE_LIBRARY_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)
set (CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${PROJECT_BINARY_DIR}/lib)

#include_directories(include)
#add_executable(program_name src/main.c)

include_directories(.)

set(CCL_SOURCES
    buffer.c
    vector.c
    bitstrings.c
    bloom.c
    error.c
    deque.c
    dictionary.c
    doublelist.c
    dlist.c
    fgetline.c
    generic.c
    hashtable.c
    heap.c
    iMask.c
    intlist.c
    list.c
    longlonglist.c
    malloc_debug.c
    pool.c
    pooldebug.c
    qsortex.c
    queue.c
    redblacktree.c
    scapegoat.c
    searchtree.c
    strcollection.c
    valarraydouble.c
    valarrayint.c
    valarrayuint.c
    valarraysize_t.c
    valarrayfloat.c
    valarraylongdouble.c
    valarrayuint.c
    valarraylonglong.c
    valarrayulonglong.c
    valarrayshort.c
    vectorsize_t.c
    observer.c
    memorymanager.c
    sequential.c
    wstrcollection.c
    )


set(CCL_HEADERS
    ccl_internal.h
    containers.h
    doubledlist.h
    doublelist.h
    intdlist.h
    intlist.h
    longlongdlist.h
    longlonglist.h
    stringlist.h
    valarray.h
    wstringlist.h
    )

add_library(ccl SHARED ${CCL_SOURCES})
set_target_properties(ccl PROPERTIES SOVERSION ${VERSION_MAJOR} VERSION ${VERSION_STRING})

install(FILES ${CCL_HEADERS} DESTINATION "include/ccl")

