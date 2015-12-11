pkgname=yarock
pkgver=1.1.4
pkgrel=1
pkgdesc="Qt Modern Music Player with collection browse based on cover art"
arch=('x86_64')
url="https://launchpad.net/yarock"
license=('GPL3')
makedepends=('cmake' 'mpv')
depends=('htmlcxx' 'qt5-x11extras' 'phonon-qt5' 'taglib')
optdepends=('mpv: alternative (working) engine')
source=("https://launchpad.net/yarock/1.x/${pkgver}/+download/Yarock_${pkgver}_source.tar.gz" "taglib-1.10.patch")
md5sums=('794020bf0a571a24df6a6505d530f7c2' 'SKIP')

prepare() {
  rm -rf "build"
  mkdir "build"

  # patch to fix upgrade tabglib 1.10 
   patch -p0 -i taglib-1.10.patch
   
  # phonon include patch
  # patch -p0 -i "phonon.patch"
  # patch to fix build with recent qt5
  # patch -p0 -i "qt-build.patch"
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
