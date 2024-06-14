# Maintainer: Filipe Laíns (FFY00) <lains@archlinux.org>

pkgname=urjtag
pkgver=2021.03
pkgrel=4
pkgdesc='Enhanced, modern tool for communicating over JTAG with flash chips, CPUs, and many more'
arch=('x86_64')
url='http://urjtag.org'
license=('GPL')
depends=('libftdi-compat' 'libusb-compat')
makedepends=('python' 'python-setuptools')
optdepends=('python: Python bindings')
source=("https://downloads.sourceforge.net/sourceforge/$pkgname/$pkgver/$pkgname-$pkgver.tar.xz"
        "0001-Add-support-for-Digilent-HS2-USB-dongle.patch")
sha512sums=('baf203e556d1d41437539d3f5c018b35fbb496f71391c2bec2786ffa47bff33d38654b3e7d106e38bcf36d075d86fc02b18eaaf634cdb65e2840ff50ca0da8b2'
            'd737bc023e407b08baebf355f5caa907a555efbce309614137c4534c4bc37f0dd2afabd5a82f79fbd734a9320b02f842b61e60a789f79199bf5b25fcf8adf52e')

prepare() {
  cd $pkgname-$pkgver
  patch -p2 -i "../0001-Add-support-for-Digilent-HS2-USB-dongle.patch"
}

build() {
  cd $pkgname-$pkgver

  autoreconf -vif

  ./configure \
        --prefix=/usr \
        --enable-svf \
        --enable-bsdl \
        --enable-stapl \
        --enable-python

  make
}

package() {
  cd $pkgname-$pkgver

  make DESTDIR="$pkgdir" install
}
