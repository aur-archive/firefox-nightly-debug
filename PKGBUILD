# Maintainer: Cedric MATHIEU <me.xenom @ gmail.com>
# Contributor : Det <nimetonmaili @ gmail.com>
# Contributor: coderoar <coderoar @ gmail.com>

pkgname=firefox-nightly-debug
pkgdesc='Standalone web browser from mozilla.org, nightly debug build'
url='http://www.mozilla.org/projects/firefox'
pkgver=21.0a1
pkgrel=1
arch=('i686' 'x86_64')
license=('MPL' 'GPL' 'LGPL')
source=('firefox-nightly-debug.desktop' 'firefox-nightly-debug-safe.desktop')
sha1sums=('2a2e1e72bfe709e4ec9b81c136fbb74d673e8180'
          '486beed9fe27bf233229a114848b5927154bc839')
depends=('alsa-lib' 'libxt' 'libnotify' 'mime-types' 'nss' 'gtk2' 'sqlite' 'dbus-glib')

package() {
  FX_SRC="firefox-${pkgver}.en-US.debug-linux-${CARCH}.tar.bz2"
  FX_SRC_URI="http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/`TZ='America/Los_Angeles' date +%Y-%m-%d`-mozilla-central-debug/${FX_SRC}"

  msg "Downloading..."
  curl -OR ${FX_SRC_URI}
  msg "Extracting..."
  bsdtar -x -f ${FX_SRC}
  msg "Packaging..."

#   uncomment this line to remove these
#   rm -rf firefox/{extensions,plugins,searchplugins}

  mkdir -p "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
  cp -r firefox "${pkgdir}/opt/${pkgname}"

  ln -s /opt/${pkgname}/firefox "${pkgdir}/usr/bin/firefox-nightly-debug"
  install -m644 "${srcdir}"/{firefox-nightly-debug.desktop,firefox-nightly-debug-safe.desktop} "${pkgdir}/usr/share/applications/"
  install -m644 "${srcdir}/firefox/icons/mozicon128.png" "${pkgdir}/usr/share/pixmaps/${pkgname}-icon.png"
}
