# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Allan McRae <allan@archlinux.org>

# toolchain build order: linux-api-headers->glibc->binutils->gcc->binutils->glibc

pkgname=linux-api-headers
pkgver=5.16.8
pkgrel=1
pkgdesc='Kernel headers sanitized for use in userspace'
arch=(any)
url='https://www.gnu.org/software/libc'
license=(GPL2)
makedepends=('rsync')
source=("https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-$pkgver.tar.xz")
sha256sums=('52aa5f05ee8addcc1ec0020f50e5f88ea1a308c2afac4a2305e1e4cf42580316')

build() {
  cd linux-$pkgver

  make mrproper
}

package() {
  cd linux-$pkgver
  make INSTALL_HDR_PATH="$pkgdir/usr" headers_install

  # use headers from libdrm
  rm -r "$pkgdir/usr/include/drm"
}
