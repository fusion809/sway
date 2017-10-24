# $Id$

pkgname=sway
pkgver=0.15.rc3
_pkgver=${pkgver/.r/-r}
pkgrel=1
pkgdesc="i3 compatible window manager for Wayland"
arch=("i686" "x86_64")
url="http://swaywm.org"
license=("MIT")
backup=("etc/sway/security")
depends=(
	"wlc" "xorg-server-xwayland" "json-c" "pango" "wayland" "gdk-pixbuf2"
)
optdepends=(
	"rxvt-unicode: Default terminal emulator."
	"dmenu: Default for launching applications."
	"imagemagick: For taking screenshots."
	"ffmpeg: For recording screencasts."
	"i3status: To display system information with a bar."
)
makedepends=("cmake" "asciidoc")
source=(
#	"$pkgname-${_comm}.tar.gz::https://github.com/SirCmpwn/$pkgname/archive/${_comm}.tar.gz"
	"$pkgname-$pkgver.tar.gz::https://github.com/SirCmpwn/$pkgname/archive/${_pkgver}.tar.gz"
)
install="$pkgname.install"
sha256sums=('29c56c7394e774ec234883082ebbee480849426860f2e19ff7f86f3492e9a5d8')

build() {
        SRC=$srcdir/sway-${_pkgver}
#        SRC=$srcdir/sway-${_comm}
        cd $SRC
	mkdir -p build
	cd build
	cmake "$SRC" \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_SYSCONFDIR=/etc \
		-DCMAKE_INSTALL_PREFIX=/usr \
		-DVERSION="${_pkgver}"
	make
}

package() {
        SRC=$srcdir/sway-${_pkgver}
#        SRC=$srcdir/sway-${_comm}
        cd $SRC
	cd build
	DESTDIR="$pkgdir" make install
	install -Dm644 "$SRC/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
