cmake_minimum_required(VERSION 2.8.12 FATAL_ERROR)
project(plastweet)

set(QT_MIN_VERSION "5.6.0")
set(KF5_MIN_VERSION "5.26.0")
set(CMAKE_AUTOMOC ON)
set(CMAKE_INCLUDE_CURRENT_DIR ON)

find_package(ECM 1.0.0 REQUIRED NO_MODULE)
add_definitions(-fexceptions)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${ECM_KDE_MODULE_DIR} ${CMAKE_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings)
include(FeatureSummary)

feature_summary(WHAT ALL FATAL_ON_MISSING_REQUIRED_PACKAGES)

find_package(Qt5 ${QT_MIN_VERSION} CONFIG REQUIRED Quick)
find_package(KF5 ${KF5_MIN_VERSION} REQUIRED COMPONENTS Plasma I18n)

add_subdirectory(plugin)
add_subdirectory(translations)

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -ltwitcurl -std=c++11 -g -s")

plasma_install_package(package com.gustawho.plastweet)