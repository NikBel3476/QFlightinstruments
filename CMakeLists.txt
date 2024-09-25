cmake_minimum_required(VERSION 3.25)
project(qflightinstruments VERSION 0.2.0 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)

set(CMAKE_WINDOWS_EXPORT_ALL_SYMBOLS TRUE)

if (NOT CMAKE_BUILD_TYPE)
	set(CMAKE_BUILD_TYPE Release)
else()
	set(CMAKE_BUILD_TYPE Debug)
endif()

find_package(Qt6 REQUIRED COMPONENTS
    Core
    Gui
    Widgets
    SvgWidgets
)

qt_standard_project_setup()

file(GLOB source_files
    ${PROJECT_SOURCE_DIR}/src/qfi/*.h
    ${PROJECT_SOURCE_DIR}/src/qfi/*.cpp
    ${PROJECT_SOURCE_DIR}/src/qfi/*.qrc
)

qt_add_library(${PROJECT_NAME} SHARED
    ${source_files}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
    Qt6::SvgWidgets
)