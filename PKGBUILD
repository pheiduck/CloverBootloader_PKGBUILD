# Maintainer: pheiduck <pheiduck@github.com>

pkgname=clover-efi
pkgver=5136
pkgrel=4 #use the number of commits to main since this release
pkgdesc='Bootloader for macOS, Windows and Linux in UEFI and in legacy mode'
arch=('any')
url='https://github.com/CloverHackyColor/CloverBootloader'
_gitcommit=15199eea5d8722cd69568385288f08ad10f8b9c8
license=('BSD')
conflicts=('refind' 'opencore-efi')
backup=('boot/EFI/CLOVER/config.plist')
source=("https://github.com/CloverHackyColor/CloverBootloader/releases/download/$pkgver/Clover-$pkgver-X64.iso.7z")
noextract=("Clover-$pkgver-X64.iso.7z")
sha512sums=('5a3013228beec33f217e356adb24392e868670580db835e3c753fe6ebd0dd2af0ae5e582e9e9445419faecfe96d95942d130150f5fb3026e8eb5b763cdd789eb')

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
