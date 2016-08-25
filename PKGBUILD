# Maintainer: Sameed Pervaiz <greenbagels@teknik.io>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: Xiao-Long Chen <chenxiaolong@cxl.epac.to>
# Contributor: Jakub Schmidtke <sjakub-at-gmail-dot-com>
# Contributor: mosra <mosra@centrum.cz>

pkgname=kdevplatform
pkgver=5.0.0
pkgrel=1
pkgdesc="A C/C++ development platform for KDE. (GIT Version)"
arch=('i686' 'x86_64')
url='http://www.kdevelop.org'
license=('GPL')
depends=('ktexteditor'
         'threadweaver'
         'kcmutils'
         'kitemmodels'
         'knewstuff'
         'knotifyconfig'
         'grantlee-qt5'
         'libkomparediff2'
         'hicolor-icon-theme'
         'llvm'
         'kde-cli-tools'
	 )
optdepends=('kompare-git: difference checking'
            'subversion: Subversion plugin')
makedepends=('cmake'
             'boost'
             'git'
             'extra-cmake-modules'
             'kdoctools'
             'subversion'
             )
source=("git://anongit.kde.org/kdevplatform.git#tag=v${pkgver}")
sha1sums=('SKIP')
install=kdevplatform.install

pkgver() {
  cd "${srcdir}/${pkgname}"
  git describe --tags `git rev-list --tags --max-count=1` | sed 's/v//g'
}

prepare() {
  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir -p build
}

build() {
  cd build
  cmake ../kdevplatform \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON \
    -DBUILD_TESTING=OFF
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
