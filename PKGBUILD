# Maintainer: 7sarus <63068332+7sarus@users.noreply.github.com>
pkgname=rstudio-desktop-bin
pkgver=2026.09.0.175
_pkgver=${pkgver%.*}-${pkgver##*.}
pkgrel=1
pkgdesc="An integrated development environment (IDE) for R (binary from RStudio official repository)"
arch=('aarch64')
license=('AGPL-3.0-or-later')
url="https://posit.co/products/open-source/rstudio/"
depends=('r>=3.3.0' 'sqlite' 'libxkbcommon')
optdepends=('clang: C/C++ and Rcpp code completion'
            'ttf-dejavu: fallback font support')
conflicts=('rstudio-desktop' 'rstudio-desktop-git' 'rstudio-desktop-preview-bin')
provides=("rstudio-desktop=${pkgver}")
options=(!strip !zipman)
PKGEXT='.pkg.tar'

source=("https://dl.dailies.rstudio.com/electron/jammy/arm64/rstudio-${_pkgver}-arm64.deb")
sha256sums=('686976be65f0f49421b7c0b51566395a50d4b685e8f9a8ee08cf76e7d4c89e09')

package() {
  cd "$srcdir"
  # deb files use ar
  tar Jxpf data.tar.xz -C "$pkgdir"

  install -dm755 "$pkgdir/usr/bin"

  ln -s /usr/lib/rstudio/rstudio "$pkgdir/usr/bin/rstudio"

  install -dm755 "$pkgdir/usr/share/licenses/$pkgname"
  ln -s /usr/lib/rstudio/resources/app/COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/COPYING"

}
