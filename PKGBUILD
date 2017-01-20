# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>
# Maintainer: Mikhail Burakov <mikhail.burakov gmail com>
# Maintainer: Joel Matthews <joelmatth gmail com>

pkgname=st-solarized-inconsolata-dz-powerline-aa
appname='st'
conflicts=(${appname})
provides=(${appname})
pkgver=0.7
pkgrel=1
pkgdesc='A simple virtual terminal emulator for X. Patched for solarized
colorscheme and Inconsolata-dz for Powerline font with anti-aliasing.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxext' 'libxft')
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
         'a89639acdb771011aea6446af68d7a47'
         )

build() {
    cd $srcdir/$appname-$pkgver
    patch -i $srcdir/st-externalpipe-20161125-e448324.diff
    patch -i $srcdir/st-solarized-both-20160727-308bfbf.diff
    patch -i $srcdir/st-inconsolata-dz-for-powerline-aa.diff
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd $srcdir/$appname-$pkgver
    make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$appname/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/$appname/README"
}
