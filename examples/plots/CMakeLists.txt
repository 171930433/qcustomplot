cmake_minimum_required(VERSION 3.10)

project(plot-examples)

# Set C++ standard
set(CMAKE_CXX_STANDARD 11)

# Find the Qt library
find_package(Qt5 COMPONENTS Core Gui Widgets PrintSupport REQUIRED)

# Include directories
include_directories(${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR})

# Source files
set(SOURCES
    main.cpp
    mainwindow.cpp
    ../../qcustomplot.cpp
)

# Header files
set(HEADERS
    mainwindow.h
    ../../qcustomplot.h
)

# UI files
set(FORMS
    mainwindow.ui
)

# Generate UI headers
qt5_wrap_ui(UI_HEADERS ${FORMS})

# Generate MOC files
qt5_wrap_cpp(MOC_SOURCES ${HEADERS})

# Add executable target
add_executable(${PROJECT_NAME} ${SOURCES} ${MOC_SOURCES} ${UI_HEADERS})

# Link Qt libraries
target_link_libraries(${PROJECT_NAME} PRIVATE Qt5::Core Qt5::Gui Qt5::Widgets Qt5::PrintSupport)
