cmake_minimum_required(VERSION 3.12)
 
include(FetchContent)
set(FETCHCONTENT_UPDATES_DISCONNECTED TRUE)
FetchContent_Declare(ftxui
  GIT_REPOSITORY https://github.com/ArthurSonzogni/ftxui
  GIT_TAG main # Important: Specify a version or a commit hash here.
)
FetchContent_MakeAvailable(ftxui)
 
project(ftxui-starter LANGUAGES CXX VERSION 1.0.0)

# Gather all source files from src/component, src/dom, and src/screen
file(GLOB COMPONENT_SOURCES "src/component/*.cpp")
file(GLOB DOM_SOURCES "src/dom/*.cpp")
file(GLOB SCREEN_SOURCES "src/screen/*.cpp")

# Add the executable and specify all source files
add_executable(ftxui-starter ${COMPONENT_SOURCES} ${DOM_SOURCES} ${SCREEN_SOURCES} src/main.cpp)

# Link the necessary libraries
target_link_libraries(ftxui-starter
  PRIVATE ftxui::screen
  PRIVATE ftxui::dom
  PRIVATE ftxui::component
)
