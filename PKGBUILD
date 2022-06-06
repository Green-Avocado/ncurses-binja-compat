# Maintainer: Green-Avocado <greenavocado@protonmail.com>
# Contributor: Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Mateusz Gozdek <mgozdekof@gmail.com>
# Contributor: Allan McRae <allan@archlinux.org>
# Contributor: judd <jvinet@zeroflux.org>
# Contributor: Nick Shipp <git@segbrk.com>

pkgname=ncurses-binja-compat
_pkgname=ncurses
pkgver=1.0.0
_pkgver=6.3
pkgrel=1
pkgdesc='System V Release 4.0 curses emulation library, ABI 6, Binja compatible'
arch=(x86_64)
url='http://invisible-island.net/ncurses/ncurses.html'
license=(MIT)
depends=(glibc gcc-libs sh)
source=(https://ftp.gnu.org/pub/gnu/ncurses/ncurses-$_pkgver.tar.gz{,.sig})
sha256sums=('97fc51ac2b085d4cde31ef4d2c3122c21abc217e9090a43a30fc5ec21684e059' 'SKIP')
validpgpkeys=('19882D92DDA4C400C22C0D56CC2AF4472167BE03') # Thomas Dickey

build() {
    cd ${_pkgname}-${_pkgver}

    ./configure \
        --prefix=/usr \
        --mandir=/usr/share/man \
        --with-shared \
        --without-normal \
        --without-debug \
        --without-ada \
        --disable-widec \
        --disable-pc-files \
        --with-cxx-binding \
        --with-cxx-shared \
        --with-versioned-syms \
        --with-abi-version=6

    make
}

package() {
    cd ${_pkgname}-${_pkgver}

    make DESTDIR="$pkgdir" install.libs
    install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

    rm -rf \
        "$pkgdir/usr/include/" \
        "$pkgdir"/usr/lib/*.so
}
