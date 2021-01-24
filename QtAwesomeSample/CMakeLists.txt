if(${QTAWESOME_BUILD_SAMPLE})
    add_executable(QtAwesomeSample main.cpp)
    target_link_libraries(QtAwesomeSample PUBLIC QtAwesome)
endif()