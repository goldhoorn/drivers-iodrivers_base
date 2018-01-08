find_package(Boost COMPONENTS thread system REQUIRED)
include_directories(${Boost_INCLUDE_DIRS})

find_package(Threads REQUIRED)

add_library(${CMAKE_PROJECT_NAME} SHARED
    Driver.cpp Bus.cpp Timeout.cpp IOStream.cpp Exceptions.cpp TCPDriver.cpp
    IOListener.cpp TestStream.cpp
)

target_link_libraries(${CMAKE_PROJECT_NAME}
  ${Boost_THREAD_LIBRARY} ${Boost_SYSTEM_LIBRARY} ${CMAKE_THREAD_LIBS_INIT}
)
    
install (TARGETS ${CMAKE_PROJECT_NAME} 
         ARCHIVE DESTINATION lib
         LIBRARY DESTINATION lib
         RUNTIME DESTINATION bin)

configure_file(	${CMAKE_CURRENT_SOURCE_DIR}/${CMAKE_PROJECT_NAME}.pc.in
		${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_PROJECT_NAME}.pc @ONLY)


install(FILES ${CMAKE_CURRENT_BINARY_DIR}/${CMAKE_PROJECT_NAME}.pc
                DESTINATION lib/pkgconfig)

