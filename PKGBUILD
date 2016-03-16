pkgname=yarock
pkgver=1.1.5
pkgrel=3
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
  cp -fr icon "${srcdir}/Yarock_${pkgver}_source/"
  cd "images"
  cp -fr genre.png "${srcdir}/Yarock_${pkgver}_source/images/media-playlist-48x48.png"
  cp -fr {computer-48x48.png,default-cover-120x120.png,download-48x48.png,equalizer-48x48-1.png,go-down_48x48.png,go-next_48x48.png,go-previous_48x48.png,go-up_48x48.png,home-48x48.png,jump_to_32x32.png,media-broken-18x18.png,media-next.png,media-pause.png,media-play.png,media-prev.png,media-repeat-1-48x48.png,media-shuffle-1-48x48.png,media-stop.png,settings-48x48.png,track-18x18.png,track-48x48.png,view-artist_18x18.png,view-artist.png,volume-muted.png} "${srcdir}/Yarock_${pkgver}_source/images"
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
