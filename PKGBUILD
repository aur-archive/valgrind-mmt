# Maintainer: Tim Jester-Pfadt <t.jp(at)gmx.de>

pkgname=valgrind-mmt
pkgver=10641.a0b767b
pkgrel=1
pkgdesc="Valgrind with mmt tool to trace application accesses to mmaped memory"
arch=('i686' 'x86_64')
url="https://github.com/envytools/valgrind.git"
license=('BSD')
conflicts=(valgrind)
replaces=(valgrind)
makedepends=(git)
source=('git+https://github.com/envytools/valgrind.git' )
sha256sums=('SKIP')

prepare() {
  git clone https://github.com/envytools/VEX.git "$srcdir"/valgrind/VEX
  cd "$srcdir"/valgrind/VEX
  git checkout -f VEX_3_9_BRANCH
  cd ..
  git checkout -f mmt-3.9
}

build() {
  cd "$srcdir"/valgrind
  autoreconf -fi
  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir"/valgrind
  make DESTDIR="$pkgdir" install
}

pkgver() {
  cd "$srcdir"/valgrind
  echo $(git rev-list --count master).$(git rev-parse --short master)
}
