# Maintainer Bardia Moshiri <fakeshell@bardia.tech>

pkgname=pulseaudio-modules-droid
provides=('pulseaduio-modules-droid')
_pkgbase=pulseaudio-modules-droid
pkgver=708.4d1bca1
pkgrel=2
arch=('armv7h' 'aarch64' 'x86' 'x86_64')
url="https://github.com/mer-hybris/pulseaudio-modules-droid"
license=('GPL2')
depends=('pulseaudio-hybris' 'libevdev')
makedepends=('git' 'pkgconfig' 'android-headers-30' 'automake' 'autoconf' 'libhybris' 'pulsecore-headers')
source=("pulseaudio-modules-droid::git+https://github.com/droidian/pulseaudio-modules-droid-modern.git")
md5sums=('SKIP')
options=(debug !strip)

pkgver() {
  cd "${srcdir}/${_pkgbase}"
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd "${srcdir}/${_pkgbase}"
  echo 14.2 > .tarball-version
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
