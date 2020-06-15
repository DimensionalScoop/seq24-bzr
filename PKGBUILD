# Maintainer: quomoow <quomoow@gmail.com>
# Contributor: Sean Bartell <archlinux@yotann.org>
# Contributor: Jonathan Hadley <dermusikman@gmail.com>

pkgname=seq24-bzr
pkgver=0.9.3
pkgrel=2
pkgdesc="A pattern-based midi sequencer with strong live performance functions"
arch=('i686' 'x86_64')
url="http://launchpad.net/seq24"
license=('GPL')
depends=('gtkmm>=2.4.0')
makedepends=('bzr')
provides=('seq24')
conflicts=('seq24')
source=("bzr+https://code.launchpad.net/~${pkgname%-bzr}team/${pkgname%-bzr}/trunk" "my_mutex.patch")
md5sums=('SKIP' '4c5b9deab38ff7f2e09b5fbed76e04f5')

prepare() {
    cd trunk

    patch --forward --strip=1 --input="${srcdir}/my_mutex.patch"
}

build() {
    cd trunk

    autoreconf -i
    CXXFLAGS="-O2 -std=c++11"
    ./configure --prefix=/usr --disable-lash
    make
}

package() {
    cd trunk

    make DESTDIR="$pkgdir/" install
}
