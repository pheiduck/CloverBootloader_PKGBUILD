# Maintainer: pheiduck <pheiduck@github.com>

pkgname=clover-efi
pkgver=5138
pkgrel=0 #use the number of commits to main since this release
pkgdesc='Bootloader for macOS, Windows and Linux in UEFI and in legacy mode'
arch=('any')
url='https://github.com/CloverHackyColor/CloverBootloader'
_gitcommit=e6617e34970c6087ab7ffbdaea0400d07e431d2e
license=('BSD')
conflicts=('refind' 'opencore-efi')
backup=('boot/EFI/CLOVER/config.plist')
source=("https://github.com/CloverHackyColor/CloverBootloader/releases/download/$pkgver/Clover-$pkgver-X64.iso.7z")
noextract=("Clover-$pkgver-X64.iso.7z")
sha512sums=('4c964c1fe5abc7227ad9adc04b7ab66a8ed21ba9e59613df81aa1c07fd25972fc3cea268d20082561708e4be3de5824ab420e6061f817d9f87a9d44330c5a659')

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
