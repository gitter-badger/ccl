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
    bitstrings.c
    bloom.c
    buffer.c
    deque.c
    dictionary.c
    dlist.c
    doubledlist.c
    doublelist.c
    error.c
    fgetline.c
    generic.c
    hashtable.c
    heap.c
    iMask.c
    intdlist.c
    intlist.c
    list.c
    longlongdlist.c
    longlonglist.c
    malloc_debug.c
    memorymanager.c
    observer.c
    pool.c
    pooldebug.c
    priorityqueue.c
    qsortex.c
    qsort_r.c
    queue.c
    redblacktree.c
    scapegoat.c
    searchtree.c
    sequential.c
    smallpool.c
    strcollection.c
    stringlist.c
    SuffixTree.c
    test.c
    valarraydouble.c
    valarrayfloat.c
    valarrayint.c
    valarraylongdouble.c
    valarraylonglong.c
    valarrayshort.c
    valarraysize_t.c
    valarrayuint.c
    valarrayulonglong.c
    vector.c
    vectorsize_t.c
    wdictionary.c
    wstrcollection.c
    wstringlist.c
    )

set(CCL_HEADERS
    ccl_internal.h
    containers.h
    dlistgen.h
    doubledlist.h
    doublelist.h
    intdlist.h
    intlist.h
    listgen.h
    longlongdlist.h
    longlonglist.h
    stringlistgen.h
    stringlist.h
    valarraygen.h
    valarray.h
    vectorgen.h
    wstringlist.h
    )

add_library(ccl SHARED ${CCL_SOURCES})
set_target_properties(ccl PROPERTIES SOVERSION ${VERSION_MAJOR} VERSION ${VERSION_STRING})

add_executable(dotest test.c)
target_link_libraries(dotest ccl m)

install(FILES ${CCL_HEADERS} DESTINATION "include/ccl")



