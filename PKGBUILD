# $Id$
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=libkdegames
pkgver=17.04.3
pkgrel=1
pkgdesc="Common code and data for many KDE games"
url="https://www.kde.org/applications/games/"
arch=('i686' 'x86_64')
license=('GPL' 'LGPL' 'FDL')
depends=('kdelibs4support' 'kdeclarative' 'kdnssd' 'knewstuff' 'openal')
makedepends=('extra-cmake-modules' 'python' 'kdoctools')
source=("https://download.kde.org/stable/applications/${pkgver}/src/${pkgname}-${pkgver}.tar.xz"{,.sig})
sha256sums=('e80ae48e631f0a4af496f6a1ba055784c9f267fdd0fc6a3770afda6e579d450a'
            'SKIP')
validpgpkeys=(CA262C6C83DE4D2FB28A332A3A6A4DB839EAA6D7  # Albert Astals Cid <aacid@kde.org>
              F23275E4BF10AFC1DF6914A6DBD2CE893E2D1C87) # Christoph Feck <cfeck@kde.org>

build() {
  mkdir -p build
  cd build
  cmake ../${pkgname}-${pkgver} \
    -DCMAKE_BUILD_TYPE=Release \
    -DBUILD_TESTING=OFF \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DKDE_INSTALL_LIBDIR=lib
  make
}

package() {
  cd build
  make DESTDIR="${pkgdir}" install
}