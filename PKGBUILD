# Maintainer: Jason R. McNeil <jason@jasonrm.net>

pkgname=('gocd-server' 'gocd-agent')
_pkgver=16.3.0-3183
pkgver=${_pkgver/-/.}
pkgrel=1
pkgdesc="Automate and streamline the build-test-release cycle for worry-free, continuous delivery of your product."
arch=('any')
url='https://www.go.cd'
license=('Apache')
depends=()
makedepends=()
source=("https://download.go.cd/binaries/${_pkgver}/generic/go-server-${_pkgver}.zip"
        "https://download.go.cd/binaries/${_pkgver}/generic/go-agent-${_pkgver}.zip"
        "gocd-server.env"
        "gocd-agent.env"
        "gocd-server.service"
        "gocd-agent.service"
        "gocd-server.install"
        "gocd-agent.install")
sha1sums=('df41ed91cb1cd1439be8643c3401f0fdabd8fcb5'
          '98a475c18eb8ae462c737daef9740ecec0b2caaa'
          'da39a3ee5e6b4b0d3255bfef95601890afd80709'
          'ef23f9560add05d39d1a65fc5cb55cc503d2847b'
          '5caee35b2637895103b8e2569b7f912d026e35f5'
          'ed2d5bf64c07f9b988e5cc81ea0cb735f08cb980'
          'b1574082a0f83f16c0a78d3c39f749881a0d06ba'
          '2343b3eb907ee00e33ecd96e5b6a01f001ee582c')

package_gocd-server() {
    install='gocd-server.install'
    backup=('etc/conf.d/gocd-server')

    install -d ${pkgdir}/usr/lib/systemd/system
    install -m644 ${srcdir}/gocd-server.service ${pkgdir}/usr/lib/systemd/system

    install -d ${pkgdir}/etc/conf.d
    install -m644 ${srcdir}/gocd-server.env ${pkgdir}/etc/conf.d/gocd-server

    install -d ${pkgdir}/usr/share/gocd-server
    cp -r ${srcdir}/go-server-${_pkgver%-*}/* ${pkgdir}/usr/share/gocd-server/

    install -d ${pkgdir}/var/{log,lib}/gocd-server
}

package_gocd-agent() {
    install='gocd-agent.install'
    backup=('etc/conf.d/gocd-agent')

    install -d ${pkgdir}/usr/lib/systemd/system
    install -m644 ${srcdir}/gocd-agent.service ${pkgdir}/usr/lib/systemd/system

    install -d ${pkgdir}/etc/conf.d
    install -m644 ${srcdir}/gocd-agent.env ${pkgdir}/etc/conf.d/gocd-agent

    install -d ${pkgdir}/usr/share/gocd-agent
    cp -r ${srcdir}/go-agent-${_pkgver%-*}/* ${pkgdir}/usr/share/gocd-agent/

    install -d ${pkgdir}/var/{log,lib}/gocd-agent
}
