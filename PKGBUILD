# Maintainer: Sebastian kasb.smith@protonmail.com
pkgname=mc-server-manager-systemd
pkgver=1.0.0
pkgrel=1
pkgdesc="Minecraft server manager using systemd and screen"
arch=('any')
url=https://github.com/Arcticzomb/mc-server-manager-systemd
license=('GPL-3.0-or-later')
depends=('systemd' 'screen' 'java-runtime')
optdepends=('java-runtime-headless: headless Java runtime for servers')
backup=('etc/systemd/system/minecraft@.service')
install=${pkgname}.install
source=(
    "minecraft@.service::https://raw.githubusercontent.com/Arcticzomb/mc-server-manager-systemd/main/minecraft@.service"
    "README.md::https://raw.githubusercontent.com/Arcticzomb/mc-server-manager-systemd/main/README.md"
    "LICENSE::https://raw.githubusercontent.com/Arcticzomb/mc-server-manager-systemd/main/LICENSE"
)
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

package() {
    # Install systemd service file
    install -Dm644 "${srcdir}/minecraft@.service" \
        "${pkgdir}/usr/lib/systemd/system/minecraft@.service"
    
    # Install documentation
    install -Dm644 "${srcdir}/README.md" \
        "${pkgdir}/usr/share/doc/${pkgname}/README.md"
    install -Dm644 "${srcdir}/LICENSE" \
        "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
