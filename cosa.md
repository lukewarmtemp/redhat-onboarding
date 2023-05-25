### cosa command to run a qemu image of RHCOS, a custom Ignition config file (using Butane with fcos variant), and additional kernel arguements
[Butane Configuration Parameters](https://coreos.github.io/butane/specs/)

[Cosa kernel arguments](https://coreos.github.io/coreos-assembler/cosa/run/#additional-kernel-arguments)

`cosa run '--qemu-image=rhcos_test.qcow2' '--ignition=ign_test.ign' --kargs 'foo bar'`
