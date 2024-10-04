cmake_minimum_required(VERSION 3.25)
project(qfi_example VERSION 0.2.0 LANGUAGES CXX)

set(CMAKE_AUTOUIC ON)

find_package(Qt6 REQUIRED COMPONENTS
    Core
    Gui
    Widgets
    SvgWidgets
)

qt_standard_project_setup()

file(GLOB source_files
    ${PROJECT_SOURCE_DIR}/*.h
    ${PROJECT_SOURCE_DIR}/*.cpp
    ${PROJECT_SOURCE_DIR}/*.ui
    # main.cpp
    # LayoutSquare.cpp
    # MainWindow.cpp
    # WidgetAI.cpp
    # WidgetALT.cpp
    # WidgetASI.cpp
    # WidgetEADI.cpp
    # WidgetEHSI.cpp
    # WidgetHI.cpp
    # WidgetTC.cpp
    # WidgetVSI.cpp
    # WidgetSix.c
    # LayoutSquare.h
    # MainWindow.h
    # WidgetAI.h
    # WidgetALT.h
    # WidgetASI.h
    # WidgetEADI.h
    # WidgetEHSI.h
    # WidgetHI.h
    # WidgetTC.h
    # WidgetVSI.h
    # WidgetSix.h
    # MainWindow.ui
    # WidgetAI.ui
    # WidgetALT.ui
    # WidgetASI.ui
    # WidgetEADI.ui
    # WidgetEHSI.ui
    # WidgetHI.ui
    # WidgetTC.ui
    # WidgetVSI.ui
    # WidgetSix.ui
)

qt_add_executable(${PROJECT_NAME}
	${source_files}
)

if (MSVC)
	target_compile_options(${PROJECT_NAME} PRIVATE /W4)
else()
	target_compile_options(${PROJECT_NAME} PRIVATE -Wall -Wextra -Wpedantic)
endif()

set_target_properties(${PROJECT_NAME} PROPERTIES
	WIN32_EXECUTABLE TRUE
	MACOSX_BUNDLE TRUE
)

target_link_libraries(${PROJECT_NAME} PRIVATE
	Qt6::Core
	Qt6::Gui
	Qt6::Widgets
    Qt6::SvgWidgets
	qflightinstruments
)
