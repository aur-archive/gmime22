# $Id: PKGBUILD 78820 2012-10-25 06:47:28Z foutrelis $
# Maintainer: Jan de Groot <jgc@archlinux.org>
# Contributor: Ben <ben@benmazer.net>

pkgname=gmime22
pkgver=2.2.26
pkgrel=2
pkgdesc="Core mime parsing library"
arch=(i686 x86_64)
license=('GPL')
url="http://spruce.sourceforge.net/gmime/"
depends=('glib2' 'zlib')
makedepends=('pkgconfig')
options=('!libtool')
source=(http://ftp.gnome.org/pub/GNOME/sources/gmime/2.2/gmime-${pkgver}.tar.bz2)
md5sums=('fed7c1beab58f5e5f4831c266fe974aa')

build() {
  # get rid of that .wapi errors in fakeroot
  export MONO_SHARED_DIR="${srcdir}/weird"
  mkdir -p "${MONO_SHARED_DIR}"

  cd ${srcdir}/gmime-${pkgver}
  [ $NOEXTRACT -eq 1 ] || ./configure --prefix=/usr --disable-mono
  make
  make DESTDIR=${pkgdir} install

  # These are gmime alternatives for the same shareutils tools
  rm -rf ${pkgdir}/usr/bin/uuencode ${pkgdir}/usr/bin/uudecode ${pkgdir}/usr/share
  mv ${pkgdir}/usr/bin/gmime-config ${pkgdir}/usr/bin/gmime22-config
}
