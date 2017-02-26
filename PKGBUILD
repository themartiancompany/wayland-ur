# Maintainer: Tom Gundersen <teg@jklm.no>
# Maintainer: Sébastien Luttringer <seblu@archlinux.org>
# Contributor: Joel Teichroeb <joel@teichroeb.net>

pkgname=wayland
pkgver=1.13.0
pkgrel=1
pkgdesc='A computer display server protocol'
arch=('i686' 'x86_64')
url='https://wayland.freedesktop.org/'
license=('MIT')
depends=('glibc' 'libffi' 'expat' 'libxml2')
validpgpkeys=('C7223EBE4EF66513B892598911A30156E0E67611') # Bryce Harrington
source=("https://wayland.freedesktop.org/releases/$pkgname-$pkgver.tar.xz"{,.sig})
sha1sums=('a8575325ed2885948624043c71629310df928312'
          'SKIP')

build() {
  cd $pkgname-$pkgver

  ./configure \
    --prefix=/usr \
    --disable-documentation \
    --disable-static
  make
}

package() {
  cd $pkgname-$pkgver

  make DESTDIR="$pkgdir" install
  install -Dm 644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set ts=2 sw=2 et:
