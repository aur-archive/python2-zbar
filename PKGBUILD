# Maintainer: Andy Weidenbaum <archbaum@gmail.com>
# Contributor: Giorgio Gilestro <giorgio@gilest.ro>
# Contributor: Valentin Huélamo <vhuelamo@gmail.com>

pkgname=python2-zbar
pkgver=0.10
pkgrel=7
pkgdesc="Python bindings for zbar QR code & bar code reader (bindings only, conflicts with community/zbar)"
arch=('i686' 'x86_64')
depends=('python2' 'zbar')
makedepends=('gcc' 'python2-distribute')
url="https://pypi.python.org/pypi/zbar/"
license=('LGPL')
source=(https://pypi.python.org/packages/source/z/${pkgname#python2-}/${pkgname#python2-}-$pkgver.tar.gz
        https://pypi.python.org/packages/source/z/${pkgname#python2-}/${pkgname#python2-}-$pkgver.tar.gz.asc)
md5sums=('09568253d65e13e252987e3fd02e5ec8'
         'cc3cc73b96ef9773f1c184d68f2077ab')
sha256sums=('5d0dad77dbca8822a4689c546f598f28030321efb14fa36ac5e409d181a0d9dd'
            'ecff67e9505b6f7773beac1f6149d661566e3b083db32b61a0e58eba9172f3d2')
validpgpkeys=('3D3365F54E1EF3F0AB70639FDDCA6A34C19234A1')
conflicts=('zbar')

prepare() {
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Fixing Python version...'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/python#/usr/bin/python2#g'
  find . -type f -print0 | xargs -0 sed -i 's#/usr/bin/env python#/usr/bin/env python2#g'
}

build() {
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Building...'
  python2 setup.py build
}

package() {
  cd "$srcdir/${pkgname#python2-}-$pkgver"

  msg 'Installing...'
  python2 setup.py install --root="$pkgdir" --optimize=1
}
