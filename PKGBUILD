# Maintainer: Jeff Baitis <jeff@baitis.net>
pkgname=libextio_genesis
pkgver=3479960
pkgrel=1
pkgdesc="Library to support Genesis SDR hardware"
arch=('i686' 'x86_64')
url="https://github.com/wd8rde/libExtio_genesis/wiki"
license=('MIT')
groups=('')
depends=(
	'gcc-libs'
	'glibc'
	'hidapi'
	'libcap'
	'libsystemd'
	'libusb'
)
makedepends=(
	'git' 
	'libtool'
	'autoconf'
	'hidapi'
) # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${pkgname}-git")
conflicts=("${pkgname}-git")
source=("${pkgname}::git://github.com/wd8rde/libExtio_genesis")
md5sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	pkgver_git
}

pkgver_git() {
    cd "${srcdir}/${pkgname}"
    local ver="$(git show | grep commit | awk '{print $2}' )"
    echo ${ver:0:7}
}

build() {
	cd "$srcdir/${pkgname}/"
	./bootstrap
	./configure
	make
}

package() {
	cd "$srcdir/${pkgname}/"
	make DESTDIR="$pkgdir/" install
}
