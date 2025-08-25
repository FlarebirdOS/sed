pkgname=sed
pkgver=4.9
pkgrel=1
pkgdesc="GNU stream editor"
arch=('x86_64')
url="https://www.gnu.org/software/sed/"
license=('GPL-3.0-or-later')
groups=('base' 'base-devel')
depends=('glibc' 'acl' 'attr')
options=('!lto')
source=(https://ftp.gnu.org/gnu/${pkgname}/${pkgname}-${pkgver}.tar.xz)
sha256sums=(6e226b732e1cd739464ad6862bd1a1aba42d7982922da7a53519631d24975181)

build() {
    cd ${pkgname}-${pkgver}

    local configure_args=(
        ${configure_options}
    )

    ./configure "${configure_args[@]}"

    make
    make html
}

package() {
    cd ${pkgname}-${pkgver}

    make DESTDIR=${pkgdir} install

    install -d -m755           ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}
    install -m644 doc/sed.html ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}
}
