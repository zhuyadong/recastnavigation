cmake_minimum_required(VERSION 3.0)

project(RecastNavigation)

# lib versions
SET(SOVERSION 1)
SET(VERSION 1.0.0)
SET(CMAKE_CXX_STANDARD 11)

option(RECASTNAVIGATION_VM "Build for running in virtual machine(vmware etc)" ON)
option(RECASTNAVIGATION_DEMO "Build demo" ON)
option(RECASTNAVIGATION_TESTS "Build tests" ON)
option(RECASTNAVIGATION_EXAMPLES "Build examples" ON)
option(RECASTNAVIGATION_STATIC "Build static libraries" ON)

if (RECASTNAVIGATION_VM)
	add_definitions(-DVM_BUILD)
endif()

add_subdirectory(DebugUtils)
add_subdirectory(Detour)
add_subdirectory(DetourCrowd)
add_subdirectory(DetourTileCache)
add_subdirectory(Recast)

if (RECASTNAVIGATION_DEMO)
    add_subdirectory(RecastDemo)
endif ()

if (RECASTNAVIGATION_TESTS)
    enable_testing()
    add_subdirectory(Tests)
endif ()
