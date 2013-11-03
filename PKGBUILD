# Maintainer: Jonathan Schleifer <js@webkeks.org>
# Contributor: Alexander Fischer <alexander.fischer@kk-info.eu>

pkgname=objfw-git
pkgver=0.0.0
pkgrel=1
pkgdesc="A portable Objective-C framework"
arch=('i686' 'x86_64')
url="https://webkeks.org/objfw/"
license=('QPL' 'GPLv2' 'GPLv3')
depends=('clang' 'automake')
makedepends=('git')
conflicts=('objfw')
provides=('objfw')
source=("$pkgname"::'git+https://webkeks.org/git/objfw.git')
# Because the sources are not static, skip Git checksum:
md5sums=('SKIP')

pkgver() {
cd "$srcdir/$pkgname"
# Use the tag of the last commit
git describe --long | sed -E 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
cd "$srcdir/$pkgname"
./autogen.sh
./configure
make
}

package() {
cd "$srcdir/$pkgname"
make DESTDIR="$pkgdir" install
}


