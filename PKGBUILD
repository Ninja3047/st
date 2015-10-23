# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>

pkgname=st
pkgver=0.6
pkgrel=2
pkgdesc='A simple virtual terminal emulator for X.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft')
makedepends=('ncurses')
url="http://st.suckless.org"
source=(http://dl.suckless.org/st/$pkgname-$pkgver.tar.gz
        config.h
		st-0.6-delkey.diff
		st-0.6-spoiler.diff
		st-0.6-externalpipe.diff
		st-0.6-argbbg.diff
		st-0.6-base16-default-dark.diff)

prepare() {
	cd $srcdir/$pkgname-$pkgver
	patch -p1 -i ../st-$pkgver-spoiler.diff
	patch -p1 -i ../st-$pkgver-externalpipe.diff
	patch -p1 -i ../st-$pkgver-argbbg.diff
	patch -p2 -i ../st-$pkgver-base16-default-dark.diff
	cp config.def.h config.h
	sed -i "s/Liberation Mono:pixelsize=12:antialias=false:autohint=false/DejaVu Sans Mono for Powerline:pixelsize=13:antialias=false:autohint=false:Symbola:pixelsize=12/" config.h
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

md5sums=('1a926f450b4eacb7e2f5ac5b8ffea7c8'
         '19175b9c88dc1f9e567ce3c2f5cb2859'
         'a980eef9a13549e945af8e148ea43320'
         '31f2885958584fb4cc7499737170442a'
         '9ee68fc36d981aebdbedb04d5da15784'
         'b74286623d75f1474402a133d89e0f81'
         '57c7f7281659fa6f115f8baa7136fd98')
