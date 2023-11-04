# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=envrun
pkgver=0.7.1
pkgrel=1
pkgdesc="Helper utility to inject environment variables stored in a file into processes"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('2bf8c60857cd67ab6fad99d20f0b28333ba5c0041edd087d91f504a23c04b1b3e4b10c2a93fcacf67f33afefbae50a7adead5cfdc68923114bc2d22ff310602f')

build() {
	export GO111MODULE=on
	export GOPATH="${srcdir}/go"

	cd "${srcdir}/${pkgname}-${pkgver}"

	go build -a -v \
		-ldflags="-X main.version=${pkgver}" \
		-mod=readonly \
		-o "${srcdir}/${pkgname}"

	go clean -modcache
}

package() {
	install -Dm755 "${srcdir}/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "${srcdir}/${pkgname}-${pkgver}/LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
