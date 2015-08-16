# Maintainer: Padfoot

pkgname=lightdm-gtk-greeter-osk-no-gnome
srcname=lightdm-gtk-greeter
pkgver=1.1.5
pkgrel=1
pkgdesc="GTK+ greeter for LightDM with on-screen keyboard support and no gnome dependencies"
arch=('i686' 'x86_64')
license=('GPL3' 'LGPL3')

url="https://launchpad.net/lightdm-gtk-greeter"
source=("https://launchpad.net/$srcname/trunk/$pkgver/+download/$srcname-$pkgver.tar.gz"
lightdm-gtk-greeter.conf
lightdm-gtk-greeter.patch)
depends=('lightdm=>1.2.0' 'gtk3')
makedepends=('gtk-doc' 'gnome-common' 'gnome-doc-utils' 'gobject-introspection' 'pkg-config' 'intltool' 'patch')
optdepends=('xorg-xserver-xephr: run lightdm in test mode')
install=lightdm-gtk-greeter.install

conflicts=('lightdm-gtk-greeter')
provides=('lightdm-gtk-greeter')

backup=('etc/lightdm/lightdm-gtk-greeter.conf')

build() {
  cd "$srcdir/$srcname-$pkgver"

  patch -p1 -i $srcdir/lightdm-gtk-greeter.patch
  
  ./autogen.sh --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib/lightdm \
    --disable-static
    
  make
}

package() {
  cd "$srcdir/$srcname-$pkgver"
  
  make DESTDIR="${pkgdir}" install
  
  cp ../lightdm-gtk-greeter.conf $pkgdir/etc/lightdm
}

md5sums=('e42cedadbebd5b45733b32db54b83a44'
         '17c8f6ae0ff350fca16b9162e9735182'
         '283d9496d405cc19721ab6f6746a9aac')
