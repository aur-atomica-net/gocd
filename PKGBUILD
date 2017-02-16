# Maintainer: Jason R. McNeil <jason@jasonrm.net>

pkgname=('gocd-server' 'gocd-agent')
_pkgver=17.1.0-4511
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
sha1sums=('f36e3b803ba677887c7330e8a8f4470b91395b48'
          '2052a8f5d7e6f0d307262be0c44b3abd587b7c10'
          'e4b548b7907e46af08770a541d1f603eb088751b'
          '09e34d3fa50dfad83b5a883769f73ed62cf4154d'
          'aeb696df73553d6245b0dc56245ae63ce5fee8d1'
          'aadfd8fe6a332c37645fbd3fabe322da072ff770'
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
