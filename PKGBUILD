# Maintainer: D. Can Celasun <dcelasun[at]gmail[dot]com>
pkgname=n1
pkgver=0.3.26
pkgrel=1
pkgdesc="N1 is a new mail client for Mac, Linux and Windows, built on the modern web and designed to be extended."
arch=('x86_64')
url="https://nylas.com/N1/"
license=('MIT')
depends=('gtk2' 'libgnome-keyring' 'desktop-file-utils' 'python2' 'gconf' 'nodejs' 'libnotify' 'libxtst' 'nss' 'alsa-lib')
source=(N1-${pkgver}.deb::http://edgehill.s3-us-west-2.amazonaws.com/${pkgver}-c1ce330/linux/x64/N1.deb)
install=${pkgname}.install
md5sums=('736505cd02d424a1ebcec55f429d057b')
package() {
    msg2 "Extracting data.tar.gz..."
    bsdtar -xf data.tar.gz -C "${pkgdir}/"

    cd "${pkgdir}"
    find -name '*.py' -exec sed -i 's|^#!/usr/bin/env python\s*$|#!/usr/bin/env python2|' {} \;
    find -name '*.py' -exec sed -i 's|^#!/usr/bin/python\s*$|#!/usr/bin/python2|' {} \;

    mkdir -p "${pkgdir}"/usr/share/licenses/nylas-n1/

    rm -rf "${pkgdir}/usr/bin/nylas"
    ln -s /usr/share/nylas/nylas "${pkgdir}"/usr/bin/nylas
    ln -s /usr/share/nylas/LICENSE "${pkgdir}"/usr/share/licenses/nylas-n1/LICENSE
}

