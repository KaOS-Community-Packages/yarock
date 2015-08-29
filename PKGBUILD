pkgname=yarock
pkgver=1.1.3
pkgrel=1
pkgdesc="Qt Modern Music Player with collection browse based on cover art"
arch=('x86_64')
url="https://launchpad.net/yarock"
license=('GPL3')
makedepends=('cmake' 'mpv')
depends=('htmlcxx' 'qt5-x11extras' 'phonon-qt5' 'taglib')
optdepends=('mpv: alternative (working) engine')
source=("https://launchpad.net/yarock/1.x/${pkgver}/+download/Yarock_${pkgver}_source.tar.gz"
        "qt-build.patch"
        "phonon.patch")
md5sums=('4131e469cbd0bc717b44a0145c7b637a'
         '84e7160c3b4e055cdcc55551389ce08d'
         '87802d76e0bf86c10ec9969a62a12203')

prepare() {
  rm -rf "build"
  mkdir "build"

  # phonon include patch
  patch -p0 -i "phonon.patch"
  # patch to fix build with recent qt5
  patch -p0 -i "qt-build.patch"
}

build() {
  cd build
  cmake "../Yarock_${pkgver}_source" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DENABLE_QT5=1 \
    -DENABLE_MPV=ON
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
