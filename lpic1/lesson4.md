---
name: lpic
lesson: "4"
topic: boot system
number: "4"
---
## boot process
1.  the firmware at first step does a poweronselftest(post) to recognize all hardware are working correctly and with no conflict or error.
2. then the firmware load the bootloader that can be grub, bootloader use minimal hardware.
3. then the bootloader loads the os(you can configure to load other service but it's not usuall and standard cause you need os at first) that means it's linux kernel in linux in memory and run it(bootloader loads it by it's config files).
4. the linux kernel have init files that load the services, applications and .... .
5. but the kernel it's also need to have some necessary driver to interact with hardware, those driver are stored in #initramfs or #initrd in /boot directory.
# initramfs or initrd
these image is a temporary filesystem image that helps to the kernel to mount the /root directory and it's components. it's format is something like **initramfs-linux-fallback.img** and **initramfs-linux.img**. actually it's bootable file that kernel loads it first and then boot the main /root directory cause the initramfs or initrd is more lightweight than main directory.

## conclution
firmware loads kernel and then initramfs or initrd(initramfs is filesystem image -> tiny os) until the kernel find the main bootable directory to loads instead of initramfs or initrd.
firmware -> kernel+initramfs/initrd -> inits(kernel pass the duties to inits) -> /
