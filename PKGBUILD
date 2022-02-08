# Maintainer:  Bartłomiej Piotrowski <bpiotrowski@archlinux.org>
# Contributor: Allan McRae <allan@archlinux.org>

# toolchain build order: linux-api-headers->glibc->binutils->gcc->binutils->glibc

pkgname=linux-api-headers
pkgver=5.16.7
pkgrel=1
pkgdesc='Kernel headers sanitized for use in userspace'
arch=(any)
url='https://www.gnu.org/software/libc'
license=(GPL2)
makedepends=('rsync')
source=("https://cdn.kernel.org/pub/linux/kernel/v5.x/linux-$pkgver.tar.xz")
sha256sums=('5751f53e8e5415eb0494ac1513765cbdea28848963999dfdb5d4e7f4c3d8a6cd')

build() {
  cd linux-$pkgver

  make mrproper
  make headers_check
}

package() {
  cd linux-$pkgver
  make INSTALL_HDR_PATH="$pkgdir/usr" headers_install

  # use headers from libdrm
  rm -r "$pkgdir/usr/include/drm"
}
