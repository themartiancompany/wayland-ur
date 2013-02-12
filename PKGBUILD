# Maintainer: Sébastien Luttringer
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=wayland
pkgver=1.0.4
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('i686' 'x86_64')
url='http://wayland.freedesktop.org'
license=('MIT')
depends=('libffi' 'expat')
makedepends=('doxygen')
options=(!libtool)
source=("http://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz")
sha1sums=('2f65654a54366cacd39a69bc5a41fea21b357e34')

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
