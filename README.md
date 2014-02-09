node-click-boards
=================

**NB: NOT DONE YET, BUT SOON... **

A node.js module to interface with various [click boards](http://www.mikroe.com/click/)
from [MikroElectronica](http://mikroe.com/),
running with the [mikroBUS cape](https://www.tigal.com/product/3651) 
on a [BeagleBone Black](http://beagleboard.org/products/beaglebone%20black).

The BeagleBone mikroBUS Cape connects upto four click boards to the BeagleBone Black.
As of this writing, there are over 70 click boards available.

Although the pro


Before Starting
---------------

You will need a [BeagleBone Black](http://beagleboard.org/products/beaglebone%20black) running Linux and node.
I'm running 3.8.13-bone30 with node v0.10.22.

You may find it useful to get the current image from [The Thing System]() and then deactivating the steward.
Instructions on finding the current disk image is located [here](http://thethingsystem.com/dev/Installation.html).
If you do that, then:

    % ssh debian@steward.local
    % sudo bash
    # sh /etc/init.d/steward stop
    # update-rc.d steward remove

You may also want to edit the hostname for the device, viz.,

    # vi /etc/hostname
    # vi /etc/hosts

Regardless, you will want to make sure you are current:

    # apt-get update
    # apt-get upgrade
    # apt-get install i2c-tools

Finally, if you are running off an SD card, you probably want to always boot from that SD card
(rather than holding down the boot button).
Look for _Perform Flash to eMMC_
[here](https://github.com/TheThingSystem/steward/wiki/Bootstrapping-the-BeagleBone-Black-with-Debian)
and it will explain how.

Finally, [install the mikroBUS driver](https://www.tigal.com/wiki/doku.php?id=tigalcapes:bb_mikrobus_cape).
To summarize:

    % wget http://download.tigal.com/tigal/BBBmikroBUScape/
    % tar xpf BB_board_dtbo.tar  
    # cp BB-MIKROBUS-01-00A0.dt* /lib/firmware/
    # halt

Now attach the mikroBUS cape and power-up your BeagleBoneBlack.
To see if all went well:

    % cat /sys/devices/bone_capemgr.9/slots
    ...
    57:P---L BBB-mikroBusCape,00A1,Tigal-KG,BB-MIKROBUS-01
    ...
