# Maintainer: Tom Gundersen <teg@jklm.no>
# Contributor: Sébastien Luttringer
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=wayland
pkgver=1.0.5
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('i686' 'x86_64')
url='http://wayland.freedesktop.org'
license=('MIT')
depends=('libffi' 'expat')
makedepends=('doxygen')
options=(!libtool)
source=("http://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz")

build() {
  cd $pkgname-$pkgver
  ./configure --prefix=/usr
  make
}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="$pkgdir" install
  install -Dm 644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:
md5sums=('e2e9ebfbaf9b013471c620b99938d764')
