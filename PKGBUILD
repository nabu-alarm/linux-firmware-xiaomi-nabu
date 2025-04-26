pkgname=linux-firmware-xiaomi-nabu
_commit="b17a3ce0f08871f1c4553351b2f64b2c6969cd5c"
pkgver=20241112
pkgrel=1
pkgdesc='Firmware for Xiaomi Pad 5'
url='https://gitlab.postmarketos.org/panpanpanpan/nabu-firmware'
arch=(any)
license=("proprietary")
makedepends=(
)
options=(
  !debug
  !strip
)
source=(
  "nabu-firmware-main.tar.gz::$url/-/archive/$_commit/nabu-firmware-main.tar.gz"
)
sha512sums=(
  '4cff180e0c765dd8d7c9b643699a685ec1394dbbca6420ca21ae4da005320f9aaade033fa5a348111457c7a141b2abc1112abee06d9d6f14f573ed78344587ac'
)
depends=(
  'linux-firmware'
)
optdepends=()
provides=()
conflicts=(
)
prepare=()
build=()

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
