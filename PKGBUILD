# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
# Maintainer: Jelle van der Waa <jelle@vdwaa.nl>
# Contributor: Douglas Soares de Andrade <dsa@aur.archlinux.org>
# Contributor: William Rea <sillywilly@gmail.com>

pkgname=('python-pytz' 'python2-pytz')
pkgver=2012c
pkgrel=1
arch=('any')
url="http://pypi.python.org/pypi/pytz"
license=("MIT")
makedepends=('python' 'python2')
source=(http://pypi.python.org/packages/source/p/pytz/pytz-$pkgver.tar.bz2{,.asc})
md5sums=('660e0cee7f6c419ca2665db460f65131'
         '1df919ab7f3987d03bc043d3fbfb8d07')



package_python-pytz(){
    depends=('python')
    pkgdesc="Cross platform time zone library for Python"

    cd $srcdir/pytz-$pkgver

    python setup.py install --root=$pkgdir/

    install -D LICENSE.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE
}

package_python2-pytz(){
    depends=('python2')
    pkgdesc="Cross platform time zone library for Python"

    cd $srcdir/pytz-$pkgver

    # python 2 fix
    sed -i 's_#!/usr/bin/env python_#!/usr/bin/env python2_' pytz/tzfile.py

    python2 setup.py install --root="$pkgdir/"

    install -D LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
