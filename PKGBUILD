# Maintainer: Denis Dzenskevich <denis.dzenskevich at gmail.com>
# Contributor: scheffold <fscheffold (at) gmail.com>
# Contributor: Urs Wolfer <uwolfer @ fwo.ch>

pkgname=intellij_idea_ce_12_eap
pkgver=129.1359
pkgrel=1
install=intellijidea.install
pkgdesc="Early access version of the upcoming Intellij Idea 12 Java IDE (community version)"
arch=('i686' 'x86_64')
url="http://confluence.jetbrains.net/display/IDEADEV/IDEA+12+EAP"
backup=(
    "usr/share/${pkgname}/bin/idea.vmoptions" 
    "usr/share/${pkgname}/bin/idea64.vmoptions" 
    "usr/share/${pkgname}/bin/idea.properties")
license=('apache')
depends=('java-environment')
options=('!strip')

source=(
    idea.vmoptions        intellijidea.sh intellijidea.desktop intellijidea.install \
    "http://download.jetbrains.com/idea/ideaIC-12.1.6.tar.gz")
    #"http://download.jetbrains.com/idea/ideaIC-${pkgver}.tar.gz")

build() {
  cd "$srcdir"

  if [ "$CARCH" = "i686" ]; then
    _rmpostfix="64"
    _retainpostfix=""
  elif [ "$CARCH" = "x86_64" ]; then
    _rmpostfix=""
    _retainpostfix="64"
  fi

  install -d -m755 $pkgdir/usr/{bin,share}
  cp -a "idea-IC-$pkgver" "$pkgdir/usr/share/$pkgname"
  sed -i 's|\.IntelliJIdea\/|\.IntelliJIdea12\/|' "$pkgdir/usr/share/$pkgname/bin/idea.properties"

  cp "$srcdir"/idea.vmoptions "$pkgdir"/usr/share/$pkgname/bin

  chmod +x $pkgdir/usr/share/$pkgname/bin/idea.sh
  chmod +x "$pkgdir"/usr/share/$pkgname/bin/fsnotifier$_retainpostfix

  rm $pkgdir/usr/share/intellij_idea_ce_12_eap/bin/fsnotifier$_rmpostfix
  rm $pkgdir/usr/share/intellij_idea_ce_12_eap/bin/libbreakgen$_rmpostfix.so
  #rm $pkgdir/usr/share/intellij_idea_ce_12_eap/bin/libyjpagent-linux$_rmpostfix.so

  install -D -m755 $srcdir/intellijidea.sh $pkgdir/usr/bin/$pkgname
  install -D -m644 $srcdir/intellijidea.desktop $pkgdir/usr/share/applications/$pkgname.desktop
  install -D -m644 $srcdir/idea-IC-$pkgver/bin/idea.png $pkgdir/usr/share/pixmaps/$pkgname.png
  #install -D -m644 $srcdir/idea-IC-$pkgver/license/IDEA_license.txt $pkgdir/usr/share/licenses/$pkgname/LICENSE.txt
}

md5sums=('c51777b27eed5cca4d0406b3cf060406'
         '9a93f6ee32b50f3a63bc322e4089a817'
         '013381d59cda2f14cf410a521f74699a'
         '48130e94e6b816978f90b6f05b788ffc'
         '5731ad2d6113ea7e8aedffc011480cb8')
