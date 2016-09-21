# Maintainer: Tom Gundersen <teg@jklm.no>
# Maintainer: Sébastien Luttringer <seblu@archlinux.org>
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=wayland
pkgver=1.12.0
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('i686' 'x86_64')
url='http://wayland.freedesktop.org'
license=('MIT')
depends=('glibc' 'libffi' 'expat' 'libxml2')
makedepends=('doxygen' 'xmlto' 'graphviz' 'docbook-xsl')
validpgpkeys=('C7223EBE4EF66513B892598911A30156E0E67611') # Bryce Harrington
source=("http://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz"{,.sig})
sha1sums=('9a0dd96f53fff3e227035ed76caaa209b632ea8d'
          'SKIP')

build() {
  cd $pkgname-$pkgver

  ./configure \
    --prefix=/usr \
    --disable-static
  make
}

package() {
  cd $pkgname-$pkgver

  make DESTDIR="$pkgdir" install
  install -Dm 644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:
