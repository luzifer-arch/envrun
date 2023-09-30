# Maintainer: Knut Ahlers <knut at ahlers dot me>

pkgname=envrun
pkgver=0.7.0
pkgrel=1
pkgdesc="Helper utility to inject environment variables stored in a file into processes"
arch=('i686' 'x86_64')
url="https://github.com/Luzifer/$pkgname"
license=('Apache')
makedepends=('go')
source=("${pkgname}-${pkgver}.tar.gz::${url}/archive/v${pkgver}.tar.gz")
sha512sums=('2c0453b809bdf7289cf4a7da48031e8ff3776d6f84e15a20e5de26d763c7dc3a95160b76d2511c9232b4b76c8ff13f54986e5b11d9100eee4e75cfda0954f135')

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
