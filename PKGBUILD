pkgname=downgrade
pkgver=5.2.1
pkgrel=1
pkgdesc="Bash script for downgrading one or more packages to a version in your cache or the A.R.M."
arch=('x86_64')
url="https://github.com/pbrisbin/$pkgname"
license=('GPL')
source=("https://github.com/pbrisbin/$pkgname/archive/v$pkgver.tar.gz")
md5sums=('eca007d8807d48ed967002612238901a')
optdepends=('sudo: for installation via sudo')

package() {
  local po_file

  cd "$pkgname-$pkgver"

  for po_file in locale/*.po; do
    locale="$(basename "$po_file" .po)"

    mkdir -p "$pkgdir/usr/share/locale/$locale/LC_MESSAGES/"
    msgfmt "$po_file" -o "$pkgdir/usr/share/locale/$locale/LC_MESSAGES/$pkgname.mo"
  done

  make PREFIX=/usr DESTDIR="$pkgdir" install
}

