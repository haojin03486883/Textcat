cmake_minimum_required(VERSION 3.1)

project(Textcat)

set(CMAKE_CXX_STANDARD 14)

if(CMAKE_CXX_COMPILER_ID MATCHES "GNU" OR CMAKE_CXX_COMPILER_ID MATCHES "Clang")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Wextra -O2")
    set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -Wl,-s")
    if(WIN32)
        set(CMAKE_EXE_LINKER_FLAGS "${CMAKE_EXE_LINKER_FLAGS} -static")
    endif()
elseif(CMAKE_CXX_COMPILER_ID MATCHES "MSVC")
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} /D_SCL_SECURE_NO_WARNINGS /EHsc /W3 /O2 /MT")
endif()

include_directories("include")

set(EXAMPLE
    XML_SAXReader
    XML_SAXWriter
    XML_DOMReader
    XML_DOMWriter)

foreach(example ${EXAMPLE})
    add_executable(${example} example/${example}/${example}.cpp)
endforeach()
