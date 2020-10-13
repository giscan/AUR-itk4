# Maintainer: Samuel Mesa <samuelmesa@gmail.com>
# Contributor: Chris <christopher.r.mullins g-mail>
# Contributor: Andrzej Giniewicz <gginiu@gmail.com>
# Contributor: Thomas Dziedzic < gostrc at gmail >
# Contributor: joel schaerer <joel.schaerer@laposte.net>
# Contributor: Sylvain Poulain <sylvain.poulain@giscan.com>

pkgname=itk4
pkgver=4.13.3
pkgrel=1
pkgdesc='Cross-platform system that provides developers with an extensive suite of software tools for image analysis'
arch=('i686' 'x86_64')
url='http://www.itk.org/'
license=('APACHE')
depends=('fftw' 'libjpeg-turbo' 'libpng' 'zlib' 'libtiff' 'gdcm' 'expat' 'hdf5-cpp-fortran' 'gtest')
optdepends=('python2: build python wrapping'
            'ruby'
            'tcl: build tcl wrapping (currently not supported)'
            'perl: build perl wrapping (currently not supported)'
            'java-runtime: build java wrapping (currently not supported)'
            'swig: generate python wrappers'
            'pcre: for wrapping'
            'castxml-git: for wrapping and docs'
            'clang: for swig'
	    'castxml-git: for ITK')
makedepends=('cmake')
conflicts=('insight-toolkit')
provides=('insight-toolkit')
replaces=('insight-toolkit')

source=(https://github.com/InsightSoftwareConsortium/ITK/releases/download/v4.13.3/InsightToolkit-${pkgver}.tar.gz)
sha512sums=(    'bc08bef804a4384ddf8694658bef34d30e54fa1ef5f72e460357382316dd45fed4088eb529014692cc28ffbd017782c9bcb276c8c8f4debe13af8eea93eaf5c0')

_usepython=false


build() {
  cd "$srcdir"
  rm -rf build
  mkdir -p build
  cd build

  cmake \
    -DCMAKE_INSTALL_PREFIX:FILEPATH=/usr \
    -DITK_USE_SYSTEM_HDF5:BOOL=ON \
    -DBUILD_PKGCONFIG_FILES:BOOL=OFF \
    ../InsightToolkit-${pkgver}

  make
}

package() {
  cd "$srcdir"/build

  make DESTDIR="${pkgdir}" install
}
