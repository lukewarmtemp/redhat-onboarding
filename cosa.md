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

### Creating a Container Enviornment for Development using Podman
```
podman volume create <volume name>
```
Find volume location at `/home/USER/.local/share/containers/storage/volumes`
```
podman run -it --name fedora38 --volume src:/home/luyang/.local/share/containers/storage/volumes/kola-test-volume registry.fedoraproject.org/fedora:38
podman start fedora38
podman exec -it fedora38 /bin/bash
```

### Creating new Kola Tests
Fork and clone the repo:
```
git clone git@github.com:lukewarmtemp/coreos-assembler.git
```

Run the build script in the root folder, edit the kola tests based on this [documentation](https://coreos.github.io/coreos-assembler/kola/adding-tests/)

Go into the mantle folder and run
```
./build kola
```

Go to the root folder and rebuild cosa from the root folder.

### making changes to [file directory permissions test](https://github.com/coreos/fedora-coreos-config/blob/testing-devel/tests/kola/files/file-directory-permissions)
```yaml
variant: fcos
version: 1.4.0
passwd:
  users:
   - name: core
     ssh_authorized_keys:
      - ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDZHnKzuQjyt6elFsm2XHEHxrGOK7Es9HlJp70hN3JLViwGgFCPv5TQBItZD58xsdmk9QfcwnS0ojaIZdERZeMX7j/uxnVy3j/yjrcdQs2o/CB7IJRiRUTH7nmDa1MlXEFOTIcW160+FHfvywx91kNoVxx8Kq/b1l/KS3ZCiTF77T0KzD9LH9FlaoLOX6WWym
systemd:
  units:
    - name: luke.service
      enabled: true
      contents:
        "[Service]\n
         Type=oneshot\n
         ExecStart=/usr/bin/echo This is a service test!\n\n
         
         [Install]\n
         WantedBy=multi-user.target"
storage:
  files:
    - path: /etc/test
      mode: 0777
      contents:
        inline: "Hello World!"
```
```
butane --pretty --strict ign_test.bu > ign_test.ign
```
```
kola run ext.config.shared.files.file-directory-permissions --append-ignition ign_test.ign
```
