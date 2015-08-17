# Maintainer: Arslan Atajanov <drzyx.enyx@gmail.com>

pkgname=pyclutter
pkgver=1.3.2
pkgrel=4
pkgdesc="Python bindings to Clutter."
arch=('i686' 'x86_64')
url="http://blogs.gnome.org/clutter/"
license=('GPL')
depends=('glib2>=2.16.0' 'gtk2>=2.10.0' 'clutter>=1.0.0' 'python2-cairo>=1.0.2' 'pygobject>=2.21.3' 'python2>=2.6.0' 'pygtk')
options=('!libtool')
source=(http://pkgs.fedoraproject.org/repo/pkgs/$pkgname/$pkgname-$pkgver.tar.bz2/36137bace35d03af4caf20747ccdc5c2/$pkgname-$pkgver.tar.bz2
        $pkgname.patch)
md5sums=('36137bace35d03af4caf20747ccdc5c2'
         'e071cfcf3c4c811c9c47488f68452663')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  
  find . -name '*.py' -print0|xargs -0 \
      sed -i -e 's,^#!/usr/bin/env python$,#!/usr/bin/env python2,' \
             -e 's,^#!/usr/bin/python$,#!/usr/bin/python2,'

  export PYTHON=/usr/bin/python2

  patch -Np1 -i ../$pkgname.patch
  ./configure --prefix=/usr
  make || return 1
  make DESTDIR="$pkgdir" install
}

