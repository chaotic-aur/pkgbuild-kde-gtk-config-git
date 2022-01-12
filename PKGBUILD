# Merged with official ABS kjsembed PKGBUILD by dr460nf1r3, 2021/12/05 (all respective contributors apply herein)
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor Felix Yan <felixonmars@archlinux.org>
# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kde-gtk-config-git
pkgver=5.23.80_r917.gf96bb2f
pkgrel=1
pkgdesc='GTK2 and GTK3 Configurator for KDE'
arch=(x86_64)
url='https://kde.org/plasma-desktop/'
license=(LGPL)
depends=(qt5-svg kdecoration-git kconfigwidgets-git kdbusaddons-git)
makedepends=(extra-cmake-modules-git gtk3 sassc)
optdepends=('gtk3: GTK3 apps support' 'xsettingsd: apply settings to GTK applications on the fly')
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
groups=(plasma-git)
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(grep -m1 'set(PROJECT_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DCMAKE_INSTALL_LIBEXECDIR=lib \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
