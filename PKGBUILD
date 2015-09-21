# Maintainer: Wayne Hartmann (DH4) <wayne@bitstorm.pw>

pkgname=protocase-designer
pkgver=4.4.8
pkgrel=1

pkgdesc="The fastest and easiest way to design, price, and build custom electronics enclosures."
arch=('i686' 'x86_64')
url="http://www.protocasedesigner.com/"
depends=('java-runtime-common' 'jre7-openjdk')
#install=protocase-designer.install
license=('custom')
source=(http://www.protocasedesigner.com/RELEASE/protocaseDesigner-linux-i586-4.4.8.tar.gz
	ProtocaseDesigner.desktop)
md5sums=('5f313ca4e923136f75a6b4cb0deba678'
	 'f66d02094444eac61f468371589fcc9c')
         
[ "$CARCH" = "x86_64" ] && source=(http://www.protocasedesigner.com/RELEASE/protocaseDesigner-linux-amd64-4.4.8.tar.gz
				   ProtocaseDesigner.desktop)
[ "$CARCH" = "x86_64" ] && md5sums=('488d5ef878132acbabba6e9fc77c72bc'
				    'f66d02094444eac61f468371589fcc9c')

package() {
	
	install -d $pkgdir/usr/local/lib/
	cp -R $srcdir/jdesigner/Protocase\ Designer $pkgdir/usr/local/lib
	install -d $pkgdir/usr/local/share/Protocase\ Designer/
	cp -R $srcdir/jdesigner/library  $pkgdir/usr/local/share/Protocase\ Designer/
	install -d $pkgdir/usr/local/share/pixmaps/
	cp $srcdir/jdesigner/Protocase\ Designer.ico $pkgdir/usr/local/share/pixmaps/ProtocaseDesigner.ico

	install -d $pkgdir/usr/local/bin/
	echo '#/bin/sh' > $pkgdir/usr/local/bin/ProtocaseDesigner
	echo "install -d  ~/ProtocaseDesigner/" >> $pkgdir/usr/local/bin/ProtocaseDesigner
	echo "mkdir ~/ProtocaseDesigner/UserLibrary" >> $pkgdir/usr/local/bin/ProtocaseDesigner
	echo "LD_LIBRARY_PATH=/usr/local/lib/Protocase\ Designer/:/usr/local/lib/Protocase\ Designer/lib/:\ $LD_LIBRARY_PATH java -jar /usr/local/lib/Protocase\ Designer/jdesigner.jar >> ~/ProtocaseDesigner/error.log 2>&1" >> $pkgdir/usr/local/bin/ProtocaseDesigner
	chmod 755 $pkgdir/usr/local/bin/ProtocaseDesigner

	install -d $pkgdir/usr/local/share/applications/
	cp $srcdir/ProtocaseDesigner.desktop $pkgdir/usr/local/share/applications/ProtocaseDesigner.desktop
}
