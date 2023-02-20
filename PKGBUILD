# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=halium-9-sargo
pkgver=0.1
pkgrel=1
pkgdesc="sargo/bonito's Halium rootfs for Android 9"
arch=('aarch64')
url="https://github.com/manjaro-libhybris/halium-9-sargo"
license=('custom')
provides=('halium-gsi')
depends=('lxc')
conflicts=('halium-9-gsi' 'halium-10-gsi' 'halium-11-gsi')
makedepends=('wget' 'tar')
options=()

package() {
  LATEST=$(wget -q -O - https://ci.ubports.com/job/UBportsCommunityPortsJenkinsCI/job/ubports%252Fporting%252Fcommunity-ports%252Fjenkins-ci%252Fsargo/job/main/api/json | awk -F 'org.jenkinsci.plugins.workflow.job.WorkflowRun' '{print $2}' | cut -d '"' -f7)
  wget $LATEST/artifact/halium_sargo.tar.xz

  tar -xf halium_sargo.tar.xz

  mkdir -p ${pkgdir}/var/lib/lxc/android/

  install -m644 "$srcdir"/system/var/lib/lxc/android/android-rootfs.img "$pkgdir"/var/lib/lxc/android/android-rootfs.img
}
