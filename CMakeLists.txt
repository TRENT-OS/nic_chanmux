#
# NIC ChanMux driver
#
# Copyright (C) 2020-2024, HENSOLDT Cyber GmbH
#
# SPDX-License-Identifier: GPL-2.0-or-later
#
# For commercial licensing, contact: info.cyber@hensoldt.net
#

cmake_minimum_required(VERSION 3.17)


#-------------------------------------------------------------------------------
#
# Declare ChanMux NIC Driver CAmkES Component
#
# Parameters:
#
#   <name>
#     component instance name
#
#   <channel_ctrl>
#     ChanMux control channel ID
#
#   <channel_data>
#     ChanMux data channel ID
#

function(NIC_ChanMux_DeclareCAmkESComponent
    name
    channel_ctrl
    channel_data
)

    DeclareCAmkESComponent(
        ${name}
        SOURCES
            ${CMAKE_CURRENT_FUNCTION_LIST_DIR}/driver.c
        C_FLAGS
            -DCFG_CHANMUX_CHANNEL_CRTL=${channel_ctrl}
            -DCFG_CHANMUX_CHANNEL_DATA=${channel_data}
            -Wall
            -Werror
        LIBS
            os_core_api
            lib_debug
            chanmux_nic_driver
    )

endfunction()
