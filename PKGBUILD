# Maintainer: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Tofe <chris.chapuis@gmail.com>
# Contributor: zhuqin <zhuqin83@gmail.com>
# Contributor: tri1976 <trile7@gmail.com>
# Contributor: snoopy33 <snoopy33@no-log.org>

pkgname=cairo-dock-plugins-git
pkgver=3.4.0.r9.d54aa04
pkgrel=1
pkgdesc='Plugins for Cairo-Dock'
arch=('i686' 'x86_64')
url='http://glx-dock.org'
license=('GPL')
depends=('cairo-dock')
makedepends=('alsa-lib' 'cmake' 'fftw' 'git' 'gnome-menus' 'gtk-sharp-2' 'gvfs'
             'libetpan' 'libexif' 'libical' 'libpulse' 'libxklavier'
             'libzeitgeist' 'lm_sensors' 'ndesk-dbus-glib' 'python' 'python2'
             'ruby' 'vala' 'vte3' 'webkitgtk3')
optdepends=('alsa-lib: Sound Control, Sound Effects applets'
            'fftw: Impulse applet'
            'gnome-menus: Applications Menu applet'
            'gtk-sharp-2: Mono API'
            'gvfs: GVFS integration'
            'libetpan: Mail applet'
            'libexif: Slider applet'
            'libical: Clock applet'
            'libpulse: Impulse applet'
            'libxklavier: Keyboard Indicator applet'
            'libzeitgeist: Recent Events applet'
            'lm_sensors: System Monitor applet'
            'ndesk-dbus-glib: Mono API'
            'python: Python 3 API'
            'python2: Python 2 API'
            'ruby: Ruby API'
            'vte3: Terminal applet'
            'webkitgtk3: Weblets applet')
provides=('cairo-dock-plugins')
conflicts=('cairo-dock-plugins')
source=("cairo-dock-plugins::git+https://github.com/Cairo-Dock/cairo-dock-plug-ins.git")
sha256sums=('SKIP')

pkgver() {
  cd cairo-dock-plugins

  printf "%s" "$(git describe --tags | sed 's/v//; s/-/.r/; s/-g/./')"
}

build() {
  cd cairo-dock-plugins

  if [[ -d build ]]; then
    rm -rf build
  fi
  mkdir build && cd build

  cmake .. \
    -DCMAKE_BUILD_TYPE='Release' \
    -DCMAKE_INSTALL_PREFIX='/usr'
  make
}

package() {
  cd cairo-dock-plugins/build

  make DESTDIR="${pkgdir}" install
}

# vim: ts=2 sw=2 et:
