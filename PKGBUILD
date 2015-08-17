# Maintainer: Andrea Scarpino <andrea@archlinux.org>

pkgname=telepathy-qt5-git
pkgver=0.9.3.38.g0191a6d
pkgrel=1
pkgdesc="A library for Qt5-based Telepathy clients"
arch=('i686' 'x86_64')
url="http://telepathy.freedesktop.org"
license=('LGPL')
depends=('qt5-base' 'telepathy-farstream')
makedepends=('libxslt' 'python2' 'cmake' 'git' 'doxygen')
conflicts=('telepathy-qt5')
provides=('telepathy-qt5')
options=('!libtool' 'staticlibs')
source=(git://git.collabora.co.uk/git/freedesktop.org-mirror/telepathy/telepathy-qt.git)
md5sums=('SKIP')

pkgver() {
  cd telepathy-qt
  git describe --always | sed 's|-|.|g;s|telepathy.qt.||'
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../telepathy-qt \
      -DCMAKE_INSTALL_PREFIX=/usr \
      -DCMAKE_BUILD_TYPE=Release \
      -DPYTHON_EXECUTABLE=/usr/bin/python2 \
      -DCMAKE_POSITION_INDEPENDENT_CODE=on \
      -DQT_QMAKE_EXECUTABLE=qmake-qt5 \
      -DENABLE_EXAMPLES=OFF \
      -DENABLE_TESTS=false \
      -DENABLE_EXPERIMENTAL_SERVICE_SUPPORT=ON
  make
}

package() {
  cd build
  make DESTDIR="$pkgdir" install
}
