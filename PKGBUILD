pkgname='perl-xml-quote'
pkgver='1.02'
pkgrel='1'
pkgdesc="XML::Quote - XML quote/dequote functions"
arch=('any')
license=('PerlArtistic' 'GPL')
options=('!emptydirs')
depends=('perl')
makedepends=()
url='http://search.cpan.org/perldoc?XML%3A%3AQuote'
source=("http://search.cpan.org/CPAN/authors/id/G/GD/GDSL/XML-Quote-${pkgver}.tar.gz")
md5sums=('98f45c2efeeea13793949e5c74689741')

build() {
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""                 \
      PERL_AUTOINSTALL=--skipdeps                            \
      PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'"     \
      PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
      MODULEBUILDRC=/dev/null

    cd "${srcdir}/XML-Quote-$pkgver" 
    /usr/bin/perl Makefile.PL
    make
  )
}

check() {
  cd "${srcdir}/XML-Quote-$pkgver"
  ( export PERL_MM_USE_DEFAULT=1 PERL5LIB=""
    make test
  )
}

package() {
  cd "${srcdir}/XML-Quote-$pkgver"
  make install
  find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
