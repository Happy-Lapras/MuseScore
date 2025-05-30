# SPDX-License-Identifier: GPL-3.0-only
# MuseScore-CLA-applies
#
# MuseScore
# Music Composition & Notation
#
# Copyright (C) 2021 MuseScore BVBA and others
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License version 3 as
# published by the Free Software Foundation.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <https://www.gnu.org/licenses/>.

declare_module(muse_dockwindow)
set(MODULE_ALIAS muse::dockwindow)

set(MODULE_QRC dock.qrc)

set(MODULE_SRC
    ${CMAKE_CURRENT_LIST_DIR}/dockmodule.cpp
    ${CMAKE_CURRENT_LIST_DIR}/dockmodule.h
    ${CMAKE_CURRENT_LIST_DIR}/docktypes.h
    ${CMAKE_CURRENT_LIST_DIR}/idockwindow.h
    ${CMAKE_CURRENT_LIST_DIR}/idockwindowprovider.h

    ${CMAKE_CURRENT_LIST_DIR}/internal/dockbase.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockbase.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/dropcontroller.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dropcontroller.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockseparator.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockseparator.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockframemodel.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockframemodel.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/docktabbar.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/docktabbar.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockwindowactionscontroller.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockwindowactionscontroller.h
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockwindowprovider.cpp
    ${CMAKE_CURRENT_LIST_DIR}/internal/dockwindowprovider.h

    ${CMAKE_CURRENT_LIST_DIR}/view/dockwindow.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockwindow.h
    ${CMAKE_CURRENT_LIST_DIR}/view/dockpageview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockpageview.h
    ${CMAKE_CURRENT_LIST_DIR}/view/dockpanelview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockpanelview.h
    ${CMAKE_CURRENT_LIST_DIR}/view/dockstatusbarview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockstatusbarview.h
    ${CMAKE_CURRENT_LIST_DIR}/view/docktoolbarview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/docktoolbarview.h
    ${CMAKE_CURRENT_LIST_DIR}/view/docktitlebar.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/docktitlebar.h
    ${CMAKE_CURRENT_LIST_DIR}/view/dockingholderview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockingholderview.h
    ${CMAKE_CURRENT_LIST_DIR}/view/dockcentralview.cpp
    ${CMAKE_CURRENT_LIST_DIR}/view/dockcentralview.h
    )

###########################################
# Setup the KDDockWidgets lib
###########################################
if (NOT BUILD_SHARED_LIBS)
    set(KDDockWidgets_STATIC ON CACHE BOOL "Build static versions of the libraries" FORCE)
endif(NOT BUILD_SHARED_LIBS)

set(KDDockWidgets_QT6 ON CACHE BOOL "Build against Qt 6" FORCE)
set(KDDockWidgets_QTQUICK ON CACHE BOOL "Build for QtQuick instead of QtWidgets" FORCE)
set(KDDockWidgets_EXAMPLES OFF CACHE BOOL "Build the examples" FORCE)
add_subdirectory(thirdparty/KDDockWidgets EXCLUDE_FROM_ALL)

set(MODULE_LINK kddockwidgets)

set(MODULE_QML_IMPORT ${CMAKE_CURRENT_LIST_DIR}/qml)

setup_module()

