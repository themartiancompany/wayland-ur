# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Sébastien Luttringer <seblu@archlinux.org>
# Contributor: Tom Gundersen <teg@jklm.no>
# Contributor: Joel Teichroeb <joel@teichroeb.net>
# Contributor: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Contributor: Truocolo <truocolo@aol.com>

_checks="false"
_docs="false"
_pkg="wayland"
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
[[ "${_docs}" == "true" ]] && \
  pkgname+=(
    "${_pkg}-docs"
  )
pkgver=1.22.0
pkgrel=1
pkgdesc='A computer display server protocol'
arch=(
  'x86_64'
  'arm'
  'aarch64'
  'armv7h'
  'powerpc'
  'i686'
  'pentium4'
)
url="https://${_pkg}.freedesktop.org"
license=('MIT')
depends=(
  'glibc'
  'libffi'
  'expat'
  'libxml2'
  'default-cursors'
)
makedepends=(
  'meson'
  'libxslt'
  'graphviz'
)
[[ "${_docs}" == "true" ]] && \
  makedepends+=(
    docbook-xsl
    'doxygen'
    xmlto
  )

validpgpkeys=(
  'C7223EBE4EF66513B892598911A30156E0E67611'  # Bryce Harrington
  'C0066D7DB8E9AC6844D728715E54498E697F11D7'  # Derek Foreman
  '34FF9526CFEF0E97A340E2E40FDE7BE0E88F5E48') # emersion <contact@emersion.fr>
_url="https://gitlab.freedesktop.org/${_pkg}/${_pkg}"
source=(
  "${_url}/-/releases/$pkgver/downloads/${_pkg}-${pkgver}.tar.xz"{,.sig}
)
sha256sums=(
  '1540af1ea698a471c2d8e9d288332c7e0fd360c8f1d12936ebb7e7cbc2425842'
  'SKIP'
)

build() {
  local \
    _meson_opts=()
  _meson_opts=(
    -D documentation="${_docs}"
    -D tests="${_checks}"
  )
  arch-meson \
    "${pkgbase}-${pkgver}" \
      build \
      "${_meson_opts[@]}"
  meson \
    compile \
      -C \
        build
}

check() {
  meson \
    test \
      -C \
        build \
      --print-errorlogs
}

package_wayland() {
  provides=(
    "lib${_pkg}-"{client,cursor,egl,server}".so"
    "lib${_pkg}=${pkgver}"
  )
  conflicts=(
    "lib${_pkg}"
  )
  meson \
    install \
      -C build \
      --destdir \
        "${pkgdir}"
  if [[ "${_docs}" == "true" ]]; then
    mkdir \
      -p \
        docs/share
    mv \
      "${pkgdir}/usr/share/"{doc,man} \
      docs/share
  fi
  install \
    -Dm \
      644 \
    $pkgbase-$pkgver/COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

package_wayland-docs() {
  pkgdesc+=" (documentation)"
  depends=()
  mv \
    docs \
    "$pkgdir/usr"
  install \
    -Dm 644 \
    $pkgbase-$pkgver/COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

# vim:set sw=2 sts=-1 et:
