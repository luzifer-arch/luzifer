# Maintainer: Knut Ahlers <knut@ahlers.me>

pkgbase=luzifer
pkgname=(
	luzifer-base
	luzifer-devel
	luzifer-gui
)
pkgver=0.5.1
pkgrel=1
pkgdesc='System configuration for @luzifer systems'
arch=(any)
url=https://github.com/luzifer-aur/luzifer
license=(Apache)
groups=(luzifer)

rootdir=${PWD}

package_luzifer-base() {
	provides=(vim vi)
	conflicts=(vim vi)
	install=luzifer-base.install

	# Build on former Archlinux base group (pacman -Qgq base | xargs | fold -sw 72)
	# Packages removed: vi
	# Packages added: base (new Base-Meta-Package, essentially containing a subset of these)
	depends=(
		base bash bzip2 coreutils cryptsetup device-mapper dhcpcd diffutils
		e2fsprogs file filesystem findutils gawk gcc-libs gettext glibc grep
		gzip inetutils iproute2 iputils jfsutils less licenses linux
		linux-firmware logrotate lvm2 man-db man-pages mdadm nano netctl pacman
		pciutils perl procps-ng psmisc reiserfsprogs s-nail sed
		shadow sysfsutils systemd-sysvcompat tar texinfo usbutils util-linux
		which xfsprogs
	)

	# Add system utils
	depends+=(
		curl
		ddrescue
		dust
		envrun
		exa
		expect
		gocryptfs
		jq
		pacman-contrib
		ripgrep
		rsync
		sudo
		tmux
		unzip
		wget
	)

	# Add debugging utils
	depends+=(
		bind-tools
		htop
		iotop
		lsof
		mtr
		nmap
		socat
	)

	# Add network utils
	depends+=(
		openssh
	)

	# Add shell
	depends+=(zsh)

	# Add editor
	depends+=(neovim python-pynvim)

	# Add script dependencies
	depends+=(
		python
		python-requests
	)

	cp -a "$rootdir/base/"* "$pkgdir"
}

package_luzifer-devel() {
	# Start with Archlinux base-devel group (pacman -Qgq base-devel | xargs | fold -sw 72)
	depends=(
		autoconf automake binutils bison fakeroot file findutils flex gawk gcc
		gettext grep groff gzip libtool m4 make pacman patch pkgconf sed sudo
		systemd texinfo util-linux which
	)

	# Apply my base package
	depends+=(luzifer-base)

	# Add dev specific tools
	depends+=(
		autopep8
		aws-cli
		docker
		git
		go
	)
}

package_luzifer-gui() {
	install=luzifer-gui.install

	depends=(luzifer-base)

	# Add fonts
	depends+=(
		adobe-base-14-fonts
		nerd-fonts-dejavu-complete
		noto-fonts-emoji
		otf-ipafont
		ttf-opensans
		ttf-roboto
		ttf-tahoma
		ttf-windows
	)

	# Add login manager
	depends+=(
		lightdm
		lightdm-gtk-greeter
	)

	# Add i3 (pacman -Qgq i3 | xargs | fold -sw 72)
	depends+=(
		i3-gaps i3blocks i3lock i3status
	)

	# Add GUI environment
	depends+=(
		dex
		dialog
		dmenu
		feh
		maim
		mupdf
		redshift
		termite
	)

	# Add Archlinux xorg group (pacman -Qgq xorg | xargs | fold -sw 72)
	depends+=(
		xf86-video-vesa xorg-bdftopcf xorg-docs xorg-font-util
		xorg-fonts-100dpi xorg-fonts-75dpi xorg-fonts-encodings xorg-iceauth
		luit xorg-mkfontscale xorg-server xorg-server-common
		xorg-server-devel xorg-server-xdmx xorg-server-xephyr xorg-server-xnest
		xorg-server-xvfb xorg-server-xwayland xorg-sessreg xorg-setxkbmap
		xorg-smproxy xorg-x11perf xorg-xauth xorg-xcmsdb xorg-xcursorgen
		xorg-xdpyinfo xorg-xdriinfo xorg-xev xorg-xgamma xorg-xhost xorg-xinput
		xorg-xkbcomp xorg-xkbevd xorg-xkbutils xorg-xkill xorg-xlsatoms
		xorg-xlsclients xorg-xmodmap xorg-xpr xorg-xprop xorg-xrandr xorg-xrdb
		xorg-xrefresh xorg-xset xorg-xsetroot xorg-xvinfo xorg-xwd
		xorg-xwininfo xorg-xwud
	)
}
