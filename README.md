# RTL8192eu linux drivers for Raspberry Pi

The official drivers for D-Link DWA-131 Rev E, with patches to keep it working on newer kernels on Raspberry Pi.  
Also works on Rosewill RNX-N180UBE v2 N300 Wireless Adapter.

**NOTE:** This is repo was forked from [Mange/rtl8192eu-linux-driver](https://github.com/Mange/rtl8192eu-linux-driver).  
Kudos to ``Magnus Bergmark <magnus.bergmark@gmail.com>`` for the great work. 

## Patches

You can see the applied patches, their sources and/or motivation by looking at the commits. The `master` branch will mostly be kept clean with a single commit per patch, except for Pull Requests. You can review commit by commit and then record the SHA in order to get a safe reference to use. As long as the SHA stays the same you know that what you get has been reviewed by you.

## Building and installing using source code

1. Install DKMS and other required tools

    ```shell
    # apt-get install git raspberrypi-kernel-headers build-essential dkms
    ```

2. Compile driver

    ```shell
    # make ARCH=arm
    ```

3. Install the driver

    ```shell
    # make install
    ```
    
If you wish to uninstall the driver at a later point, use

    ```shell
    # make uninstall
    ```    

## Building and installing using DKMS

This tree supports Dynamic Kernel Module Support (DKMS), a system for
generating kernel modules from out-of-tree kernel sources. It can be used to
install/uninstall kernel modules, and the module will be automatically rebuilt
from source when the kernel is upgraded (for example using your package manager).

1. Install DKMS and other required tools

    ```shell
    # apt-get install git raspberrypi-kernel-headers build-essential dkms
    ```

2. Add the driver to DKMS. This will copy the source to a system directory so
that it can used to rebuild the module on kernel upgrades.

    ```shell
    # dkms add .
    ```

3. Build and install the driver.

    ```shell
    # dkms install rtl8192eu/1.0
    ```

If you wish to uninstall the driver at a later point, use

    ```shell
    # dkms uninstall rtl8192eu/1.0
    ```

To completely remove the driver from DKMS use

    ```shell
    # dkms remove rtl8192eu/1.0 --all
    ```

## Submitting patches

1. Fork repo
2. Do your patch in a topic branch
3. Open a pull request on GH, or send it by email to `Alessandro Ratti <lord2y@gmail.com>`.
4. I'll squash your commits when everything checks out and add it to `master`.

## Copyright and licenses

The original code is copyrighted, but I don't know by whom. The driver download does not contain license information; please open an issue if you are the copyright holder.

Most C files are licensed under GNU General Public License (GPL), version 2.

[driver-downloads]: http://support.dlink.com.au/Download/download.aspx?product=DWA-131
[direct-download]: ftp://files.dlink.com.au/products/DWA-131/REV_E/Drivers/DWA-131_Linux_driver_v4.3.1.1.zip
[initial-commit]: https://github.com/Mange/rtl8192eu-linux-driver/commit/1387cf623d54bc2caec533e72ee18ef3b6a1db29

