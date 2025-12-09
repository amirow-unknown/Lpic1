---
name: lpic
lesson: "8"
topic: bootloader(lilo, grub legacy, grub2)
number: "8"
---
what's the grub:
	grub(grand unified bootloader):firmware->bootloader->kernel->init
	there are some bootloaders such as lila, grub1(grub lagacy), grub(grub2)
lila and grub1(legacy)
	we ignore lilo cause it's old and even older than my father's age, but what about grub1!
	the grub lagacy is elder grub version that used less todays, it has /boot/grub/grub.conf configuration file.
	#bios and #uefi:in bios we use #MBR partition but in #uefi we have some stages to do, first some security stages and then looks to find #efi filesystem partion which is just a #fat32 partion and PE executable file to. in windows and maby other os, we have chains to load them which bootloaders like grub pass the bootloading to those chain to load windows or other os boot files.
	#difference_/etc/default/grub and #/boot/grub/: the /etc/default/grub used for user changes which has effects on main grub configs on /boot/grub/grub.
	#path_to_grub:the grub1(legacy) is mainted on /boot/grub/grub.conf for main grub1 config file and in #grub2 it's #grub.cfg 
# grub2:
#grub2 configuration file is on #/boot/grub/ and the #/grub.cfg is main configuration grub2.
- grub's configuration files are distributed in several directory and when user change them, he must run #grub-mkconfig > #/boot/grub/grub.cfg , by running this command, your modified configs gonna apply to the main #grub config file which is #grub.cfg . 
###### the source code of grub config:
```bash
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5db013b6-f967-4935-8c30-d5e5180a9590' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod fat
	set root='hd1,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  9501-7AD2
	else
	  search --no-floppy --fs-uuid --set=root 9501-7AD2
	fi
	echo	'Loading Linux linux ...'
	linux	/vmlinuz-linux root=UUID=5db013b6-f967-4935-8c30-d5e5180a9590 rw  loglevel=3 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-linux.img
}

```
#menuentry -> to define new distro with it's kernel and initramfs and other configs
#set_root -> defines where the distro gonna boot(here is at hd1,gpt1)
#linux -> defines the kernel path
#initrd -> defines the initrd path
- if you noticed, there some services and modules where defined to load before booting!
###### commands:
- #grub-install #/dev/sdx -> to install grub on /dev/sdx
- #grub-mkconfig -o #/boot/grub/grub.cfg OR #grub-mkconfig > #/boot/grub/grub.cfg -> both reads the configuration files from #/etc/default/grub and #/etc/grub.d and create the #grub.cfg based on them.
- example:
```bash
//1-> change the Default_timeout Variable in /etc/default/grub
//2-> run command grub-mkconfig -o /boot/grub/grub.cfg 
//3-> the boot menu gonna freeze and not disappear for ... seconds which you dedicated in Default_timeout variable. 
```
- how does it work for #EFI?

same like the bios commands and settings but there are some difference in grub.cfg config file:
```bash
menuentry 'Arch Linux' --class arch --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5db013b6-f967-4935-8c30-d5e5180a9590' {
	savedefault
	load_video
	set gfxpayload=keep
	insmod gzio
	insmod part_gpt
	insmod fat
	set root='hd1,gpt1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,gpt1 --hint-efi=hd1,gpt1 --hint-baremetal=ahci1,gpt1  9501-7AD2
	else
	  search --no-floppy --fs-uuid --set=root 9501-7AD2
	fi
	echo	'Loading Linux linux ...'
	linux	/vmlinuz-linux root=UUID=5db013b6-f967-4935-8c30-d5e5180a9590 rw  loglevel=3 quiet
	echo	'Loading initial ramdisk ...'
	initrd	/initramfs-linux.img
}
```
- in EFI we use settings of bios like #linux and #initrd 
in difference variable:
linux -> #linuxefi
initrd -> #initrdefi 
now save the changes and run command #grub-mkconfig.
