# Maintainer: Thomas Kerpe <toke@toke.de>
# Description: PACKAGE only for my Workstation

pkgname=st-toke
appname='st'
conflicts=(${appname})
provides=(${appname})
replaces=('st')
pkgver=0.8.1
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X. Patched for solarized
colorscheme and Inconsolata-dz for Powerline font with anti-aliasing.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft' 'libxext' 'xorg-fonts-misc')
makedepends=('ncurses')

url="http://st.suckless.org"

source=(http://dl.suckless.org/st/$appname-$pkgver.tar.gz
        https://st.suckless.org/patches/externalpipe/st-externalpipe-0.8.diff
        https://st.suckless.org/patches/solarized/st-solarized-both-0.8.1.diff
        )
md5sums=(
         '92135aecdba29300bb2e274a55f5b71e'
         'ef7d8404215cb73e41c8fe63ff3356c5'
         '5bcc5c2d58bb71d2c7c258b3907ecc6d'
         )

prepare() {
  cd $srcdir/$appname-$pkgver
}

build() {
    cd $srcdir/$appname-$pkgver
    patch -i $srcdir/st-externalpipe-0.8.diff
    patch -i $srcdir/st-solarized-both-0.8.1.diff
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd $srcdir/$appname-$pkgver
    make PREFIX=/usr DESTDIR="$pkgdir" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$appname/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/$appname/README"
}
