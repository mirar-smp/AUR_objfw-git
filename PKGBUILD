# Contributor: mirar <mirar@aachen.ccc.de>
pkgver=0.7.1
pkgrel=1
arch=('i686' 'x86_64' 'mips64el' 'armv6h' 'armv7h')
depends=('clang>=3.3')
source=('https://webkeks.org/git/objfw.giti')


# Maintainer: Jonathan Schleifer <js@webkeks.org>
# Contributor: Alexander Fischer <alexander.fischer@kk-info.eu>

pkgname=objfw-git
pkgver=0.0.0
pkgrel=1
pkgdesc="A portable Objective-C framework"
arch=('i686' 'x86_64')
url="https://webkeks.org/objfw/"
license=('QPL' 'GPLv2' 'GPLv3')
depends=('clang')
makedepends=('git')
conflicts=('objfw')
provides=('objfw')
# The git repo is detected by the 'git:' or 'git+' beginning. The branch
# '$pkgname' is then checked out upon cloning, expediating versioning:
#source=('git+https://github.com/falconindy/expac.git'
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


