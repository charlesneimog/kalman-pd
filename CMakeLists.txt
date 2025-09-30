cmake_minimum_required(VERSION 3.28)

project(kalman)

cmake_policy(SET CMP0135 NEW)
set(PDCMAKE_FILE ${CMAKE_BINARY_DIR}/pd.cmake)
if(NOT EXISTS ${PDCMAKE_FILE})
    message(STATUS "Downloading pd.cmake")
    file(
        DOWNLOAD https://raw.githubusercontent.com/pure-data/pd.cmake/refs/tags/v0.2.6/pd.cmake ${PDCMAKE_FILE}
        SHOW_PROGRESS
        STATUS DOWNLOAD_STATUS)
endif()
include(${PDCMAKE_FILE})

pd_add_external(kalman kalman.c)
pd_add_datafile(kalman kalman-help.pd)
