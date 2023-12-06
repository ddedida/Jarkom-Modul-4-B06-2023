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

## CIDR

### Labelling Subnet

- Label A
  
![ehe](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/04906204-3c3f-4bef-b00c-2c023cd6f208)

- Label B

![Slide 16_9 - 1](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/ddf1ba45-22db-462a-b4c1-e468daff1b9a)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/fc1c440f-1e83-498e-a2f8-c01772ef4e53)

- Label C

![Slide 16_9 - 2](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/0d8fbbb5-2050-432c-a87d-d17e20a4b44e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/68f13a0b-120b-4756-9114-8df2b7e554bc)

- Label D

![Slide 16_9 - 3](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/9cd604dd-2305-4ccb-8e85-26a7d2fefdd7)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/9b62eaa7-f51d-41c8-a72e-b719637d7611)

- Label E

![Slide 16_9 - 4](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/ad1c8fee-d7d2-4bda-b5fa-501388c99331)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/a58521c7-1ada-4da6-bcba-30a057328315)

- Label F

![Slide 16_9 - 5](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/0f0cfa8c-c456-48c6-aef0-bbf5158e5d02)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/805fb1dd-c1ef-4eda-8672-3f46d536a698)

- Label G

![Slide 16_9 - 6](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/b376b49f-a737-46d5-ad43-47cb8b954591)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/b29cab7b-b8fc-4935-a13a-c265aff8f1b5)

- Label H

![Slide 16_9 - 7](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/5ebb9197-b944-4913-88d5-f454d680e9ef)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/f6aedccd-c917-423f-8ee4-fdb7eb8532f1)

- Label I

![Slide 16_9 - 8](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/5a67fa9d-6a99-43ca-b87b-9172ba3f186e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c29c5773-3e68-493b-b722-2b1d4ac334fb)

Setelah melakukan labelling didapatkan label terakhir yaitu `I` dengan netmask `/14`.

### Tree

<img width="2869" alt="Jarkom Modul 3 Tree" src="https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c4a0693c-37e7-47e2-ad3f-984886038b95">

### Pembagian IP

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/4297e9b2-2f6e-419f-a0e7-ad1a3e142ba6)

### Konfigurasi Subnetting dan Routing Network

- Aura

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/1ff2bf37-1f4c-42ff-b104-e31a42419028)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/27e321c4-5c89-407c-93b8-28dd01fd4b8e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/478ab9d5-f35e-4688-8abd-4b8f005006c3)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/f45f23c0-228c-45d7-b60c-3017f4edbd6a)

- Denken

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/8d0f9290-9aad-48da-9116-608d59a4f19e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/a66868c7-3480-4baf-8ba4-74b1c56681c1)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c6997308-11f4-4890-b3ad-ff6f8813d1c2)

- RoyalCapital (63 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/b122f31f-c5c5-405a-9b03-c7fa9ef0b6a0)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/8d86d196-15ed-4dc5-b950-bf810e41dc30)

- WilleRegion (63 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/2229b327-82c0-42a0-a874-f40c490133a3)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c5426ce8-0d8b-43c8-934a-0d23894d3388)

- Frieren

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/41d02f29-738e-4b38-b5e6-827cf62e6a0b)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/ee5063ae-af10-4cf3-8df7-9028f216d10d)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/4da6adbe-27ba-4ddf-b8f4-2c735f8d4e13)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/3ff8f8f2-3075-42d9-9ad3-ebb20d6c7abc)

- LakeKorridor (24 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c71451d9-b372-4e1f-bfb7-8ebe599dfcc0)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c4e39c76-b213-472c-bc96-b785312c71ad)

- Flamme

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/4340bfdc-cdc7-4e8e-8ca9-db22a22a19e7)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/e51141d9-61ac-40be-9cbd-9d298bba5cf3)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/166d42b9-1c76-4b51-9526-487e2f8690eb)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/26408064-c326-49f1-949c-977e15307ba1)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/47dcb992-74e1-4e0b-af77-cf20d0931869)

- Fern

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/96f6d405-58bb-4468-8cc0-92b6dfc50a05)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/08695ff1-7732-4789-9d8c-c314fe9f27f2)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/5a719f54-7fef-4e96-9ee9-86f7331c4f76)

- LaubHills (397 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/17fca53e-7963-41c7-a7a0-a74e802da020)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/02df7b60-cf9c-40e2-94a1-7972f4be7205)

- AppetitRegion (625 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/5732498f-0dc1-471b-aede-2e73fa8dd399)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/71ed8061-7032-466e-ba44-479b1145383d)

- RohrRoad (1000 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/8465bc23-2271-4540-a428-deef6b494a53)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/23bd350e-e989-4228-bb38-0229acd6b50b)

- Himmel

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/62527eec-532e-4cbe-ae12-1b97ec59a15b)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/2abdc6fe-7637-4ce2-90e0-49ef6f11f737)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/ac08712c-5752-49dd-b495-d6920451a4f9)

- SchwerMountains (5 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/35ccdb4f-7def-4f10-b32c-9a07cb43d32f)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/15ae7125-5e03-4c4d-ad2a-0856421c2bd8)

- Eisen

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/68cfef31-e8a7-4cc3-b385-e4510b1daae3)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c9db86ec-112b-4597-9cbc-f704a42c38de)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/029bb842-b196-4eb8-a259-217433ac79f2)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/d1a51240-51bc-4628-b14e-093469d2fe62)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/6c61d731-58dc-49ed-b391-f4395a53b4c4)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/e8cdec8b-b891-4e96-88db-a0d2ef4f4f80)

- Ritcher (Server)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/6d90eb8b-eb5c-4126-8c2a-cdb84da8d1e0)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/27713eb8-bc34-4e24-8ee5-7e3d21d76bd3)

- Revolt (Server)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/54c959c9-f7fb-4688-a2e0-4b02a82044c7)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/4d438692-7b13-4ad9-bdd5-f46678843c57)

- Stark (Server)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/449613b8-2546-42da-86de-555fb1ca55ae)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/0004e90f-55fb-4e68-ab4b-b0c0c9a9c370)

- Lugner

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/f19d68a3-0e22-42d1-b21b-1857575d7eee)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/4e6abe8b-77af-46d0-84b7-bd4d3501098e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/d51141bf-7712-4076-b0d5-b2d546207f1e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/aa258335-3746-4ef6-9e6d-175a66799839)

- TurkRegion (1000 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/17f637ca-ce94-41db-b84b-b9b12fe98d46)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/ffcb50ab-0290-497a-817f-5a48d685a29c)

- GrobeForest (1000 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/9e8869bf-41c0-4cde-9ace-715013577000)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/8503b013-b231-4eb0-9e94-6aac83ab71e5)

- Linie

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/d56bf0a5-7777-4a0b-b779-b3381b2e8954)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/0d162942-6550-4375-b5c9-d8e23bbad16f)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/f3d7c4f1-9718-43cd-b99e-5479cf77f9fa)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/fa391bf8-6e42-4180-8769-66fde4dce3d8)

- GranzChannel (254 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/bf91efe3-fc2b-4ab0-b2d1-8ad633b13701)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/58f25053-14bb-44fb-8f29-be3094f99c3e)

- Lawine

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/069847a9-0566-43fa-8962-51e8c13b4259)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/20167557-6815-41d1-8f0a-450cafa5618f)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/836143f7-f724-4f10-ac44-b8ce4343df7f)

- BredtRegion (29 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/6aa3a48a-1400-4f93-83b0-9cbf00084e88)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/fb55b999-1ab2-4be0-82f7-784297e7cb58)

- Heiter

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/6f68e0ce-1870-4d71-b767-67b81e44b8fb)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/a7042b2f-94e4-44af-9fbc-aceccd711c96)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/3e84f7ba-c020-44d5-9a01-986007c19a8b)

- Sein (Server)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/cff98c74-69c8-42b8-85e8-6d815fde7261)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/8f43c990-73a6-4e05-a03d-c4ca9b153318)

- RiegelCanyon (510 Host)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/55ff85e3-cb77-4266-bdb9-6b36ad038f4e)

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/c2726153-380d-4ca2-8a87-5c301a6ad53c)

### Testing

![image](https://github.com/ddedida/Jarkom-Modul-4-B06-2023/assets/108203648/629a3383-be5b-41c4-a0ac-21f64c99d153)

