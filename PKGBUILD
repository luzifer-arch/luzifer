# Maintainer: Knut Ahlers <knut@ahlers.me>

pkgbase=luzifer
pkgname=(
  luzifer-base
  luzifer-devel
  luzifer-gui
  luzifer-lenovo-gui
)
pkgver=0.6.3
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

  # Build on former base package
  depends=(
    base
  )

  # Add basic system packages (formerly in "base" group)
  depends+=(
    cryptsetup
    e2fsprogs
    less
    linux
    linux-firmware
    logrotate
    lvm2
    man-db
    man-pages
    mdadm
    netctl
    usbutils
    util-linux
    which
    xfsprogs
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
    peco
    ripgrep
    rsync
    sudo
    tmux
    unzip
    vault-bin
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
  # Start with Archlinux base-devel group (pacman -Sg base-devel | cut -d ' ' -f 2 | xargs | fold -sw 72)
  depends=(
    autoconf automake binutils bison fakeroot file findutils flex gawk gcc
    gettext grep groff gzip libtool m4 make pacman patch pkgconf sed sudo
    texinfo which
  )

  # Apply my base package
  depends+=(luzifer-base)

  # Add dev specific tools
  depends+=(
    autopep8
    aws-cli
    diffutils
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

  # Add packages of the xorg group (pacman -Sg xorg | cut -d ' ' -f 2 | xargs | fold -sw 72)
  depends+=(
    xf86-video-vesa xorg-bdftopcf xorg-docs xorg-font-util
    xorg-fonts-100dpi xorg-fonts-75dpi xorg-fonts-encodings xorg-iceauth
    xorg-mkfontscale xorg-server xorg-server-common xorg-server-devel
    xorg-server-xephyr xorg-server-xnest xorg-server-xvfb xorg-sessreg
    xorg-setxkbmap xorg-smproxy xorg-x11perf xorg-xauth xorg-xbacklight
    xorg-xcmsdb xorg-xcursorgen xorg-xdpyinfo xorg-xdriinfo xorg-xev
    xorg-xgamma xorg-xhost xorg-xinput xorg-xkbcomp xorg-xkbevd
    xorg-xkbutils xorg-xkill xorg-xlsatoms xorg-xlsclients xorg-xmodmap
    xorg-xpr xorg-xprop xorg-xrandr xorg-xrdb xorg-xrefresh xorg-xset
    xorg-xsetroot xorg-xvinfo xorg-xwayland xorg-xwd xorg-xwininfo xorg-xwud
  )

  # Add i3 (pacman -Sg i3 | cut -d ' ' -f 2 | xargs | fold -sw 72)
  depends+=(
    i3-gaps i3-wm i3blocks i3lock i3status
  )

  # Add GUI environment
  depends+=(
    alacritty
    chromium
    dex
    dialog
    dmenu
    feh
    maim
    mupdf
    redshift
    xbindkeys
    xclip
  )

  # Add sound
  depends+=(
    alsa-utils
    pulseaudio
    pulsemixer
  )
}

package_luzifer-lenovo-gui() {
  # This extends the normal GUI package for Thinkpads
  depends=(luzifer-gui)

  depends+=(
    acpi            # Required for lid-close events
    xorg-xbacklight # Control display brightness
  )
}
