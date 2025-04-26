pkgname=linux-firmware-xiaomi-nabu
_commit="d15fc36a670ef186ca32cdbc3e940ab18bcc2505"
pkgver=20252604
pkgrel=1
pkgdesc='Firmware for Xiaomi Pad 5'
url='https://gitlab.postmarketos.org/panpanpanpan/nabu-firmware'
arch=(any)
license=("proprietary")
options=(
  !debug
  !strip
)
source=(
  "nabu-firmware-main.tar.gz::$url/-/archive/$_commit/nabu-firmware-main.tar.gz"
)
sha256sums=(
  '0ebc6f597f892472cbe458078ecbceb92c5150cd8bb2d2d740d98d0c97e57a2e'
)
depends=(
  'linux-firmware'
)

package() {
  builddir="$srcdir/nabu-firmware-$_commit"
  mkdir -p "$pkgdir"

  # adreno
  install -Dm644 "$builddir"/a630_sqe.fw -t \
    "$pkgdir/usr/lib/firmware/qcom/"
  install -Dm644 "$builddir"/a640_gmu.bin -t \
    "$pkgdir/usr/lib/firmware/qcom/"
  install -Dm644 "$builddir"/a640_zap.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"

  # adsp
  install -Dm644 "$builddir"/adsp.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"

  # cdsp
  install -Dm644 "$builddir"/cdsp.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"

  # cirrus
  # install -Dm644 "$builddir"/cs35l41* -t \
  #	"$pkgdir/usr/lib/firmware/cirrus/"

  # modem
  mkdir -p "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"
  cp -r "$builddir"/modem* \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"
  find "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/" \
    -type f -exec chmod 0644 {} \;

  # venus
  install -Dm644 "$builddir"/venus.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"

  # wlan
  install -Dm644 "$builddir"/wlanmdsp.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"
  # install -Dm644 "$builddir/firmware-5.bin" -t \
  #	"$pkgdir/usr/lib/firmware/ath10k/WCN3990/hw1.0"
  # install -Dm644 "$builddir/board-2.bin" -t \
  #	"$pkgdir/usr/lib/firmware/ath10k/WCN3990/hw1.0"

  # touchscreen
  install -Dm644 "$builddir"/novatek_nt36523_fw.bin -t \
    "$pkgdir/usr/lib/firmware/novatek/"

  # slpi
  install -Dm644 "$builddir"/slpi_nb.mbn -t \
    "$pkgdir/usr/lib/firmware/qcom/sm8150/xiaomi/nabu/"

  # hexagonfs
  mkdir -p "$pkgdir/usr/share/qcom/sm8150/xiaomi"
  cp -r "$builddir/hexagonfs/" \
    "$pkgdir/usr/share/qcom/sm8150/xiaomi/nabu"
}

# vim:set ts=8 sts=2 sw=2 et:
