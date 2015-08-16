# Maintainer: Radu Andries <admiral0@tuxfamily.org>
pkgname=kdevelop-extra-plugins-qmake-git
pkgver=20110128
pkgrel=1
pkgdesc="Qmake Projects for kdevelop. Experimental plugin"
arch=('i686' 'x86_64' 'arm')
url="http://projects.kde.org/projects/extragear/kdevelop/experimental/kdev-qmake"
license=('GPL')
depends=('kdevelop-git' 'kdevelop-pg-qt-git')
makedepends=('git' 'cmake')

_gitroot="git://anongit.kde.org/kdev-qmake"
_gitname="kdev-qmake"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd "$srcdir/$_gitname"
  rm -rf build
  mkdir build
  cd build
  cmake -DCMAKE_INSTALL_PREFIX=/usr ..
  make
}

package() {
  cd "$srcdir/$_gitname/build"
  make DESTDIR="$pkgdir/" install
  rm -rf "$pkgdir/usr/share/apps/kdevappwizard"
} 
