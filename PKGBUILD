pkgname=lib32-libmagic
_pkgname=file
pkgver=5.19
pkgrel=2
pkgdesc='Magic number recognition library'
arch=('x86_64')
license=('custom')
groups=('base' 'base-devel')
url='http://www.darwinsys.com/file/'
depends=('glibc' 'zlib')
makedepends=('gcc-multilib')
source=("ftp://ftp.astron.com/pub/$_pkgname/$_pkgname-$pkgver.tar.gz")
md5sums=('e3526f59023f3f7d1ffa4d541335edab')

build() {
	export CC="gcc -m32"
	export CXX="g++ -m32"
	export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

	cd $_pkgname-$pkgver
	./configure --prefix=/usr --libdir=/usr/lib32 --datadir=/usr/share/lib32-libmagic
	make
}

package() {
	cd $_pkgname-$pkgver
	make DESTDIR="$pkgdir" install
	install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
	rm -rf "${pkgdir}"/usr/{include,share/man,bin}
}
