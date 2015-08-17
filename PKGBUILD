# Maintainer: Niels Abspoel <aboe76 (at) Gmail (dot) com>
pkgname=ruby-cfacter
_gemname=cfacter
pkgver=0.2.0
pkgrel=4
pkgdesc="Ruby module for collecting simple facts about a host operating system"
arch=(any)
url='http://puppetlabs.com/puppet/related-projects/cfacter'
license=('APACHE')
depends=('ruby' 'boost' 'yaml-cpp' 'gcc' 'openssl' 'libutil-linux' 'cfacter' 'ruby-ffi')
builddepends=('gcc' 'cmake' 'ruby-bundler')
source=('https://github.com/puppetlabs/cfacter/archive/0.2.0.tar.gz'
        '.AURINFO')
build() {
  cd "${srcdir}/${_gemname}-${pkgver}"
  cd gem
  bundle install
  rake gem
}
package() {
  cd "${srcdir}/${_gemname}-${pkgver}/gem/pkg"
  local _gemdir="$(ruby -e'puts Gem.default_dir')"
  gem install --ignore-dependencies --no-user-install -i "$pkgdir/$_gemdir" -n "$pkgdir/usr/bin" $_gemname-$pkgver.gem
  rm "$pkgdir/$_gemdir/cache/$_gemname-$pkgver.gem"
}
sha256sums=('126fcb8151522fd6cfb7a070f86f0a0f2c9aea56328b79ed961fa912258fc857' SKIP)
