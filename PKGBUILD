# Maintainer: Martin Müllenhaupt <mm+aur.archlinux.org@netlair.de>
pkgname=downlords-faf-client
pkgver=1.2.1
_pkgver_major=$(echo $pkgver | cut -d . -f 1)
_pkgver_minor=$(echo $pkgver | cut -d . -f 2)
_pkgver_tag=$(echo $pkgver | cut -d . -f 3)
#_pkgver_suffix=$(echo $pkgver | cut -d . -f 4)
#_pkgver="${_pkgver_major}.${_pkgver_minor}.${_pkgver_tag}-${_pkgver_suffix}"
#_filename="dfc_unix_${_pkgver_major}_${_pkgver_minor}_${_pkgver_tag}-${_pkgver_suffix}.tar.gz"
_pkgver="${_pkgver_major}.${_pkgver_minor}.${_pkgver_tag}"
_filename="dfc_unix_${_pkgver_major}_${_pkgver_minor}_${_pkgver_tag}.tar.gz"
pkgrel=2
epoch=0
pkgdesc="Forged Alliance Forever - Lobby Client. Community-driven client system for Supreme Commander: Forged Alliance. Downlord's Java client reimplementation."
url="http://www.faforever.com/"
arch=('any')
license=('MIT')
groups=()
checkdepends=()
optdepends=()
# Faf is broken with Arch's OpenJDK 14
# https://github.com/FAForever/downlords-faf-client/issues/1957
depends=('jre14')
makedepends=('jq')
replaces=()
backup=()
options=()
install=
changelog=
source=("https://github.com/FAForever/downlords-faf-client/releases/download/v$_pkgver/$_filename" "https://github.com/FAForever/downlords-faf-client/raw/develop/src/media/appicon/128.png" 'DownlordsFafClient.desktop' 'downlords-faf-client')
sha256sums=('322521547c6e774b5bf9c82fc165b0120e44f153730faa8fdfdff4b8ba069bb6'
            '2a5803ca2dd463aa4b53d79cff7f30e3aa7beb0d874b39c8ef59e679fbde9d3d'
            '3fd2b21da9de9f9c02dd89ee07f49c559dbb2de15f4e86a9b31f6353f608ffa6'
            '3df2ae7c886d03a899427e493583be2b1db8d5e557b3b83d4362ff7d5b1b32a7')
noextract=()
validpgpkeys=()

#pkgver() {
#  _pkgver=`curl -s https://api.github.com/repos/FAForever/downlords-faf-client/releases | jq -r '.[0].tag_name' | cut -d v -f 2 | sed "s/-/\./"`
#  _pkgver_major=$(echo $_pkgver | cut -d . -f 1)
#  _pkgver_minor=$(echo $_pkgver | cut -d . -f 2)
#   echo "${_pkgver_major}.${_pkgver_minor}.${_pkgver_tag}"
#  _pkgver_suffix=$(echo $_pkgver | cut -d . -f 4)
#   echo "${_pkgver_major}.${_pkgver_minor}.${_pkgver_tag}.${_pkgver_suffix}"
#}

package() {
  mkdir -p $pkgdir/usr/share/java
  tar xfv $_filename -C $pkgdir/usr/share/java
  _subdir="downlords-faf-client-${_pkgver}"
  mv $pkgdir/usr/share/java/$_subdir $pkgdir/usr/share/java/downlords-faf-client
  install -D "$srcdir/DownlordsFafClient.desktop" "$pkgdir/usr/share/applications/DownlordsFafClient.desktop"
  install -D "$srcdir/downlords-faf-client" "$pkgdir/usr/bin/downlords-faf-client"
  install -D "$srcdir/128.png" "$pkgdir/usr/share/java/downlords-faf-client/icon.png"
  chmod +x "$pkgdir/usr/share/java/downlords-faf-client/natives/faf-uid"
}
