### cosa command to run a qemu image of RHCOS, a custom Ignition config file (using Butane with fcos variant), and additional kernel arguements
source[https://coreos.github.io/coreos-assembler/cosa/run/#additional-kernel-arguments]
`cosa run '--qemu-image=rhcos_test.qcow2' '--ignition=ign_test.ign' --kargs 'foo bar'`
