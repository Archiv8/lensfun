#!/bin/bash

# Created from the original package by Peter Bartfai, "Alexandre Demers <alexandre.f.demers@gmail.com>"

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154

# Maintainer: Hyacinthe Cartiaux <hyacinthe.cartiaux@free.fr>
# Contributor: zhuqin <zhuqin83@gmail.com>
pkgname=lensfun
# pkgname=lensfun
pkgver=0.3.2.r2451.g37c25478
pkgrel=1
pkgdesc="Database of photographic lenses and a library that allows advanced access to the database"
arch=(i686 x86_64)
url="https://lensfun.github.io/"
license=('LGPL3')
depends=('glibc' 'glib2')
makedepends=('git' 'python' 'libpng' 'cmake')
optdepends=('python: for lensfun-update-data and lensfun-add-adapter')
provides=('lensfun=0.3.0')
conflicts=('lensfun')
source=("lensfun::git+https://github.com/lensfun/lensfun.git")
sha512sums=('SKIP')

pkgver() {
  cd $pkgname
  git describe --long | sed -r 's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd $pkgname
  cmake -DCMAKE_INSTALL_PREFIX=/usr \
        -DCMAKE_INSTALL_LIBDIR=lib \
        -DCMAKE_BUILD_TYPE=Release \
        .
  make
}

package() {
  cd $pkgname
  make DESTDIR="$pkgdir/" install
}
