project(qtcudaprop)
cmake_minimum_required(VERSION 2.8.11)

set(${PROJECT_NAME}_VERSION_MAJOR 0)
set(${PROJECT_NAME}_VERSION_MINOR 3)

find_package(CUDA REQUIRED)
find_package(Qt5Widgets REQUIRED)

set(CMAKE_INCLUDE_CURRENT_DIR ON)

# CUDA SESSION
include_directories(${CUDA_INCLUDE_DIRS})

# QT SESSION
list(APPEND QT_LIBRARIES Qt5::Widgets)
set(CMAKE_AUTOMOC ON)
aux_source_directory(. SRC_LIST)
qt5_wrap_ui(SRC_LIST deviceinfowidget.ui mainwindow.ui)
add_executable(${PROJECT_NAME} ${SRC_LIST})

# LINKING SESSION
target_link_libraries(${PROJECT_NAME} ${QT_LIBRARIES} ${CUDA_LIBRARIES})
