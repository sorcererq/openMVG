# ==============================================================================
# Generic CMake File for QTBased project
# ==============================================================================

find_package( Qt5Widgets )

if(Qt5Widgets_FOUND)
  # CMake version control
  CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

  if(POLICY CMP0020)
  cmake_policy(SET CMP0020 OLD)
  endif(POLICY CMP0020)

  set(CMAKE_INCLUDE_CURRENT_DIR ON)
  set(CMAKE_AUTOMOC ON)
  # The name of my project.
  SET(ProjectName ui_openMVG_control_points_registration)
  PROJECT(${ProjectName})

  # All Source Files here
  SET(SourceFiles
  main.cpp
  MainWindow.cpp
  GraphicsView.cpp
  ControlPointTableView.cpp
  ControlPoint2DNode.cpp)

  # All non moc header files here
  SET(HeaderFiles
  MainWindow.hpp
  GraphicsView.hpp
  ControlPoint2DNode.hpp
  document.hpp
  ControlPointTableView.hpp)

  # ==============================================================================
  # Add the following files, modules and libraries to the project.
  # ==============================================================================
  # Files
  ADD_EXECUTABLE(${ProjectName} 
  ${SourceFiles}
  ${HeaderFiles} )
  #${MocSourceFiles})

  # Linking with Qt Libraries.
  TARGET_LINK_LIBRARIES(${ProjectName}
  Qt5::Widgets Qt5::Gui
  ${OpenMVG_LIBRARIES}
  )

  SET_PROPERTY(TARGET ${ProjectName} PROPERTY FOLDER OpenMVG/software/ui)
  INSTALL(TARGETS ${ProjectName} DESTINATION bin/)
endif(Qt5Widgets_FOUND)
