
# Maintainer: Johan Noren <johnor@tuta.io>

pkgname=custom_patches
pkgver=20190224
pkgrel=2
pkgdesc="Contains various customizations, tools and fixes that i like/need."
arch=('x86_64')
license=('GPL')

source=('systemd-fsck@.service'
	'systemd-fsck-root.service'
	'disable_gpe4E.service'
	'randomize_hostname.service'
	'40-disable_wakeup_xhc1.rules'
	'hostname_wordlist'
	'start_powertop.service'
	'10-quiet_kernel_during_boot.conf'
	'dont_clear_console.conf'
	'50-allow_user_to_change_backlight.rules'
	'51-allow_user_to_change_kbd_led.rules'
	'10-spoof-wlp3s0.link'
	'15-wireless.network'
	'tty-no-cursor-blink.conf'
)


package() {

	cd "${srcdir}/"

	# Wordlist for randomizer
	install -Dm0644 hostname_wordlist "${pkgdir}/usr/share/custom_patches/hostname_wordlist"

	# Installs all services
	for xservice in *.service; do
		install -Dm0644 $xservice "${pkgdir}/etc/systemd/system/${xservice}"
	done

    	# Install prehibitor for clearing screen at login
	install -Dm644 dont_clear_console.conf "${pkgdir}/etc/systemd/system/getty@tty1.service.d/dont_clear_console.conf"
	install -Dm644 tty-no-cursor-blink.conf "${pkgdir}/etc/tmpfiles.d/tty-no-cursor-blink.conf"
	install -Dm644 10-quiet_kernel_during_boot.conf "${pkgdir}/etc/sysctl.d/10-quiet_kernel_during_boot.conf"
	# udev-rules
	install -Dm644 40-disable_wakeup_xhc1.rules "${pkgdir}/etc/udev/rules.d/40-disable_wakeup_xhc1.rules"
	install -Dm644 50-allow_user_to_change_backlight.rules "${pkgdir}/etc/udev/rules.d/50-allow_user_to_change_backlight.rules"
	install -Dm644 51-allow_user_to_change_kbd_led.rules "${pkgdir}/etc/udev/rules.d/51-allow_user_to_change_kbd_led.rules"

	# network-config
	install -Dm644 10-spoof-wlp3s0.link "${pkgdir}/etc/systemd/network/10-spoof-wlp3s0.link"
	install -Dm644 15-wireless.network "${pkgdir}/etc/systemd/network/15-wireless.network"




}
md5sums=('ca9fa912645f1e1766859c30e5d71327'
         '8d959fd166b3e867a577ba2c8cd577f1'
         '6f7b5c70cb1f39a1d86e373b701861df'
         '891483dfb18cef843ef844f5a22fc5ae'
         'b3daabd268b835361b5debaf13ed5364'
         '1bb1bc53d0e60c1b6b67aaaae966940f'
         '066937cc31232e7ac80c77d861aad35a'
         'b5720a3cbd6c7c7a47ef6d427ca005a1'
         '6878b910d1d59db21df60b1a8ba3a919'
         '4126ab2cf02f8cff812d97d56b9d8338'
         '1dd0a82f5215f48c2f52a1cb44632c40'
         '1e4a2743ebbafd4c4af41df59a7bc804'
         '1492da8419f62d28d9f7be1fdbc0cfd1'
         '6bb7cf53197c8ce88e84a368cab23d6a')
