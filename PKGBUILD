# Maintainer: Abd El-Twab M. Fakhry <abdeltwab.m.fakhry@gmail.com>

pkgname=next-prayer
pkgver=2.0.0
pkgrel=1
pkgdesc="Islamic prayers reminder for your status bar."
arch=('x86_64')
url="https://github.com/abdeltwabmf/next-prayer.git"
license=('GPL-v3')
depends=(
	'libnotify'
)
makedepends=(
	'git'
	'python3'
)
provides=("${pkgname}")
conflicts=("${pkgname}")
source=("git+${url}")
sha1sums=('SKIP')

pkgver() {
	cd "${pkgname}"
	printf "%s.r%s.%s" "$(awk '/VERSION\[\] =/{print $5}' src/np_main.cpp | sed 's/\"\|;//g')" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${pkgname}"
	make DESTDIR="${pkgdir}"
}

package() {
	cd "${pkgname}"
	make DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
