pkgname="xenobino-st-git"
pkgver="0.8.5"
pkgrel="2"
pkgdesc="Suckless's st terminal, patched to my liking"
arch=("x86_64")
depends=("glibc" "libx11" "libxft" "libxrender")
url="https://github.com/XenoBino/st"
license=("MIT")

prepare() {
	if [ -d xenobino-st-git ]; then rm -rf xenobino-st-git; fi
	git clone --depth 1 https://github.com/XenoBino/st xenobino-st-git
}

build() {
	pushd xenobino-st-git &> /dev/null
	make
	popd &> /dev/null
}

package() {
	# DESTDIR: Install to ${pkgdir} for packaging
	# PREFIX: Use /usr instead of /usr/local
	# TERMINFO: st's terminfo is already provided by ncurses, skip
	pushd xenobino-st-git &> /dev/null
	make DESTDIR="${pkgdir}" PREFIX="/usr" TERMINFO="$(mktemp -d)" install
	popd
}
