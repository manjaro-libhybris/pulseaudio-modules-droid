#Maintainer Erik Inkinen <erik.inkinen@gmail.com>
pkgname=pulseaudio-modules-droid
provides=('pulseaduio-modules-droid')
_pkgbase=pulseaudio-modules-droid
pkgver=568.2f14557
pkgrel=1
arch=('armv7h' 'aarch64' 'x86' 'x86_64')
url="https://github.com/mer-hybris/pulseaudio-modules-droid"
license=('GPL2')
depends=('pulseaudio-module-keepalive' 'pulseaudio' 'libevdev')
makedepends=('git' 'pkgconfig' 'android-headers' 'automake' 'autoconf' 'libhybris' 'pulsecore-headers')
source=("pulseaudio-modules-droid::git+https://github.com/droidian/pulseaudio-modules-droid.git")
md5sums=('SKIP')
options=(debug !strip)

pkgver() {
  cd "${srcdir}/${_pkgbase}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
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

