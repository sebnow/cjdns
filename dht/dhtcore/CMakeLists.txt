# You may redistribute this program and/or modify it under the terms of
# the GNU General Public License as published by the Free Software Foundation,
# either version 3 of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
find_package(Libevent2 REQUIRED)

add_library(dhtcore
    NodeStore.c
    RouterModule.c
    RouterModule_admin.c
    SearchStore.c
    Janitor.c
    VersionList.c
)

target_link_libraries(dhtcore
    cjdbenc
    util
    crypto
    switch
    ${LIBEVENT2_LIBRARIES}
    cjdns-util-version-version
)

# Everything must be tested.
enable_testing()
add_subdirectory(test)
