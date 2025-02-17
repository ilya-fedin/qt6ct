project(app)

set(app_SRCS
  appearancepage.cpp
  fontconfigdialog.cpp
  fontspage.cpp
  iconthemepage.cpp
  interfacepage.cpp
  main.cpp
  mainwindow.cpp
  paletteeditdialog.cpp
  qsseditordialog.cpp
  qsspage.cpp
  tabpage.cpp
  troubleshootingpage.cpp
  appearancepage.ui
  fontconfigdialog.ui
  fontspage.ui
  iconthemepage.ui
  interfacepage.ui
  mainwindow.ui
  paletteeditdialog.ui
  previewform.ui
  qsseditordialog.ui
  qsspage.ui
  troubleshootingpage.ui
)

if(Qt6LinguistTools_FOUND)
    list(APPEND app_SRCS translations/translations.qrc)
endif()

add_executable(qt6ct ${app_SRCS})
target_link_libraries(qt6ct PRIVATE Qt6::Widgets Qt6::GuiPrivate $<TARGET_NAME_IF_EXISTS:KF6::ConfigCore> qt6ct-common)
target_compile_definitions(qt6ct PRIVATE USE_WIDGETS $<$<TARGET_EXISTS:KF6::ConfigCore>:KF_CONFIGCORE_LIB> $<$<TARGET_EXISTS:KF6::ColorScheme>:KF_COLORSCHEME_LIB>)
install(TARGETS qt6ct DESTINATION ${CMAKE_INSTALL_BINDIR})
install(FILES qt6ct.desktop DESTINATION ${CMAKE_INSTALL_DATADIR}/applications)
