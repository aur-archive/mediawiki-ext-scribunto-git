# Maintainer: Felix E. xelif@icqmail.com

# Upstream name of extension:
_extname=Scribunto
# Variant valid as package name:
_extpkgname=scribunto

pkgname=mediawiki-ext-$_extpkgname-git
pkgver=r688.93579c7
pkgrel=2
pkgdesc="A MediaWiki extension to support script enabled content (e.g. lua)."
source=("git+https://gerrit.wikimedia.org/r/mediawiki/extensions/$_extname")
md5sums=("SKIP")
arch=("i686" "x86_64")
url="http://www.mediawiki.org/wiki/Extension:$_extname"
license=("GPL")
depends=("mediawiki")
optdepends=("lib32-glibc: When using the 32-bit version of included lua binaries"
            "mediawiki-ext-codeeditor-git: Code editor with scribunto support (diabled by default)")
makedepends=("git")
provides=("mediawiki-ext-$_extpkgname")
conflicts=()

pkgver() {
  cd $_extname
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
  # Target extension directory of MediaWiki:
  _extdir="$pkgdir/usr/share/webapps/mediawiki/extensions"
  mkdir -p "$_extdir"
  rsync -a $_extname "$_extdir/" --exclude .git
}