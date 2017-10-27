OpenVSwitch
===========
OpenVSwitch adalah sebuah switch virtual berbasis linux. OpenVSwitch sendiri merupakan perangkat lunak sumber terbuka yang berada dalam lisensi Apache 2.0. OpenVSwitch mendukung pengontrolan secara automatis dengan protokol openflow.

![alt text](https://github.com/zufardhiyaulhaq/OpenVSwitch/blob/master/Images/featured-image.jpg)

Instalasi OpenVSwitch
=====================

Pada Tutorial ini, akan digunakan Ubuntu sebagai operating systemnya. Kamu dapat melakukan `build from source` melalui dokumentasi resmi [OpenVSwitch](http://docs.openvswitch.org/en/latest/intro/install/)

Proses Instalasi :
- Install Ubuntu
- Install OpenVSwitch

```
$ sudo apt-get install qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
$ sudo apt-get install openvswitch-switch 
```

- Cek Instalasi OpenVSwitch

```
ovs-vsctl --version
```

Menghubungkan OpenVSwitch ke OpenDayLight
=========================================

OpenDayLight adalah sebuah controller SDN yang bersifat Open Source. Kamu dapat membaca lebih dalam tenang controller ini di repositori [OpenDayLight](https://github.com/zufardhiyaulhaq/OpenDayLight).

OpenDayLight dan OpenVSwitch yang akan digunakan adalah berbasis docker yang diimplementasikan didalam GNS3. Untuk melihat instalasinya, silahkan lihat repositori [OpenDayLight](https://github.com/zufardhiyaulhaq/OpenDayLight).

## Topologi
![alt text](https://github.com/zufardhiyaulhaq/OpenVSwitch/blob/master/Images/Topology.png)

## Konfigurasi OpenVSWitch

- Buat sebuah Bridge

```
$ ovs-vsctl add-br br0
```

- Masukan interface kedalam Bridge

```
$ ovs-vsctl add-port br0 eth0
$ ovs-vsctl add-port br0 eth1
$ ovs-vsctl add-port br0 eth2
$ ovs-vsctl add-port br0 eth3
```

- Set Controller ke OpenDayLight

```
$ ovs-vsctl set-controller br0 "tcp:192.168.122.254:6633"
```

## Konfigurasi OpenDayLight

- Jalankan OpenDayLight dengan Karaf

```
$ ./bin/karaf
```

- Install OpenDayLight DLUX dan L2Switch feature

```
feature:install odl-dlux-all odl-l2switch-all
```

## Verifikasi

Lihat apakah OpenVSwitch terkoneksi dengan Controller
```
$ ovs-vsctl list controller
_uuid               : dd619d79-33f8-4efb-89c6-bda14799b40e
connection_mode     : []
controller_burst_limit: []
controller_rate_limit: []
enable_async_messages: []
external_ids        : {}
inactivity_probe    : []
is_connected        : true
local_gateway       : []
local_ip            : []
local_netmask       : []
max_backoff         : []
other_config        : {}
role                : master
status              : {last_error="Connection refused", sec_since_connect="11", sec_since_disconnect="19", state=ACTIVE}
target              : "tcp:192.168.122.254:6633"
```

## Troubleshooting
- Jika OpenVSwitch dan OpenDayLight sudah terkoneksi tetapi tidak dapat terhubung ke controller, nyalakan interface bridge pada OpenVSwitch

```
$ ifconfig br0 up
```
