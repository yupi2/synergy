# synergy -- mouse and keyboard sharing utility
# Copyright (C) 2012-2016 Symless Ltd.
# Copyright (C) 2009 Nick Bolton
#
# This package is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public License
# found in the file LICENSE that should have accompanied this file.
#
# This package is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

file(GLOB sources "*.cpp")

if (SYNERGY_ADD_HEADERS)
	file(GLOB headers "*.h")
	list(APPEND sources ${headers})
endif()

include_directories(
	../
)

add_library(ipc STATIC ${sources})

if (NOT MSVC)
	target_link_libraries(ipc arch base mt io net synlib)
endif()
