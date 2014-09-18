pkgname=yarock
pkgver=0.9.67
pkgrel=1
pkgdesc="Yarock is Qt4 Modern Music Player with collection browser based on cover art."
arch=(x86_64)
url="https://launchpad.net/yarock"
license=('GPL3')
makedepends=('cmake' 'automoc4')
depends=('qt' 'taglib' 'phonon' 'qjson')
source=(https://launchpad.net/yarock/trunk/${pkgver}/+download/Yarock_${pkgver}_source.tar.gz)
md5sums=('957601ccafa55285d3494eae8943976b')

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
