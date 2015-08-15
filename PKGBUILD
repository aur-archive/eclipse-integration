# $Id$
# Maintainer : Ionut Biru <ibiru@archlinux.org>
# Contributor: Paul Mattal <paul@archlinux.org>
# Contributor: Andrew Wright <andreww@photism.org>
# Contributor: Andreas W. Hauser <andy-aur@splashground.de>
# Contributor: Marco Crosio <marco.crosio@gmail.com>
# Contributor: Roman Komkov <r.komkov@gmail.com>

pkgname=eclipse-integration
_date=20121002
_time=0800
pkgver=4.3_${_date}
pkgrel=3
pkgdesc="An IDE for Java and other languages. Integration version (updates depends on unit-test results)."
arch=('i686' 'x86_64')
url="http://eclipse.org"
depends=('java-environment' 'gtk2' 'unzip' 'libwebkit' 'libxtst')
install=${pkgname}.install
makedepends=('zip')
conflicts=('xulrunner' 'eclipse')
provides=('eclipse' 'eclipse=4.3')
license=("EPL/1.1")

source=("http://download.eclipse.org/eclipse/downloads/drops4/I${_date}-${_time}/eclipse-SDK-I${_date}-${_time}-linux-gtk-$CARCH.tar.gz"
	 'eclipse.sh' 'eclipse.desktop' 'eclipse.svg')
md5sums=('9cab571f7dd9cb770cf767bef24d42d5'
         '7ea99a30fbaf06ec29261541b8eb1e23'
         'ba8a37e30a7ebd69774cec87c69e8c44'
         '4df4cfe4a09135ceb35d1572d2248a52')
[ "$CARCH" = "x86_64" ] && source[0]="http://download.eclipse.org/eclipse/downloads/drops4/I${_date}-${_time}/eclipse-SDK-I${_date}-${_time}-linux-gtk-$CARCH.tar.gz"
[ "$CARCH" = "x86_64" ] && md5sums[0]='aae1016644770ba84e8fe3f1cf3e1601'

package() {
  # install eclipse
  install -m755 -d "$pkgdir/usr/share"
  mv eclipse "$pkgdir/usr/share/"

  # install misc
  install -d $pkgdir/usr/bin $pkgdir/usr/share/applications \
    $pkgdir/usr/share/icons/hicolor/{16x16,32x32,48x48,256x256}/apps
  install -m755 eclipse.sh "$pkgdir/usr/bin/eclipse"
  install -m644 eclipse.desktop "$pkgdir/usr/share/applications/"
  ln -s /usr/share/eclipse/plugins/org.eclipse.sdk_$pkgver.v${_date}/eclipse.png \
    "$pkgdir/usr/share/icons/hicolor/16x16/apps/eclipse.png"
  ln -s /usr/share/eclipse/plugins/org.eclipse.sdk_$pkgver.v${_date}/eclipse32.png \
    "$pkgdir/usr/share/icons/hicolor/32x32/apps/eclipse.png"
  ln -s /usr/share/eclipse/plugins/org.eclipse.sdk_$pkgver.v${_date}/eclipse48.png \
    "$pkgdir/usr/share/icons/hicolor/48x48/apps/eclipse.png"
  ln -s /usr/share/eclipse/plugins/org.eclipse.sdk_$pkgver.v${_date}/eclipse256.png \
    "$pkgdir/usr/share/icons/hicolor/256x256/apps/eclipse.png"

  # install icon
  install -Dm644 "$srcdir"/eclipse.svg \
    "$pkgdir"/usr/share/icons/hicolor/scalable/apps/eclipse.svg
  sed -i "s|#!/usr/bin/python|#!/usr/bin/python2|" "$pkgdir"/usr/share/eclipse/plugins/org.apache.ant_1.8.4.v201209061652/bin/runant.py
}
