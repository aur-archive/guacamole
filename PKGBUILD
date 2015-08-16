# Maintainer: Joshua Stiefer <facedelajunk@gmail.com>
pkgname=guacamole
pkgver=0.8.0
pkgrel=1
pkgdesc="An HTML5 web application that provides access to your desktop using remote desktop protocols."
arch=('any')
url="http://guacamole.sourceforge.net/"
license=('GPL3')
depends=('guacd' 'java-environment' 'tomcat6')
makedepends=('maven')
optdepends=()
provides=()
install=$pkgname.install
source=(http://sourceforge.net/projects/guacamole/files/current/source/$pkgname-$pkgver.tar.gz
        $pkgname.install)
md5sums=('ce04e26f2b379d365e9abce4a9d7851c'
         '3fe7d844e2461aeb0147d9787d48d5f5')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  /opt/maven/bin/mvn package
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  install -Dm600 $srcdir/$pkgname-$pkgver/target/guacamole-$pkgver.war $pkgdir/var/lib/guacamole/guacamole.war
  install -Dm755 $srcdir/$pkgname-$pkgver/doc/example/guacamole.properties $pkgdir/etc/guacamole/guacamole.properties
  install -Dm755 $srcdir/$pkgname-$pkgver/doc/example/user-mapping.xml $pkgdir/etc/guacamole/user-mapping.xml
  sed -i 's#path/to#etc/guacamole#' $pkgdir/etc/guacamole/guacamole.properties
}

# vim:set ts=2 sw=2 et:
