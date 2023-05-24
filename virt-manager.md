# Create storage
```
sudo dd if=/dev/zero of=/var/lib/libvirt/images/guest.img bs=1M count=20480
```

# Download ISO and specifiy storage space you just created and the ISO for installation
```
sudo virt-install --name Fedora38 \
--description 'Fedora 38 Workstation' \
--ram 4096 --vcpus 2 \
--disk path=/var/lib/libvirt/images/guest.img,size=20 \
--os-type linux --os-variant fedora37 --network bridge=virbr0 \
--graphics vnc,listen=127.0.0.1,port=5901 \
--cdrom /var/lib/libvirt/images/Fedora-Workstation-Live-x86_64-38-1.6.iso \
--noautoconsole
```
