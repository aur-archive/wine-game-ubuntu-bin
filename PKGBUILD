# Maintainer: Christoph Haag <haagch@studi.informatik.uni-stuttgart.de>
pkgname=wine-game-ubuntu-bin
pkgver=1.7.15
_pkgrel=1
pkgrel=$_pkgrel
pkgdesc="This archive contains builds of wine that have been patched to make various games work better. Includes patches for CSMT, guild wars"
arch=("i686" "x86_64")
url="https://launchpad.net/~foresto/+archive/ubuntu/winepatched/+packages?field.name_filter=&field.status_filter=published&field.series_filter=trusty"
license=('GPL')
depends=("lib32-gstreamer0.10-base" "lib32-fontconfig" "lib32-libxcursor" "lib32-libxrandr" "lib32-libxdamage" "lib32-libxi" "lib32-gettext" "lib32-freetype2" "lib32-glu" "lib32-libsm" "lib32-gcc-libs")
[ "$CARCH" = 'i686' ] && depends=("gstreamer0.10-base" "fontconfig" "libxcursor" "libxrandr" "libxdamage" "libxi" "gettext" "freetype2" "glu" "libsm" "gcc-libs")
optdepends=()
conflicts=()
replaces=()
backup=()
options=()
install="wine-game.install"
changelog=

_name="wine-game-${pkgver}.deb"
_name2="wine-game-${pkgver}2.deb"
                #https://launchpad.net/~foresto/+archive/ubuntu/winepatched/+files/wine1.7-i386_1.7.15%2Bguildwarsii1_i386.deb
                #https://launchpad.net/~foresto/+archive/ubuntu/winepatched/+files/wine1.7_1.7.15%2Bguildwarsii1_i386.deb
source=("$_name::https://launchpad.net/~foresto/+archive/ubuntu/winepatched/+files/wine1.7-i386_${pkgver}%2Bguildwarsii1_i386.deb"
        "$_name2::https://launchpad.net/~foresto/+archive/ubuntu/winepatched/+files/wine1.7_${pkgver}%2Bguildwarsii1_i386.deb"
        "wine-game"
        "wine-game.conf"
        "csmt.reg")
noextract=("$_name2") # because fuck you, that's why

#prepare() {
#}

build() {
        cd "$srcdir/"
        install -d wine1
        bsdtar -xf data.tar.gz -C "$srcdir/wine1/"

        install -d "wine2"
        ar x "$_name2"
        bsdtar -xf data.tar.gz -C "$srcdir/wine2/"
}

#check() {
#	cd "$srcdir/$pkgname-$pkgver"
#	make -k check
#}

package() {
        install -d "$pkgdir/opt/"
        mv "$srcdir/wine1/usr/" "$pkgdir/opt/wine-game"
        cp -ra "$srcdir/wine2/usr/"* "$pkgdir/opt/wine-game"
        install -d "$pkgdir/usr/bin"
        install -m 755 "$srcdir/wine-game" "$pkgdir/usr/bin/"
        install -d "$pkgdir/etc"
        install "$srcdir/wine-game.conf" "$pkgdir/etc"
        install -d "$pkgdir/usr/share/wine-game/"
        install "$srcdir/csmt.reg" "$pkgdir/usr/share/wine-game/"
}
#pkgver() {
#        #TODO
#}

md5sums=('14e7cb91b99cb9e69a762fef673ede20'
         'a5ea8b99a499590d5a4bbf55953d97cf'
         '66964f8b047272424d646f7e7a4941be'
         '34aa093b104c4c5a0f489df480712b2d'
         '9de4ddf38376ed8b24b679cbc7eefd74')
