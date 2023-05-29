### cosa command to run a qemu image of RHCOS, a custom Ignition config file (using Butane with fcos variant), and additional kernel arguements
[Butane Configuration Parameters](https://coreos.github.io/butane/specs/)

[Butane to Ignition](https://docs.fedoraproject.org/en-US/fedora-coreos/producing-ign/)

[Cosa Kernel Arguments](https://coreos.github.io/coreos-assembler/cosa/run/#additional-kernel-arguments)

[Configure Cosa Alias](https://coreos.github.io/coreos-assembler/building-fcos/)

[Cosa Build Documentation](https://coreos.github.io/coreos-assembler/cosa/)

`cosa run --qemu-image rhcos_test.qcow2 --ignition ign_test.ign --kargs 'foo bar' --devshell-console`


### To exit out of devshell console
`sudo poweroff`


### basic kola command
`cosa kola --basic-qemu-scenarios`

### adding kola test patterns
[Kola Documentation](https://coreos.github.io/coreos-assembler/kola/)

`find -name 'kola-denylist.yaml`

### Adding Kola Tests
[xeno pipefail informaition](https://gist.github.com/mohanpedala/1e2ff5661761d3abd0385e8223e16425?permalink_comment_id=3945021)

`set -xeuo pipefail` is used in the test in order to stop the script from running when certain errors occur. If you o not set these flags, certain errors may be ignored and will continue running.

### Using Cosa Shell
```
cosa shell
```
