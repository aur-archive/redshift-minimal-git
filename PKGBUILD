# Maintainer: Alex Kir <alex@wall-dev.org>

pkgname=redshift-minimal-git
pkgver=1.8.r30.ge26337d
pkgrel=1
pkgdesc="Adjusts the color temperature of your screen according to your surroundings, with minimal dependencies."
arch=('i686' 'x86_64')
url="http://jonls.dk/redshift/"
license=('GPL3')
depends=('libxxf86vm')
makedepends=('python')
conflicts=('redshift' 'redshift-git' 'redshift-minimal')
provides=('redshift')
source=("$pkgname"::'git://github.com/jonls/redshift.git')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  git describe --long --tags | sed  -E 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$pkgname"
  ./bootstrap

  PYTHON=/usr/bin/python ./configure \
    --disable-geoclue \
    --disable-gui \
    --disable-ubuntu \
    --prefix=/usr

  make
}

package() {
  cd "$srcdir/$pkgname"
  make DESTDIR="$pkgdir" install
}
