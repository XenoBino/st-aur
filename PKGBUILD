pkgname="xenobino-st-git"
pkgver="0.8.5"
pkgrel="1"
pkgdesc="Suckless's st terminal, patched to my liking"
arch=("x86_64")
depends=("glibc" "libx11" "libxft" "libxrender")
url="https://github.com/XenoBino/st"
license=("MIT")

prepare() {
	if [ -d st ]; then rm -rf st; fi
	git clone --depth 1 https://github.com/XenoBino/st
}

build() {
	pushd st &> /dev/null
	make
	popd &> /dev/null
}

package() {
	strip "${srcdir}/st/st"
	mkdir -p "${pkgdir}/usr/bin"
	mkdir -p "${pkgdir}/usr/share/applications"
	mkdir -p "${pkgdir}/usr/share/man/man1"
	cp "${srcdir}/st/st" "${pkgdir}/usr/bin/st"
	cp "${srcdir}/st/st.1"  "${pkgdir}/usr/share/man/man1/st.1"
	cp "${srcdir}/st/st.desktop" "${pkgdir}/usr/share/applications/st.desktop"
	chmod +x "${pkgdir}/usr/bin/st"
}
