# Maintainer: Maxime Morel <maxime@mmorel.eu>

pkgname=dali-toolkit-git
pkgver=1.0.40
pkgrel=1
pkgdesc="OpenGl based 3D GUI toolkit - toolkit"
arch=('x86_64' 'i686')
url="git://git.tizen.org/platform/core/uifw/dali-toolkit"
license=('APACHE')
depends=('dali-adaptor-git')
makedepends=('git' 'autoconf' 'boost')
provides=('dali-toolkit')
conflicts=('dali-toolkit')
source=("git://git.tizen.org/platform/core/uifw/dali-toolkit")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/dali-toolkit"
  printf "%s" "$(git describe | sed -r 's/^dali_(.*)-[0-9]+-[a-z0-9]+$/\1/')"
}

prepare() {
  cd "$srcdir/dali-toolkit/build/tizen"
  sed -i '/SUBDIRS += docs/d' Makefile.am
}

build() {
  cd "$srcdir/dali-toolkit/build/tizen"
  autoreconf --install
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/dali-toolkit/build/tizen"
  make DESTDIR="$pkgdir/" install
}

