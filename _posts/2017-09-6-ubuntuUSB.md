---
layout: post
title: Carry your Linux around in a USB, boot it on Mac or PC. (The missing tutorial)
published: true
read_time: 5m
excerpt: Create portable Linux on a USB bootable on Mac and PC. Full working method, clearly described. 
tags:
- pendrivelinux
- pendrive linux
- ubuntu usb
- mac linux
- mac dual boot
- ubuntu flash drive
- refind
---

#### The Need  

I was recently using multiple machines for work (Lab machines, friend's laptop, etc) and I needed Linux. I own a 128GB MacBook Air I could'nt install Linux on it as storage was tiny. I did have a USB 3.0 flash drive which had speeds comparable to some(not-so-fast) harddrives. It struck me that if I install Linux on my flash drive it would make my life a hell lot easier. It was later that I realised it wasn't so straight forward mainly because of EFI boot and Mac 'quirks'. I did a lot of googling but could'nt find anything that worked. After reading multiple sources I deduced what was the problem. Since I got it figured out I decided to write this post so that other people can benefit from it.

#### The problem  

- Modern Macs boot using EFI and their bootloader expects boot partition to be HFS+ or APFS(High Sierra) not EXT4.
- Ubuntu installer is buggy and always installs bootloader in EFI partition of internal HDD despite being instructed to install it on EFI partition of flash drive.  
  - This makes the flash drive only bootable on the mac it was made on  

#### The Solution  

##### Step 1: Preparing live USB for installation  

- Download [https://unetbootin.github.io/](UNetbootin)  

- Download your favourite Ubuntu flavor, Im using Ubuntu Mate  

- Burn the iso to a USB drive(not on your installation flash drive) using UNetbootin  

  ​

##### Step 2: Boot using live installation drive  

- Plug both drives and press `option+power button`    

- Choose `EFI boot` option  

- Choose `Try Ubuntu without Installing`   

  ​

##### Step 3: Install Linux on target flash drive  

- Once into the live session, open terminal and run `ubuquity —no-bootloader`  , this will start installation wizard in a mode that wont install a bootloader (Dont worry we will take care of it later)  

![Run installer with no-bootloader option]({{site.baseurl}}/images/portable_linux_usb/0.png){:class="center-image"}  
<center>
Fig 1: Run installer with no-bootloader option  
</center>

- Keep going next untill an option comes as shown in below image. Choose `Something else`  

![Choose this option]({{site.baseurl}}/images/portable_linux_usb/1.png){:class="center-image"}  
<center>
Fig 2: Choose this option  
</center>

- On your target drive, create a 200MB `EFI System Partition` as the first partition (Primary)  
- Create a reasonable sized `ext4` partition, with `mount point = '\'` (Primary)  

![Create partitions similar to this]({{site.baseurl}}/images/portable_linux_usb/2.png){:class="center-image"}  
<center>
Fig 3: Sample partitions  
</center>

- Click on `Install` 
- Reboot into Mac after installation finishes  

##### Step 4: Setting up Boot manager
We will be using a super awesome 3rd party boot manager [rEFInd](http://www.rodsbooks.com/refind/). It can detect any operating systems installed in EFI mode and boot them.  
- Download [rEFInd](http://www.rodsbooks.com/refind/) zip and extract it  
- Open Terminal and navigate to rEFInd directory  
- Run `diskutil list` and find the name of your flash drive's EFI partition. (In my case /dev/disk2s1)  
- Run `./refind-install --usedefault /dev/diskXXX` (replace XXX with appropriate name)  

![output should be similar to this]({{site.baseurl}}/images/portable_linux_usb/3.png){:class="center-image"}  
<center>
Fig 4: Output must be similar to this  
</center>

Now your flash drive is ready to boot on any Mac or EFI compatible PC. Moreover, if you ever mess up your bootloader and are unable to boot rEFInd can help you boot into your OS (if it exists :p)  

#### Testing on Mac and PC  
##### MacBook Air (Early 2015)  
- Press `option+power` and select `EFI Boot`  
![rEFInd screen]({{site.baseurl}}/images/portable_linux_usb/4.jpg){:class="center-image"}  
<center>
Fig 5: rEFInd screen  
</center>

- Select your apropriate Linux to boot  
![Booted up]({{site.baseurl}}/images/portable_linux_usb/5.jpg){:class="center-image"}  
<center>
Fig 6: MacBook booted  
</center>

##### Asus X550LD (PC)     
- Boot from flash drive in `UEFI Mode`    
![rEFInd screen]({{site.baseurl}}/images/portable_linux_usb/6.jpg){:class="center-image"}  
<center>
Fig 7: rEFInd screen    
</center>

- Select your apropriate Linux to boot  
![Booted up]({{site.baseurl}}/images/portable_linux_usb/7.jpg){:class="center-image"}  
<center>
Fig 8: PC booted  
</center>