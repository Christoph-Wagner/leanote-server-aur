# Maintainer: cwagner <github at cwagner dot me>

pkgname=leanote
pkgver=2.6.1
pkgrel=1
pkgdesc="Knowledge, Blog, Sharing, Cooperation."
arch=("i686" "x86_64")
url="https://leanote.com/"
license=("GPL3")
depends=("gconf")
makedepends=("gulp" "libarchive")
provides=("${pkgname}")
conflicts=("${pkgname}")
#install=$pkgname.install

source=("leanote")
sha256sums=('57155a0e423bc98f0e83acb35f03ace06b3de54bdc64b2373128671c801727b1')

source_x86_64=("${pkgname}-${pkgver}.tar.gz::https://sourceforge.net/projects/leanote-bin/files/${pkgver}/leanote-linux-amd64-v${pkgver}.bin.tar.gz/download")
source_i686=("${pkgname}-${pkgver}.tar.gz::https://sourceforge.net/projects/leanote-bin/files/${pkgver}/leanote-linux-386-v${pkgver}.bin.tar.gz/download")
sha256sums_x86_64=('e009ca6663c15626aafd51f0ed62f736d0287008f38c6dcfb935e98a3745eefa')
sha256sums_i686=('01180c07a960c36b129885df06e25b88578ca2acdd60420ea66e2f44840e7f75')
noextract=("${pkgname}-${pkgver}.tar.gz")

prepare() {
    echo "    Extracting files..."
    mkdir -p src
    bsdtar -xf ${pkgname}-${pkgver}.tar.gz -C src
}

build() {
    echo "    Cleanup directories..."
	cd "${srcdir}/src"
    rm -rf __MACOSX 
    rm -rf .DS_Store
}

package() {
    install -d "${pkgdir}"/opt
    install -D -m655 "./${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
    install -D -m644 "${srcdir}/src/${pkgname}.png" "${pkgdir}/usr/share/pixmaps/${pkgname}.png"
    install -D -m644 "${srcdir}/src/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    
    rm -rf "${srcdir}/src/LICENSE"
    rm -rf "${srcdir}/src/${pkgname}.png"

    cp -R ${srcdir}/src/ "${pkgdir}/opt/leanote"
}
