# xva-img_docker
Docker Container for xva-img

Docker containerization of https://github.com/eriklax/xva-img


To create docker image: cd into folder containing this dockerfile.
run: 

    docker build -t xva-img .

use this command to enter the docker container to run commands:

    docker run -d -it -v [LOCAL SOURCE]:/mount xva-img

Run outside of Container
=======
Extract the XVA file.

    mkdir my-virtual-machine
    tar -xf my-virtual-machine.xva -C my-virtual-machine
    chmod -R 755 my-virtual-machine

XVA-IMG Commands
=======

Extract one of the disks

    xva-img -p disk-export my-virtual-machine/Ref\:1/ disk.raw

Splice the disk file (remove all files in the folder, required not to make any unnecessary mistakes)

    rm -rf my-virtual-machine/Ref\:1/*
    xva-img -p disk-import my-virtual-machine/Ref\:1/ disk.raw

Rebuild the XVA file

    xva-img -p package my-virtual-machine-fixed.xva my-virtual-machine/ova.xml my-virtual-machine/Ref\:1/
