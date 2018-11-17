# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>

pkgname=st
pkgver=0.8.1
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(http://dl.suckless.org/st/$pkgname-$pkgver.tar.gz
        config.h
        1-st-0.8-scrollback.diff	
	2-st-0.8-scrollback-mouse.diff
        3-st-0.8-scrollback-mouse-altscreen.diff
        4-st-0.8-alpha.diff
        5-st-0.8-base64-default-black.diff
        6-st-0.8-spoiler.diff)

prepare() {
	cd $srcdir/$pkgname-$pkgver
        patch -p1 -i ../1-st-0.8-scrollback.diff	
	patch -p1 -i ../2-st-0.8-scrollback-mouse.diff
        patch -p1 -i ../3-st-0.8-scrollback-mouse-altscreen.diff
        patch -p1 -i ../4-st-0.8-alpha.diff
        patch -p1 -i ../5-st-0.8-base16-default-dark.diff
        patch -p1 -i ../6-st-0.8-spoiler.diff
}

build() {
  cd $srcdir/$pkgname-$pkgver
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$pkgname-$pkgver
  sed -i '/\@tic /d' Makefile
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
	install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
	install -Dm644 README "$pkgdir/usr/share/doc/$pkgname/README"
}
