# What

tftp server inside vagrant box

# Usage

install box
```
$ vagrant box add ubuntu/xenial64
```

execute vagrant
```
vagrant up
```

Choose interface to bridge to.

```
1) en0: Wi-Fi (Wireless)
2) ap1
3) p2p0
4) awdl0
5) en1: Thunderbolt 1
6) en2: Thunderbolt 2
7) en3: Thunderbolt 3
8) en4: Thunderbolt 4
9) bridge0
10) en5: USB Ethernet(?)
==> default: When choosing an interface, it is usually the one that is
==> default: being used to connect to the internet.
    default: Which interface should the network bridge to? 1
```


do tftp to displayed address; files will saved & served in ./conf
```
    default:     inet 192.168.10.233/24 brd 192.168.10.255 scope global enp0s8
    default:     inet6 fe80::a00:27ff:fe9d:ecf5/64 scope link
```
address could be changed to DHCP or statistically assigned by "config.vm.network" in Vagrantfile

```
$ tftp 192.168.10.233
tftp> ascii
tftp> put testfile
Sent 15665511 bytes in 4.0 seconds
```
