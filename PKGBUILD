 
# Contributor: giacomogiorgianni@gmail.com
# Contributor: ming13@yandex.ru

pkgname=mysql-workbench-gpl
_name=mysql-workbench-community
pkgver=6.3.3
pkgrel=1
pkgdesc="A cross-platform, visual database design tool developed by MySQL (Ubuntu precompiled binary)."
arch=('i686' 'x86_64')
url="https://www.mysql.com/products/workbench/"
license=('GPL2')
depends=('hicolor-icon-theme' 'tinyxml' 'pcre>=8' 'libzip' 'lua51' 'netcdf' 'gtkmm' 'ctemplate' 'libgl' 'python2-pexpect' 'python2-paramiko' 'libgnome-keyring' 'libmariadbclient' 'python2-crypto' 'libpng12' 'libjpeg6-turbo')
optdepends=('mysql-utilities')
conflicts=('mysql-workbench' 'python26')
install=${pkgname}.install

if [ "${CARCH}" = 'x86_64' ]; then
  ARCH='amd64'
  md5sums=('888aae4f9b705cd58a437ba9be74194f' '74df3a6c69519a3fa7458b0e0366f70a' '7600292884e1c180c03989a0aedea413')

elif [ "${CARCH}" = 'i686' ]; then
  ARCH='i386'
  md5sums=('3e9d9370cc42aa59771846a42b6a9cf1' '34a3d74976ffa18ef22a29dec5dd5ba3' '7600292884e1c180c03989a0aedea413')
fi

#source=(http://download.softagency.net/mysql/Downloads/MySQLGUITools/${_name}-${pkgver}-1ubu1204-${ARCH}.deb)
source=(http://www.mirrorservice.org/sites/ftp.mysql.com/Downloads/MySQLGUITools/${_name}-${pkgver}-1ubu1404-${ARCH}.deb 
	http://ftp.us.debian.org/debian/pool/main/libh/libhdf4/libhdf4-0-alt_4.2.10-3_${ARCH}.deb $pkgname.install)
package() {
  ar -x "${srcdir}/${_name}-${pkgver}-1ubu1404-${ARCH}.deb"
  tar -xf "${srcdir}/data.tar.xz"
  cp -r "${srcdir}/usr/" "${pkgdir}"
  
  rm -rf "${srcdir}/usr"
  rm -f "${srcdir}/data.tar.xz" && rm -f "${srcdir}/control.tar.gz" && rm -f "${srcdir}/debian-binary"
  
  ar -x "${srcdir}/libhdf4-0-alt_4.2.10-3_${ARCH}.deb"
  tar -xf "${srcdir}/data.tar.xz"
  cp -r "${srcdir}/usr/lib/" "${pkgdir}/usr"
  # the /usr/bin fix, see
  # https://www.archlinux.org/news/binaries-move-to-usrbin-requiring-update-intervention/
  rm -rf "${pkgdir}"/sbin
 
  #ln -s "/usr/lib/libmfhdfalt.so" "${pkgdir}/usr/lib/libmfhdfalt.so.0"
  ln -s "/usr/lib/libnetcdf.so" "${pkgdir}/usr/lib/libnetcdf.so.6"
  ln -s "/usr/lib/liblua.so.5.1" "${pkgdir}/usr/lib/liblua5.1.so.0"
  ln -s "/usr/lib/libpython2.7.so.1.0" "${pkgdir}/usr/lib/libpython2.6.so.1.0"
  ln -s "/usr/lib/libzip.so.2" "${pkgdir}/usr/lib/libzip.so.1"
  ln -s "/usr/lib/libmysqlclient_r.so.18" "${pkgdir}/usr/lib/libmysqlclient_r.so.16"
  ln -s "/usr/lib/libpcre.so.1" "${pkgdir}/usr/lib/libpcre.so.3"
  ln -s "/usr/lib/libctemplate.so.3" "${pkgdir}/usr/lib/libctemplate.so.2"
  ln -s "/usr/lib/libtinyxml.so.0.2.6.2" "${pkgdir}/usr/lib/libtinyxml.so.2.6.2"
  #ln -s "/usr/lib/ctemplate.so" "${pkgdir}/usr/lib/ctemplate.so.0"
  rm -rf "${pkgdir}/usr/sbin"
}
