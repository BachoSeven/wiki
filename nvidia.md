# Guide for complete nvidia and tensorflow setup on arch linux using System76 Drivers

~ Nageen

[Source](https://archie9211.github.io/blog/guide-for-complete-nvidia-and-tensorflow-setup-on-arch-linux-using-system76-drvers-on-any-non-system76-device)

------------------------------------------------------------------------

Setting up nvidia drivers and making tensorflow to work on gpu on linux
system is always mind boggling task. I have many times
reinstalled/formatted my laptop just to get it working. No matter what
there is always something that messes up while setting up working
environment for tensorflow on grphic card.

In this post, I will explain an easy to perform procedure for installing
everything on Arch Linux so that you can finally execute tensorflow
programs on GPU.

Note: I am assuming that you have working Arch Linux installed with any
Desktop Environment(Gnome, KDE, i3 etc) with no extra packages related
to nvidia or tensorflow(e.g Bumblebee, optimus, nvidia etc). Make sure
you have yay installed.
We will install system76-power from **Arch User Repository(AUR)**. \[
**System76 have their own linux distribution Pop OS based on Ubuntu
which have inbuilt nvidia support.**\]

------------------------------------------------------------------------

------------------------------------------------------------------------

So lets get started:

```

    yay -S system76-power system76-dkms
    sudo systemctl enable system76-power.service

```

This will take some time to install.

System76 Drivers require “ec_sys.write_support=1” argument to be passed
for kernel to work. Open grub file with:

```

    sudo nano /etc/default/grub

```

And search for line starting with GRUB_CMDLINE_LINUX_DEFAULT and append
this in it. It should look something like this:

```

    ...
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ec_sys.write_support=1"
    ...

```

Then we will regenerate grub confab with this new setting using:

```

    sudo grub-mkconfig -o /boot/grub/grub.cfg

```

Install bumblebee and optimus:

```

    sudo pacman -S bumblebee primus
    sudo gpasswd -a $USER bumblebee
    sudo systemctl enable bumblebeed.service
    sudo pacman -S nvidia-dkms nvidia-settings

```

Reboot your system.

system76-power is used to switch the graphic cards between Intel and
nvidia, but it need a reboot after the change.

Switch the graphics to Intel:

```

    sudo system76-power graphics intel

```

And to switch to nvidia, use:

```

    sudo system76-power graphics nvidia

```

After reboot, turn on graphic card and load nvidia drivers using:

```

    sudo system76-power graphics power on
    sudo modprobe nvidia-drm nvidia-modeset nvidia

```

To confirm if nvidia drivers have successfully loaded and working, use:

```

    primusrun glxinfo | grep -i renderer

```

Output should be something like :

```

    OpenGL renderer string: GeForce 940MX/PCIe/SSE2

```

And to turn off:

```

    sudo rmmod nvidia-drm nvidia-modeset nvidia
    sudo system76-power graphics power off

```

For easy use you can you bash alias as follow:

```

    alias nvidia-settings="optirun -b none nvidia-settings -c :8 "
    alias nvidia-on="sudo system76-power graphics power on ; sudo modprobe nvidia-drm nvidia-modeset nvidia"
    alias nvidia-off="sudo rmmod nvidia-drm nvidia-modeset nvidia ; sudo system76-power graphics power off"

```

Now you can install tensorflow from directly arch linux official
repository

```

    sudo pacman -S python-tensorflow-cuda

```

If everything goes fine. You are ready to run tensorflow programs with
GPU now.

If you want to install nvidia drivers and tensorflow from from official
nvidia website follow this
[post](https://archie9211.github.io/blog/How-To-install-Nvidia-drivers-,-Cuda-and-tensorflow-on-Linux).

If you have any query, Comment below.

References:

1.  <https://wiki.archlinux.org/index.php/NVIDIA>
2.  <https://ebobby.org/2018/07/15/archlinux-on-oryp4/>
3.  <https://www.archlinux.org/packages/community/x86_64/python-tensorflow-cuda/>
