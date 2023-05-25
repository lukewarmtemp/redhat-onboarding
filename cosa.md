### cosa command to run a qemu image of RHCOS, a custom Ignition config file (using Butane with fcos variant), and additional kernel arguements
[Butane Configuration Parameters](https://coreos.github.io/butane/specs/)

[Butane to Ignition](https://docs.fedoraproject.org/en-US/fedora-coreos/producing-ign/)

[Cosa Kernel Arguments](https://coreos.github.io/coreos-assembler/cosa/run/#additional-kernel-arguments)

`cosa run --qemu-image rhcos_test.qcow2 --ignition ign_test.ign --kargs 'foo bar' --devshell-console`


### To exit out of devshell console
`sudo poweroff`


### basic kola command
`cosa kola --basic-qemu-scenarios`
