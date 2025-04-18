cmake_minimum_required(VERSION 3.10)
project(MWMS VERSION 1.0)

include_directories(include)
include_directories(${CMAKE_CURRENT_SOURCE_DIR}/include)

set(SOURCES
    src/App.cpp
    src/Settings.cpp
    src/core/User.cpp
    src/core/Role.cpp
    src/ui/MainFrame.cpp
    src/utilities/RenderText.cpp
    src/utilities/Session.cpp
    src/utilities/UserManager.cpp
    src/ui/panels/DashboardPanel.cpp
    src/ui/panels/LoginPanel.cpp
)

set(INCLUDES
    include/core
    include/ui
    include/ui/panels
    include/utilities
)

find_package(wxWidgets REQUIRED COMPONENTS core base)
include(${wxWidgets_USE_FILE})

add_executable(${PROJECT_NAME} ${SOURCES})

target_link_libraries(${PROJECT_NAME}
PUBLIC
    ${wxWidgets_LIBRARIES}
)

target_include_directories(${PROJECT_NAME}
PUBLIC
    ${wxWidgets_INCLUDE_DIRS}
    ${INCLUDES}
)
