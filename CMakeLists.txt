cmake_minimum_required(VERSION 3.25)
project(qflightinstruments VERSION 0.2.0 LANGUAGES CXX)

set(CMAKE_AUTOMOC ON)

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

file(GLOB source_files
    ${PROJECT_SOURCE_DIR}/src/*.h
    ${PROJECT_SOURCE_DIR}/src/*.cpp
)

qt_add_library(${PROJECT_NAME} STATIC
    ${source_files}
)

target_link_libraries(${PROJECT_NAME} PRIVATE
    Qt6::Core
    Qt6::Gui
    Qt6::Widgets
    Qt6::SvgWidgets
)

target_include_directories(${PROJECT_NAME} INTERFACE
    ${CMAKE_CURRENT_SOURCE_DIR}/src
)

qt_add_resources(${PROJECT_NAME} "qfi_images"
    PREFIX "/qfi/"
    FILES
        images/eadi/eadi_back.svg
        images/eadi/eadi_mask.svg
        images/eadi/eadi_adi_back.svg
        images/eadi/eadi_adi_doth.svg
        images/eadi/eadi_adi_dotv.svg
        images/eadi/eadi_adi_fd.svg
        images/eadi/eadi_adi_ladd.svg
        images/eadi/eadi_adi_mask.svg
        images/eadi/eadi_adi_fpm.svg
        images/eadi/eadi_adi_fpmx.svg
        images/eadi/eadi_adi_roll.svg
        images/eadi/eadi_adi_scaleh.svg
        images/eadi/eadi_adi_scalev.svg
        images/eadi/eadi_adi_slip.svg
        images/eadi/eadi_adi_stall.svg
        images/eadi/eadi_adi_turn.svg
        images/eadi/eadi_alt_back.svg
        images/eadi/eadi_alt_bug.svg
        images/eadi/eadi_alt_frame.svg
        images/eadi/eadi_alt_ground.svg
        images/eadi/eadi_alt_scale.svg
        images/eadi/eadi_asi_back.svg
        images/eadi/eadi_asi_bug.svg
        images/eadi/eadi_asi_frame.svg
        images/eadi/eadi_asi_scale.svg
        images/eadi/eadi_asi_vne.svg
        images/eadi/eadi_hsi_back.svg
        images/eadi/eadi_hsi_bug.svg
        images/eadi/eadi_hsi_face.svg
        images/eadi/eadi_hsi_marks.svg
        images/eadi/eadi_vsi_scale.svg
        images/ehsi/ehsi_back.svg
        images/ehsi/ehsi_mask.svg
        images/ehsi/ehsi_mark.svg
        images/ehsi/ehsi_brg_arrow.svg
        images/ehsi/ehsi_cdi_from.svg
        images/ehsi/ehsi_cdi_to.svg
        images/ehsi/ehsi_crs_arrow.svg
        images/ehsi/ehsi_dev_bar.svg
        images/ehsi/ehsi_dev_scale.svg
        images/ehsi/ehsi_hdg_bug.svg
        images/ehsi/ehsi_hdg_scale.svg
        images/ai/ai_back.svg
        images/ai/ai_case.svg
        images/ai/ai_face.svg
        images/ai/ai_ring.svg
        images/alt/alt_case.svg
        images/alt/alt_face_1.svg
        images/alt/alt_face_2.svg
        images/alt/alt_face_3.svg
        images/alt/alt_hand_1.svg
        images/alt/alt_hand_2.svg
        images/asi/asi_case.svg
        images/asi/asi_face.svg
        images/asi/asi_hand.svg
        images/hi/hi_case.svg
        images/hi/hi_face.svg
        images/tc/tc_case.svg
        images/tc/tc_back.svg
        images/tc/tc_ball.svg
        images/tc/tc_face_1.svg
        images/tc/tc_face_2.svg
        images/tc/tc_mark.svg
        images/vsi/vsi_case.svg
        images/vsi/vsi_face.svg
        images/vsi/vsi_hand.svg
)

# add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/example)