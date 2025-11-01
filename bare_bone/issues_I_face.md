**Problem**

```bash
qemu-system-i386 -cdrom myos.iso
```

while I ran the above command to open the empty virtual machine, I got no bootable device in the black screen.

**Reason**

when we use grub to create `.iso` file if we didn't create it for the BIOS, it will not run basically it will create the .iso for the current machine capability
but qemu will not support EFI. but while it occurs, It created for the EFI. Not for BIOS, So that was the issue.

it is simply solved by below command:_(for this command to work you need have this `sudo apt-get install grub-pc-bin grub-common`)_
```bash
grub-mkrescue /usr/lib/grub/i386-pc -o myos.iso isodir
```

I solved it with a help this forum:[click here](https://f.osdev.org/viewtopic.php?t=28894)
