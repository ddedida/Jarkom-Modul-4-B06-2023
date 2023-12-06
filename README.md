# Jarkom-Modul-4-B06-2023

**Praktikum Jaringan Komputer Modul 4**

| Nama                   | NRP        |
| ---------------------- | ---------- |
| M. Dafian Zaki Akhdan  | 5025211108 |
| Dewangga Dika Darmawan | 5025211109 |

# Laporan Resmi

Disini kami mengimplementasikan `VLSM` dengan menggunakan `GNS3` dan `CIDR` dengan menggunakan `Cisco`

## Topologi CIDR Cisco

## Topologi VLSM GNS

![image](https://github.com/Rencist/A07_Sisop_Individu_Modul_3/assets/91055469/e39d00c4-4761-45f0-980b-a2daacdec250)

## Prefix IP

Kelompok kami memiliki prefix IP `192.181`

## Rute

Sheet Pembagian IP dan Rute

![image](https://github.com/Rencist/A07_Sisop_Individu_Modul_3/assets/91055469/058410ee-f9da-4cd2-a975-3c9f4dd81b5b)

## VLSM

### Tree

![image](https://github.com/Rencist/A07_Sisop_Individu_Modul_3/assets/91055469/a64d5ddb-9c47-4ba6-bc8c-80402f4b5b8c)

### Pembagian IP

![image](https://github.com/Rencist/A07_Sisop_Individu_Modul_3/assets/91055469/6fb41f00-6e7e-4231-bca2-3423bd31a196)

### Konfigurasi Subnetting dan Routing Network

- RoyalCapital (63 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.23.2
	netmask 255.255.255.0
	gateway 192.181.23.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- WilleRegion (63 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.23.100
	netmask 255.255.255.0
	gateway 192.181.23.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Denken

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.114
	netmask 255.255.255.252
        gateway 192.181.24.113

auto eth1
iface eth1 inet static
	address 192.181.23.1
	netmask 255.255.255.0

```

- Aura

```sh
auto eth0
iface eth0 inet dhcp
up iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.181.24.0/19

auto eth1
iface eth1 inet static
	address 192.181.24.113
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.181.24.133
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 192.181.24.117
	netmask 255.255.255.252

# Eisen
up route add -net 192.181.24.136 netmask 255.255.255.252 gw 192.181.24.134
up route add -net 192.181.24.104 netmask 255.255.255.248 gw 192.181.24.134
up route add -net 192.181.24.140 netmask 255.255.255.252 gw 192.181.24.134
up route add -net 192.181.12.0 netmask 255.255.252.0 gw 192.181.24.134
up route add -net 192.181.22.0 netmask 255.255.255.0 gw 192.181.24.134
up route add -net 192.181.24.144 netmask 255.255.255.252 gw 192.181.24.134
up route add -net 192.181.20.0 netmask 255.255.254.0 gw 192.181.24.134
up route add -net 192.181.24.148 netmask 255.255.255.252 gw 192.181.24.134
up route add -net 192.181.24.0 netmask 255.255.255.192 gw 192.181.24.134
up route add -net 192.181.16.0 netmask 255.255.252.0 gw 192.181.24.134

# Denken
up route add -net 192.181.23.0 netmask 255.255.255.0 gw 192.181.24.114

# Frieren
up route add -net 192.181.24.64 netmask 255.255.255.224 gw 192.181.24.118
up route add -net 192.181.24.120 netmask 255.255.255.252 gw 192.181.24.118
up route add -net 192.181.24.124 netmask 255.255.255.252 gw 192.181.24.118
up route add -net 192.181.0.0 netmask 255.255.248.0 gw 192.181.24.118
up route add -net 192.181.8.0 netmask 255.255.252.0 gw 192.181.24.118
up route add -net 192.181.24.128 netmask 255.255.255.252 gw 192.181.24.118
up route add -net 192.181.24.96 netmask 255.255.255.248 gw 192.181.24.118


```

- Frieren

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.118
	netmask 255.255.255.252
	gateway 192.181.24.117

auto eth1
iface eth1 inet static
	address 192.181.24.65
	netmask 255.255.255.224

auto eth2
iface eth2 inet static
	address 192.181.24.121
	netmask 255.255.255.252

up route add -net 192.181.24.124 netmask 255.255.255.252 gw 192.181.24.122
up route add -net 192.181.0.0 netmask 255.255.248.0 gw 192.181.24.122
up route add -net 192.181.8.0 netmask 255.255.252.0 gw 192.181.24.122
up route add -net 192.181.24.128 netmask 255.255.255.252 gw 192.181.24.122
up route add -net 192.181.24.96 netmask 255.255.255.248 gw 192.181.24.122
```

- LakeKorridor (24 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.66
	netmask 255.255.255.224
	gateway 192.181.24.65
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Flamme

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.122
	netmask 255.255.255.252
	gateway 192.181.24.121

auto eth1
iface eth1 inet static
	address 192.181.24.125
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.181.24.129
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 192.181.8.1
	netmask 255.255.252.0

up route add -net 192.181.0.0 netmask 255.255.248.0 gw 192.181.24.126
up route add -net 192.181.24.96 netmask 255.255.255.248 gw 192.181.24.130
```

- Fern

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.126
	netmask 255.255.255.252
	gateway 192.181.24.125

auto eth1
iface eth1 inet static
	address 192.181.0.1
	netmask 255.255.248.0
```

- LaubHills (397 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.0.2
	netmask 255.255.248.0
	gateway 192.181.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- AppetitRegion (625 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.0.200
	netmask 255.255.248.0
	gateway 192.181.0.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- RohrRoad (1000 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.8.2
	netmask 255.255.252.0
	gateway 192.181.8.1
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Himmel

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.130
	netmask 255.255.255.252
	gateway 192.181.24.129

auto eth1
iface eth1 inet static
	address 192.181.24.97
	netmask 255.255.255.248
```

- ShcwerMountains (5 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.98
	netmask 255.255.255.248
	gateway 192.181.24.97
```

- Eisen

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.134
	netmask 255.255.255.252
        gateway 192.181.24.133

auto eth1
iface eth1 inet static
	address 192.181.24.105
	netmask 255.255.255.248

auto eth2
iface eth2 inet static
	address 192.181.24.145
	netmask 255.255.255.252

auto eth3
iface eth3 inet static
	address 192.181.24.137
	netmask 255.255.255.252

 auto eth4
 iface eth4 inet static
	address 192.181.24.141
	netmask 255.255.255.252

up route add -net 192.181.12.0 netmask 255.255.252.0 gw 192.181.24.142
up route add -net 192.181.22.0 netmask 255.255.255.0 gw 192.181.24.142

up route add -net 192.181.20.0 netmask 255.255.254.0 gw 192.181.24.146
up route add -net 192.181.24.148 netmask 255.255.255.252 gw 192.181.24.146
up route add -net 192.181.24.0 netmask 255.255.255.192 gw 192.181.24.146
up route add -net 192.181.16.0 netmask 255.255.252.0 gw 192.181.24.146
```

- Stark

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.138
	netmask 255.255.255.252
	gateway 192.181.24.137
	up echo nameserver 192.168.122.1 > /etc/resolv.conf
```

- Lugner

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.142
	netmask 255.255.255.252
        gateway 192.181.24.141

auto eth1
iface eth1 inet static
	address 192.181.22.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.181.12.1
	netmask 255.255.252.0
```

- TurkRegion (1000 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.12.2
	netmask 255.255.252.0
	gateway 192.181.12.1
```

- GrobeForest (250 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.22.2
	netmask 255.255.255.0
	gateway 192.181.22.1
```

- Richter

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.106
	netmask 255.255.255.248
	gateway 192.181.24.105
```

- Revolte

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.107
	netmask 255.255.255.248
	gateway 192.181.24.105
```

- Linie

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.146
	netmask 255.255.255.252
	gateway 192.181.24.145

auto eth1
iface eth1 inet static
	address 192.181.24.149
	netmask 255.255.255.252

auto eth2
iface eth2 inet static
	address 192.181.20.1
	netmask 255.255.254.0

up route add -net 192.181.24.0 netmask 255.255.255.192 gw 192.181.24.150
up route add -net 192.181.16.0 netmask 255.255.252.0 gw 192.181.24.150
```

- GranzChannel (254 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.20.2
	netmask 255.255.254.0
	gateway 192.181.20.1
```

- Lawine

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.150
	netmask 255.255.255.252
	gateway 192.181.24.149

auto eth1
iface eth1 inet static
	address 192.181.24.1
	netmask 255.255.255.192

up route add -net 192.181.16.0 netmask 255.255.252.0 gw 192.181.24.33
```

- BredtRegion (29 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.24.2
	netmask 255.255.255.192
	gateway 192.181.24.1
```

- Heiter

```sh
auto eth0
iface eth0 inet static
	address 192.181.24.33
	netmask 255.255.255.192
	gateway 192.181.24.1

auto eth1
iface eth1 inet static
	address 192.181.16.1
	netmask 255.255.252.0
```

- Sein

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.16.2
	netmask 255.255.252.0
	gateway 192.181.16.1

```

- RiegelCanyon (510 Host)

```sh
# Static config for eth0
auto eth0
iface eth0 inet static
	address 192.181.16.3
	netmask 255.255.252.0
	gateway 192.181.16.1
```

### Testing

https://github.com/Rencist/A07_Sisop_Individu_Modul_3/assets/91055469/eee31c28-0cac-416e-9208-961e3606b256
