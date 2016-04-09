# Maintainer: Jason R. McNeil <jason@jasonrm.net>
# Contributor: Daichi Shinozaki <dsdseg@gmail.com>

pkgname=('gocd-server' 'gocd-agent')
pkgver=16.3.0
pkgrel=3183
pkgdesc="Automate and streamline the build-test-release cycle for worry-free, continuous delivery of your product."
arch=('any')
url='https://www.go.cd'
license=('Apache')
depends=()
makedepends=()
source=("https://download.go.cd/binaries/${pkgver}-${pkgrel}/generic/go-server-${pkgver}-${pkgrel}.zip"
        "https://download.go.cd/binaries/${pkgver}-${pkgrel}/generic/go-agent-${pkgver}-${pkgrel}.zip"
        "gocd-server.service"
        "gocd-agent.service"
        "gocd-server.install"
        "gocd-agent.install")
sha1sums=('df41ed91cb1cd1439be8643c3401f0fdabd8fcb5'
          '98a475c18eb8ae462c737daef9740ecec0b2caaa'
          'a4be16048176e4e2739adf6e3e777559a959d569'
          'd674bab5a4434b7f798758ed12705eb293465a86'
          'b1574082a0f83f16c0a78d3c39f749881a0d06ba'
          '2343b3eb907ee00e33ecd96e5b6a01f001ee582c')

package_gocd-server() {
    install='gocd-server.install'

    install -d ${pkgdir}/usr/lib/systemd/system
    install -m644 ${srcdir}/gocd-server.service ${pkgdir}/usr/lib/systemd/system

    install -d ${pkgdir}/usr/share/gocd-server
    cp -r ${srcdir}/go-server-${pkgver}/* ${pkgdir}/usr/share/gocd-server/

    install -d ${pkgdir}/var/{log,lib}/gocd-server
}

package_gocd-agent() {
    install='gocd-agent.install'

    install -d ${pkgdir}/usr/lib/systemd/system
    install -m644 ${srcdir}/gocd-agent.service ${pkgdir}/usr/lib/systemd/system

    install -d ${pkgdir}/usr/share/gocd-agent
    cp -r ${srcdir}/go-agent-${pkgver}/* ${pkgdir}/usr/share/gocd-agent/

    install -d ${pkgdir}/var/{log,lib}/gocd-agent
}
