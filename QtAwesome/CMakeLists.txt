# set headers
set(header_path "${QTAWESOME_SOURCE_DIR}/QtAwesome")
file(GLOB headers ${header_path}/*.h)

# set sources
file(GLOB src *.cpp)

# setup deps
find_package(Qt5 COMPONENTS Core REQUIRED)
find_package(Qt5 COMPONENTS Gui REQUIRED)
find_package(Qt5 COMPONENTS Widgets REQUIRED)

qt5_add_resources(src QtAwesome.qrc)

# define library target
add_library(QtAwesome STATIC ${headers} ${src})
target_link_libraries(QtAwesome PUBLIC Qt5::Core Qt5::Gui Qt5::Widgets)
target_include_directories(
    QtAwesome
    PUBLIC
        $<BUILD_INTERFACE:${header_path}>
        $<INSTALL_INTERFACE:${include_dest}>

    PRIVATE
        ${Qt5Core_PRIVATE_INCLUDE_DIRS}
)

# install
install(TARGETS QtAwesome EXPORT QtAwesome DESTINATION ${lib_dest})
install(FILES ${headers} DESTINATION ${include_dest})
