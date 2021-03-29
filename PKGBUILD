# $Id$
# Maintainer: PhotonX <photon89@googlemail.com>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=libbonoboui
pkgver=2.24.5
pkgrel=3
pkgdesc="User Interface library for Bonobo"
arch=('i686' 'x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('GPL' 'LGPL')
depends=('libgnomecanvas' 'libgnome')
makedepends=('intltool' 'pkg-config' 'python')
options=('!emptydirs')
url="http://www.gnome.org"
source=(https://download.gnome.org/sources/${pkgname}/2.24/${pkgname}-${pkgver}.tar.bz2
		config.guess
        config.sub)
sha256sums=('fab5f2ac6c842d949861c07cb520afe5bee3dce55805151ce9cd01be0ec46fcd'
			'7d1e3c79b86de601c3a0457855ab854dffd15163f53c91edac54a7be2e9c931b'
			'0c6489c65150773a2a94eebaa794b079e74a403b50b48d5adb69fc6cd14f4810')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  cp -vf ${srcdir}/config.guess	${srcdir}/${pkgname}-${pkgver}/
  cp -vf ${srcdir}/config.sub	${srcdir}/${pkgname}-${pkgver}/
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr --sysconfdir=/etc \
      --localstatedir=/var --disable-static
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
  rm -f "${pkgdir}/usr/share/applications/bonobo-browser.desktop"
}
