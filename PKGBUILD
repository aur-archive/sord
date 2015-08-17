# Maintainer: SpepS <dreamspepser at yahoo dot it>

pkgname=sord
pkgver=0.8.0
pkgrel=1
pkgdesc="A lightweight C library for storing RDF data in memory."
arch=(i686 x86_64)
url="http://drobilla.net/software/$pkgname/"
license=('custom:ISC')
depends=('serd>=0.14.0' 'serd<1.0.0' 'pcre')
makedepends=('python2')
source=("http://download.drobilla.net/$pkgname-$pkgver.tar.bz2")
md5sums=('62be6a2cd6e9bc2933d1297afeacda30')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # remove ldconfig
  sed -i "/ldconfig/d" wscript

  python2 ./waf configure --prefix=/usr \
                          --mandir=/usr/share/man
  python2 ./waf
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  DESTDIR="$pkgdir" python2 ./waf install

  # license
  install -Dm644 COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
