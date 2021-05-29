# Maintainer: pheiduck <pheiduck@github.com>

pkgname=clover-efi
pkgver=5135
pkgrel=30 #use the number of commits to main since this release
pkgdesc='Bootloader for macOS, Windows and Linux in UEFI and in legacy mode'
arch=('x86_64')
url='https://github.com/CloverHackyColor/CloverBootloader'
_gitcommit=8b2af7e287feb545bb1b405b1c8d7747fbfa7ae9
license=('BSD')
conflicts=('refind' 'opencore-efi')
backup=('boot/EFI/CLOVER/config.plist')
source=("https://github.com/CloverHackyColor/CloverBootloader/releases/download/$pkgver/Clover-$pkgver-X64.iso.7z")
noextract=("Clover-$pkgver-X64.iso.7z")
sha512sums=('6ba843902ff989355c0d3c9a23e63d813bf14c461e168c5e948891b876d03fa89d1ec5d40aba3b46c6724d73571b991a9f2f55dfaceafd5804759b606b8305a2')

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
