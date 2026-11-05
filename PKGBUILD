# Maintainer: Sergey Kanafyev <sergeykanafyev@gmail.com>
# Contributor: Christian Wieden <wiedenchr@gmail.com>
# Automation: https://github.com/its-me/aur.hstr

pkgname=hstr
pkgver=.3.3
pkgrel=1
pkgdesc="Bash and Zsh shell history suggest box - easily view, navigate, search and manage your command history."
arch=('x86_64')
url="https://github.com/dvorka/hstr"
license=('Apache')
makedepends=('readline' 'ncurses')
depends=('readline')
source=("https://github.com/dvorka/${pkgname}/archive/v${pkgver}.tar.gz")
sha256sums=('ca458520804b1494ac3af4cfaafe484468ff00978aa4528fc4ef0536e383374a')


build() {
    cd "${pkgname}-${pkgver}/build/tarball"
    ./tarball-automake.sh
    cd ../..
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/include/hstr_curses.h
    sed -i -e "s#<ncursesw/curses.h>#<curses.h>#g" src/include/hstr.h
    ./configure --prefix=/usr
    make
}

package() {
    cd "${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}/" install
    install -D -p -m 644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -D -p -m 644 Changelog "${pkgdir}/usr/share/doc/${pkgname}/Changelog"
    install -D -p -m 644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
