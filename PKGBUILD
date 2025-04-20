# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=envrun
pkgver=0.7.4 # renovate: depName=Luzifer/envrun datasource=github-releases
pkgrel=1
pkgdesc="Helper utility to inject environment variables stored in a file into processes"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('e622dbe9b7b14c365aada11cdaf737f3173065e0f35768a21613ec5787fc2e773ee70d35bab7d3cb06c2e53a2d4f7ca23827669a5783c2fb6f854274af5b9672')

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
