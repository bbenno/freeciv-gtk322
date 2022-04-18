# Maintainer: Benno Bielmeier <aur at bbenno dot com>

pkgname=freeciv-gtk322
_pkgname=freeciv
pkgver=3.0.1
pkgrel=1
pkgdesc="A multiuser clone of the famous Microprose game of Civilization - GTK3.22 Client"
arch=('i686' 'x86_64')
url="http://freeciv.org"
license=('GPL')
depends=(
	'pkgconf'
	'glib2>=2.50'
	'atk'
	'pango'
	'gdk-pixbuf2'
	'lua53'
	'gtk3>=3.22'
	'imagemagick'
	)
conflicts=('freeciv' 'freeciv-git' 'freeciv-sdl2')
makedepends=('gcc' 'make' 'libtool>=2.2' 'curl>=7.15.4' 'icu')
options=('!libtool')
provides=('freeciv-server' 'freeciv-gtk')
source=(http://files.freeciv.org/stable/$_pkgname-$pkgver.tar.xz)
sha256sums=('beda7adaebb3462797c8f090ec604c2974f15a1559fff2fb4cfff2607cb0180f')

build() {
  cd "$srcdir"/$_pkgname-$pkgver
  ./configure --prefix=/usr --sysconfdir=/etc --enable-shared --enable-sys-lua \
  --enable-client=gtk3.22 --enable-fcdb=sqlite3 --enable-aimodules
  make
}

package() {
  cd "$srcdir"/$_pkgname-$pkgver
  make DESTDIR="$pkgdir" install
  install -m644 client/org.freeciv.gtk322.desktop "$pkgdir"/usr/share/applications/org.freeciv.gtk322.desktop
}
