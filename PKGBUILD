# Maintainer: Cedric Girard <girard.cedric@gmail.com>
# Maintainer: Jonas Strassel <info@jonas-strassel.de>

pkgname=wlay
pkgver=0.0.0
pkgrel=1
pkgdesc="Graphical output management for Wayland"

arch=('i686' 'x86_64')
url="https://github.com/atx/wlay"
license=('MIT')
makedepends=('git' 'cmake' 'extra-cmake-modules' 'wayland' 'glfw-wayland' 'libepoxy')
depends=('wayland' 'glfw-wayland' 'libepoxy')
provides=('wlay')
conflicts=('wlay' 'wlay-git')

_commit='1e316ca92d38856c517af4a0a7d88c8589bd2131'
source=("git+${url}.git#commit=${_commit}")
sha512sums=(
	'SKIP'
)

prepare(){
  cd "$srcdir"/wlay
  git submodule init
  git submodule update
}

build() {
  cd "$srcdir"/wlay
  cmake . \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd "$srcdir"/wlay
  make DESTDIR="$pkgdir/" install
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
