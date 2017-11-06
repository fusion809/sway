# $Id$

pkgname=sway
pkgver=0.15
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
sha256sums=('80e1f0f255b2c47b956c6f850a6fa1c22c648081d2ec5fcf0ec0f836b5a34cbc')

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
