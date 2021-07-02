# Maintainer: pheiduck <pheiduck@github.com>

pkgname=clover-efi
pkgver=5137
pkgrel=9 #use the number of commits to main since this release
pkgdesc='Bootloader for macOS, Windows and Linux in UEFI and in legacy mode'
arch=('any')
url='https://github.com/CloverHackyColor/CloverBootloader'
_gitcommit=e6617e34970c6087ab7ffbdaea0400d07e431d2e
license=('BSD')
conflicts=('refind' 'opencore-efi')
backup=('boot/EFI/CLOVER/config.plist')
source=("https://github.com/CloverHackyColor/CloverBootloader/releases/download/$pkgver/Clover-$pkgver-X64.iso.7z")
noextract=("Clover-$pkgver-X64.iso.7z")
sha512sums=('ac515f7d422eb7d392d7831744b7a70bfa5690812115a96e26116b4c3c06a95beff4e9516e7c1c4e9ff249e07c00f7ca1fb0da1789a511f279be271f88365c86')

prepare() {
  rm -rf EFI
  bsdtar -xf "Clover-$pkgver-X64.iso.7z" -O | bsdtar -xf - 'EFI'
}

package() {
  install -dm755 "$pkgdir/boot/EFI"
  install -dm755 "$pkgdir/usr/share/doc"
  install -dm644 "$pkgdir/usr/share/licenses/$pkgname/LICENSE"

  install -D "EFI/BOOT/BOOTX64.efi" "$pkgdir/usr/lib/$pkgname/EFI/BOOT/BOOTX64.efi"

  cp --archive 'EFI/CLOVER' "$pkgdir/boot/EFI/CLOVER"
  mv -f "$pkgdir/boot/EFI/CLOVER/doc" "$pkgdir/usr/share/doc/$pkgname"
}
