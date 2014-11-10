pkgname=yarock
pkgver=1.0.0
pkgrel=1
pkgdesc="Yarock is Qt4 Modern Music Player with collection browser based on cover art."
arch=(x86_64)
url="https://launchpad.net/yarock"
license=('GPL3')
makedepends=('cmake' 'automoc4')
depends=('qt' 'taglib' 'phonon' 'qjson')
source=(https://launchpad.net/yarock/1.x/${pkgver}/+download/Yarock_${pkgver}_source.tar.gz)
md5sums=('a80e53a36502ba2f6c10bc6a3e04a473')

build() {
mkdir build
cd build
cmake ../Yarock_${pkgver}_source \
-DCMAKE_BUILD_TYPE=Release \
-DCMAKE_INSTALL_PREFIX=/usr
make
}

package() {
cd build
make DESTDIR="${pkgdir}" install
}
