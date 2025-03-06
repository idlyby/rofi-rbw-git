# Maintainer: Joshua Schmeder <joshua@schmeder.dev>

_pkgname='rofi-rbw'
pkgname="${_pkgname}-git"
pkgver=968a4e2
pkgrel=1
pkgdesc='Rofi frontend for Bitwarden'
arch=('x86_64')
url='https://github.com/idlyby/rofi-rbw'
license=('MIT')
makedepends=('git' 'python-pip')
depends=('rbw' 'python' 'python-configargparse')
optdepends=('rofi: rofi frontend' 
            'wofi: wofi frontend'
            'fuzzel: fuzzel frontend'
            'libnotify: for totp copy notifications'
            'xdotool: for autofill on X11'
            'wtype: for autofill on Wayland'
            'ydotool: for autofill on Wayland'
            'dotool: for autofill on X11 and Wayland'
            'xclip: for copying passwords to clipboard on X11'
            'xsel: for copying passwords to clipboard on X11'
            'wl-clipboard: for copying passwords to clipboard on Wayland')
provides=("${_pkgname}")
conflicts=("${_pkgname}")
source=("git+${url}.git#branch=fuzzel")
sha256sums=('SKIP')
install="${pkgname}.install"

pkgver() {
  git -C "${srcdir}/${_pkgname}" describe --long --tags --always | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

package() {
  cd "$_pkgname"
  pip install --isolated --no-deps --ignore-installed --root="${pkgdir}" .
  install -Dvm644 'README.md' -t "${pkgdir}/usr/share/doc/${_pkgname}"
  install -Dvm644 'LICENSE' -t "${pkgdir}/usr/share/licenses/${_pkgname}"
  install -Dvm644 "docs/${_pkgname}.1" -t "${pkgdir}/usr/share/man/man1"
}
