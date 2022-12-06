set(target sft)

link_directories(${SOURCE_DIR}/include/lib)
include_directories(${SOURCE_DIR}/include/header)
include_directories(${SOURCE_DIR}/src/include)


#add_library(program_options ${SOURCE_DIR}/include/program_options.h program_options.cpp)

add_executable(${target} main.cpp)

IF(APPLE)
    target_link_libraries(${target} ${SYSTEMCONFIGURATION_LIBRARY} ${COREFOUNDATION_LIBRARY})
ENDIF()

target_link_libraries(${target}
        -lpthread
        Pcap++
        Packet++
        Common++
        -lpcap
        )

