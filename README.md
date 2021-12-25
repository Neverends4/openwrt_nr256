# openwrt_nr256
Adding dts and necessary files to support **Netcore NR256** router in openwrt

For personal record usage. If you bumped into this repo and want to use the patch, some hints below:

1. This patch only applies to **Netcore NR256**, an outdated wired-ONLY router with RT3052F CPU, 8M NOR ROM and 64M SDR RAM.
  
2. This router has **tamper protection** in place, any attempt to boot from 3rd -party/non-authorized firmware will result in **boot-loop**, even you have flashed the famous breed bootloader. To recovery from this disaster, use a program called "breed enter" and follow it's instructions to get back to breed bootloader.
  
3. For reason unknown, the router can only successfully boot using 19.07 source code, so remember to check out the branch before compiling.
  
4. Only tested on the official openwrt source code.
  
5. Even using an openwrt firmware generated by this patch, the only working one is the initramfs-kernel version, that is, your config to the router will not survive after a reboot, so just bring all your config files to /openwrt/files when compiling the firmware.
  
6. Do it at your own risk, no guarantee from me.

Usage:

Download the patch file to your local PC, openwrt 19.07 source code should be ready beforehand.

Apply the patch and compile.

`git am < nr256.patch`

`make menuconfig`

`make -j$(($(nproc) + 1)) V=s`
