#Maintainer Erik Inkinen <erik.inkinen@gmail.com>
pkgname=pulseaudio-modules-droid
provides=('pulseaduio-modules-droid')
_pkgbase=pulseaudio-modules-droid
pkgver=9902.09074dc0
pkgrel=1
arch=('armv7h' 'aarch64' 'x86' 'x86_64')
url="https://github.com/mer-hybris/pulseaudio-modules-droid"
license=('GPL2')
depends=('pulseaudio-module-keepalive' 'pulseaudio')
makedepends=('git' 'pkgconfig' 'android-headers' 'automake' 'autoconf' 'libhybris' 'pulsecore-headers')
source=("pulseaudio-modules-droid::git+https://github.com/mer-hybris/pulseaudio-modules-droid.git" "0001-fix_build.patch")
md5sums=('SKIP' 'SKIP')
options=(debug !strip)

pkgver() {
  cd "${srcdir}/${_pkgbase}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

prepare() {
  cd "${srcdir}/${_pkgbase}"
  patch -p1 --input="${srcdir}/0001-fix_build.patch"
}

build() {
  cd "${srcdir}/${_pkgbase}"
  echo 15.0 > .tarball-version
  ./bootstrap.sh
  ./configure --disable-static \
    --prefix=/usr --mandir=/usr/share/man --libdir=/usr/lib \
    --sysconfdir=/etc --localstatedir=/var --sbindir=/usr/bin
  make KEEP_SYMBOLS=1 all
}

package() {
  cd "${srcdir}/${_pkgbase}"
  make DESTDIR="$pkgdir" install
}

