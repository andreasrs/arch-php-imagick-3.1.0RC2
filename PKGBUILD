# Maintainer: Andreas Rudi Søvik <arsovik@gmail.com>
# Contributor: Evangelos Foutras <foutrelis@gmail.com>

pkgname=php-imagick
pkgver=3.1.0RC2
pkgrel=4
pkgdesc="PHP extension for IMagick"
arch=('i686' 'x86_64')
url="http://pecl.php.net/package/imagick"
license=('PHP')
depends=('php>=5.1.3' 'imagemagick>=6.2.4')
backup=('etc/php/conf.d/imagick.ini')
install=php-imagick.install
source=("http://pecl.php.net/get/imagick-$pkgver.tgz"
"header-location.patch")

build() {
    cd "$srcdir/imagick-$pkgver"

    # patch for imagemagick-6.8.3 header location
    patch -p1 -i "$srcdir/header-location.patch"

    phpize || return 1
    ./configure --prefix=/usr

    make || return 1
    make INSTALL_ROOT="$pkgdir" install
    echo ';extension=imagick.so' > imagick.ini
    install -D -m644 imagick.ini "$pkgdir/etc/php/conf.d/imagick.ini"
}

md5sums=('de9cca809fb2db61f4cbd9fac4f69314'
'ef34a4a603866a9bd63ad5cc0976bdf9')

