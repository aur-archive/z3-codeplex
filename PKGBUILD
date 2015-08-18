# Maintainer: Marat Akhin <Marat.Akhin@gmail.com>

pkgname=z3-codeplex
pkgver=4.3.2
pkgrel=1
pkgdesc="Z3 is a high-performance theorem prover being developed at Microsoft Research (built from Codeplex sources, libraries only)"
arch=('i686' 'x86_64')
url="http://z3.codeplex.com/"
license=('custom')
makedepends=('python2')
provides=('z3' 'z3-lib')
conflicts=('z3' 'z3-lib')
source=("git+https://git01.codeplex.com/z3#tag=v$pkgver")
md5sums=('SKIP')

build() {
  cd "$srcdir/z3"

  PYTHON=/usr/bin/python2 ./configure --prefix="$srcdir/z3/build"

  cd "$srcdir/z3/build"
  make
}

package() {
  mkdir -p "$pkgdir/usr/include/z3"
  mkdir -p "$pkgdir/usr/lib"
  mkdir -p "$pkgdir/usr/lib/python2.7/site-packages"

  cd "$srcdir/z3/src/api"
  cp `find . -name "z3*.h"` "$pkgdir/usr/include/z3"
  cd "$srcdir/z3/src/api/c++"
  cp `find . -name "z3*.h"` "$pkgdir/usr/include/z3"

  cd "$srcdir/z3/build"
  cp `find . -name "libz3.*"` "$pkgdir/usr/lib"
  cp `find . -name "libz3.*"` "$pkgdir/usr/lib/python2.7/site-packages"
  cp `find . -name "z3*.pyc"` "$pkgdir/usr/lib/python2.7/site-packages"

  cd "$srcdir/z3/"
  install -Dm644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
