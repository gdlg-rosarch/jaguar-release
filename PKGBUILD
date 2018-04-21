# Script generated with Bloom
pkgdesc="ROS - Navigation package for DrRobot's Jaguar 4X4"
url='http://wiki.ros.org/jaguar'

pkgname='ros-kinetic-jaguar-navigation'
pkgver='0.1.0_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-roslaunch'
)

depends=('ros-kinetic-amcl'
'ros-kinetic-base-local-planner'
'ros-kinetic-dwa-local-planner'
'ros-kinetic-frontier-exploration'
'ros-kinetic-gmapping'
'ros-kinetic-map-server'
'ros-kinetic-move-base'
'ros-kinetic-navfn'
)

conflicts=()
replaces=()

_dir=jaguar_navigation
source=()
md5sums=()

prepare() {
    cp -R $startdir/jaguar_navigation $srcdir/jaguar_navigation
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

