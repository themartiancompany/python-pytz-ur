# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
# Maintainer: Jelle van der Waa <jelle@vdwaa.nl>
# Contributor: Douglas Soares de Andrade <dsa@aur.archlinux.org>
# Contributor: William Rea <sillywilly@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=pytz
pkgname="${_py}-${_pkg}"
pkgver=2024.1
pkgrel=2
arch=(
  'any'
)
url="https://pypi.python.org/pypi/${_pkg}"
license=(
  "MIT"
)
pkgdesc="Cross platform time zone library for Python"
depends=(
  "${_py}>=${_pymajver}"
  "${_py}<${_pynextver}"
)
makedepends=(
  "${_py}"
  "${_py}-setuptools"
)
_pypi="https://pypi.io/packages/source"
source=(
  "${_pypi}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
  "0001-Use-the-system-zoneinfo-from-the-tzdata-package.patch"
)
sha512sums=(
  'cc1e4c9b34c62791cea277a0ce188d975e62135cb15bccfb49dc1a9366c7697ead9c67956846699f18b90db4c66e6c5fe1a91a524d01ae821c0eaa613550ea74'
  '3cbd497313c3049a2ae04298118aefb6dfa9ec4626078c665c95c13a78ae944b33a68813aea0c53b02b0532b64221cca4a0cd2153bd91b3760916bc3c0f6df8f'
)
validpgpkeys=(
  'C7ECC365AB6F255E1EB9BA1701FA998FBAC6374A'
)

prepare() {
  cd \
    "${_pkg}-${pkgver}"
  patch \
    -p2 \
    -i \
    "../0001-Use-the-system-zoneinfo-from-the-tzdata-package.patch"
  rm \
    -r \
    "${_pkg}/zoneinfo/"
}

build(){
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    setup.py \
      build
}

check(){
  cd \
    "${_pkg}-${pkgver}/${_pkg}/tests"
  "${_py}" \
    test_tzinfo.py
}

package(){
  cd \
    "${_pkg}-${pkgver}/${_pkg}/tests"
  "${_py}" \
    setup.py \
      install \
      --root="${pkgdir}/"
  install \
    -Dm644 \
    LICENSE.txt \
    "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
