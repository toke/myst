# Maintainer: Thomas Kerpe <toke@toke.de>
# Description: PACKAGE only for my Workstation

pkgname=st-toke
appname='st'
conflicts=(${appname})
provides=(${appname})
replaces=('st')
pkgver=0.7
pkgrel=4
pkgdesc='A simple virtual terminal emulator for X. Patched for solarized
colorscheme and Inconsolata-dz for Powerline font with anti-aliasing.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')

url="http://st.suckless.org"

source=(http://dl.suckless.org/st/$appname-$pkgver.tar.gz
        http://st.suckless.org/patches/st-externalpipe-20161125-e448324.diff
        #http://st.suckless.org/patches/st-no_bold_colors-$pkgver.diff
        http://st.suckless.org/patches/st-solarized-both-20160727-308bfbf.diff
        https://raw.githubusercontent.com/toke/myst/master/st-inconsolata-dz-for-powerline-aa.diff)

md5sums=(
         '29b2a599cf1511c8062ed8f025c84c63'
         'c54c87489342b8d77c6dd8f3c2ff997e'
         'b7219cf14d214086c9bb573cc87d1465'
         'fe644917dd56b371be5c9d54a6082318'
         )

prepare() {
  cd $srcdir/$appname-$pkgver
  # skip terminfo which conflicts with nsurses
  #sed -i '/\@tic /d' Makefile
  #cp $srcdir/config.h config.h
}

build() {
    cd $srcdir/$appname-$pkgver
    patch -i $srcdir/st-externalpipe-20161125-e448324.diff
    patch -i $srcdir/st-solarized-both-20160727-308bfbf.diff
    patch -i $srcdir/st-inconsolata-dz-for-powerline-aa.diff
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd $srcdir/$appname-$pkgver
    make PREFIX=/usr DESTDIR="$pkgdir" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$appname/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/$appname/README"
}
