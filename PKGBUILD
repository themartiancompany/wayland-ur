# Maintainer: Tom Gundersen <teg@jklm.no>
# Maintainer: Sébastien Luttringer <seblu@archlinux.org>
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=wayland
pkgver=1.7.0
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('i686' 'x86_64')
url='http://wayland.freedesktop.org'
license=('MIT')
depends=('libffi' 'expat')
makedepends=('doxygen' 'xmlto' 'graphviz')
source=("http://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz")
sha1sums=('a731201534dcf6ec76a1184411724376cbf1acb6')

build() {
  cd $pkgname-$pkgver

  ./configure --prefix=/usr \
    --disable-static
  make
}

package() {
  cd $pkgname-$pkgver

  make DESTDIR="$pkgdir" install
  install -Dm 644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:
