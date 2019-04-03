
pkgname=polybar
pkgver=3.3.1
pkgrel=1
pkgdesc="A fast and easy-to-use status bar"
arch=("x86_64")
url="https://github.com/jaagr/polybar"
license=("MIT")
depends=("cairo" "xcb-util-image" "xcb-util-wm" "xcb-util-xrm" "xcb-util-cursor")
makedepends=("cmake" "git" "python3" "pkg-config")
source=(${url}/releases/download/${pkgver}/polybar-${pkgver}.tar)
sha256sums=('b0982a729f99f658d77969fd582d074843a57982b5e7c6b2b6efee5480b2a81c')

prepare() {
  mkdir -p "${pkgname}/build"
}

build() {
  cd "${pkgname}/build" || exit 1
  cmake -DCMAKE_INSTALL_PREFIX=/usr ..
  cmake --build .
}

package() {
  cmake --build "${pkgname}/build" --target install -- DESTDIR="${pkgdir}"
  install -Dm644 "${pkgname}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
