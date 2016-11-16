# Contributor: Patrick Jackson <PatrickSJackson gmail com>
# Maintainer: Christoph Vigano <mail@cvigano.de>
# Maintainer: Mikhail Burakov <mikhail.burakov gmail com>
# Maintainer: Joel Matthews <joelmatth gmail com>

pkgname=st-solarized-inconsolata-dz-powerline-aa
appname='st'
conflicts=(${appname})
provides=(${appname})
pkgver=0.6
pkgrel=0
pkgdesc='A simple virtual terminal emulator for X. Patched for solarized
colorscheme and Inconsolata-dz for Powerline font with anti-aliasing.'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxext' 'libxft')
makedepends=('ncurses')
url="http://st.suckless.org"

source=(http://dl.suckless.org/st/$appname-$pkgver.tar.gz
        http://st.suckless.org/patches/st-externalpipe-0.6.diff
        http://st.suckless.org/patches/st-no_bold_colors-0.6.diff
        http://st.suckless.org/patches/st-solarized-dark-0.6.diff
        https://raw.githubusercontent.com/toke/myst/master/st-inconsolata-dz-for-powerline-aa.diff)

md5sums=('1a926f450b4eacb7e2f5ac5b8ffea7c8'
         '9ee68fc36d981aebdbedb04d5da15784'
         '318bffa6a563970754554694107b1ca1'
         'cd75677133a2d6b3111fec5ae1b466bd'
         '577f3dba477c2845f473784489da48c7')

build() {
  cd $srcdir/$appname-$pkgver
  patch -i $srcdir/st-externalpipe-0.6.diff
  patch -i $srcdir/st-no_bold_colors-0.6.diff
  patch -i $srcdir/st-solarized-dark-0.6.diff
  patch -i $srcdir/st-inconsolata-dz-for-powerline-aa.diff
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $srcdir/$appname-$pkgver
  make PREFIX=/usr DESTDIR="$pkgdir" TERMINFO="$pkgdir/usr/share/terminfo" install
    install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$appname/LICENSE"
    install -Dm644 README "$pkgdir/usr/share/doc/$appname/README"
}
