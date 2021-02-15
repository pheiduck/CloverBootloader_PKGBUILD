# Maintainer: pheiduck <pheiduck@github.com>

pkgname=clover-efi
pkgver=5130
pkgrel=1
pkgdesc='Bootloader for macOS, Windows and Linux in UEFI and in legacy mode'
arch=('x86_64')
url='https://github.com/CloverHackyColor/CloverBootloader'
license=('BSD')
backup=('boot/EFI/CLOVER/config.plist')
source=("https://github.com/CloverHackyColor/CloverBootloader/releases/download/$pkgver/Clover-$pkgver-X64.iso.7z")
noextract=("Clover-$pkgver-X64.iso.7z")
sha256sums=('9d8aac06c2f47d538f7693202c35996ad486d0edf1a76d33a41b4b3700af603b')

prepare() {
  rm -rf EFI
  bsdtar -xf "Clover-$pkgver-X64.iso.7z" -O | bsdtar -xf - 'EFI'
}

package() {
  install -dm755 "$pkgdir/boot/EFI"
  install -dm755 "$pkgdir/usr/share/doc"

  install -D "EFI/BOOT/BOOTX64.efi" "$pkgdir/usr/lib/$pkgname/EFI/BOOT/BOOTX64.efi"

  cp --archive 'EFI/CLOVER' "$pkgdir/boot/EFI/CLOVER"
  mv -f "$pkgdir/boot/EFI/CLOVER/doc" "$pkgdir/usr/share/doc/$pkgname"
}
