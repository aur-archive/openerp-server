# Maintainer: Dan Serban
# Contributors: Mark Doe, L42y

pkgname=openerp-server
pkgver=6.0.3
pkgrel=1
pkgdesc="Advanced OpenSource ERP and CRM server"
url=http://openerp.com/
arch=(i686 x86_64)
license=(GPLv3)
depends=('postgresql' 'python-egenix-mx-base' 'python-lxml' 'python-pychart' 'python-pytz' 'python-reportlab' 'python2' 'python2-psycopg2' 'python2-yaml' 'python2-mako' 'python2-dateutil' 'pydot' 'python2-vobject' 'python-imaging' 'python2-distribute')
source=(
"http://www.openerp.com/download/stable/source/openerp-server-${pkgver}.tar.gz"
openerp-server.rc
openerp-server.confd
)
install=openerp-server.install

build()
{
  cd ${srcdir}/${pkgname}-${pkgver}
  mkdir ${pkgdir}/etc/{rc.d,conf.d,openerp,logrotate.d} -p
  install -Dm 755 ${srcdir}/openerp-server.rc ${pkgdir}/etc/rc.d/openerp-server
  install -Dm 644 ${srcdir}/openerp-server.confd ${pkgdir}/etc/conf.d/openerp-server

  python2 setup.py install --root="${pkgdir}"
  cp ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}/openerp-server.conf ${pkgdir}/etc/openerp/
  install -Dm 644 ${pkgdir}/usr/share/doc/${pkgname}-${pkgver}/openerp-server.logrotate ${pkgdir}/etc/logrotate.d/
  mv ${pkgdir}/usr/share/doc/${pkgname}-${pkgver} ${pkgdir}/usr/share/doc/${pkgname}
  cd "${pkgdir}"/usr/bin
  sed -i 's/cd .*pkg/cd /' openerp-server
}

md5sums=('33b165b124efb15ba9285cea8d7767f5'
         'e7dc5e9b048ea206b02634587a9a7e45'
         'f88d49de3dae4bbe4f0a41ebb53e52ff')
