OpenVSwitch
===========
OpenVSwitch adalah sebuah switch virtual berbasis linux. OpenVSwitch sendiri merupakan perangkat lunak sumber terbuka yang berada dalam lisensi Apache 2.0. OpenVSwitch mendukung pengontrolan secara automatis dengan protokol openflow.

![alt text](https://github.com/zufardhiyaulhaq/OpenVSwitch/blob/master/Images/featured-image.jpg)

Instalasi OpenVSwitch
=====================

Pada Tutorial ini, akan digunakan Ubuntu sebagai operating systemnya. Kamu dapat melakukan build from source melalui dokumentasi resmi [OpenVSwitch](http://docs.openvswitch.org/en/latest/intro/install/)

Proses Instalasi :
- Install Ubuntu
- Install OpenVSwitch

```
$ sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
$ sudo apt-get install openvswitch-switch 
```

- Cek Istalasi OpenVSwitch

```
ovs-vsctl --version
```

Menghubungkan OpenVSwitch ke OpenDayLight
=========================================

OpenDayLight adalah sebuah controller SDN yang bersifat Open Source. Kamu dapat membaca lebih dalam tenang controller ini di repositori [OpenDayLight](https://github.com/zufardhiyaulhaq/OpenDayLight).

OpenDayLight dan OpenVSwitch yang akan digunakan adalah berbasis docker yang diimplementasikan didalam GNS3. Untuk melihat instalasinya, silahkan lihat repositori [OpenDayLight](https://github.com/zufardhiyaulhaq/OpenDayLight).

## Topologi



