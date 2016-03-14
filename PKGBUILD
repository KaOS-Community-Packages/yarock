pkgname=yarock
pkgver=1.1.5
pkgrel=2
pkgdesc="Qt Modern Music Player with collection browse based on cover art"
arch=('x86_64')
url="https://launchpad.net/yarock"
license=('GPL3')
makedepends=('cmake' 'mpv')
depends=('htmlcxx' 'qt5-x11extras' 'phonon-qt5' 'taglib')
optdepends=('mpv: alternative engine (working)')
source=("https://launchpad.net/yarock/1.x/${pkgver}/+download/Yarock_${pkgver}_source.tar.gz"
        "git+https://github.com/fabianalexisinostroza/yarock_icons.git")
md5sums=('ec0d30272716e6e52915699d088e5fcc'
         'SKIP')

prepare() {
  rm -rf "build"
  mkdir "build"
  cd "${srcdir}/${pkgname}_icons"
  cp -fr {icon,images} "${srcdir}/Yarock_${pkgver}_source/"
}

build() {
  cd build
  cmake "../Yarock_${pkgver}_source" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DENABLE_QT5=1 \
    -DENABLE_VLC=OFF \
    -DENABLE_MPV=ON \
    -DENABLE_PHONON=ON \
    -DTAGLIB_MIN_VERSION=1.10
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}
