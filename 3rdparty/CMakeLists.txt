# ECM
# ##############################################################################
check_submodule(extra-cmake-modules extra-cmake-modules)
# cmake-lint: disable=C0301
install_dependency(
  ECM
  "${CMAKE_CURRENT_SOURCE_DIR}/extra-cmake-modules"
  "-DBUILD_TESTING=OFF;-DBUILD_HTML_DOCS=OFF;-DBUILD_MAN_DOCS=OFF;-DBUILD_QTHELP_DOCS=OFF"
)
find_package(ECM CONFIG REQUIRED)
list(PREPEND CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

# KSyntaxHighlighting
# ##############################################################################
set(KSYNTAXHIGHLIGHTING_USE_GUI OFF)
set(DISABLE_ALL_OPTIONAL_SUBDIRECTORIES TRUE)
set(BUILD_TESTING OFF)
check_submodule(ksyntaxhighlighting ksyntaxhighlighting)
add_subdirectory(ksyntaxhighlighting)

