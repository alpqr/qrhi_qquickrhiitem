cmake_minimum_required(VERSION 3.16)
project(testapp LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)

find_package(Qt6 REQUIRED COMPONENTS Core Gui Qml Quick ShaderTools)

qt_add_executable(testapp
    rhitextureitem.cpp rhitextureitem.h
    main.cpp
)

target_link_libraries(testapp PRIVATE
    Qt6::Core
    Qt6::Gui
    Qt6::GuiPrivate
    Qt6::Qml
    Qt6::Quick
)

qt_add_qml_module(testapp
    URI
        Test
    QML_FILES
        main.qml
        SettingsDrawer.qml
    RESOURCE_PREFIX
        /testapp
    RESOURCES
        icon_settings.png
    NO_RESOURCE_TARGET_PATH
)

qt_add_shaders(testapp "shaders"
    PREFIX
        /testapp
    FILES
        shaders/color.vert
        shaders/color.frag
)
