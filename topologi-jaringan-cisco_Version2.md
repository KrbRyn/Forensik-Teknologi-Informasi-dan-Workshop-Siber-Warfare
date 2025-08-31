# Topologi Jaringan Cisco

## 1. Deskripsi Topologi
Topologi jaringan yang digunakan adalah **topologi star**, di mana seluruh perangkat client terhubung ke satu perangkat pusat (switch Cisco) dan router sebagai gateway ke internet.

## 2. Diagram Topologi

```
            +-----------+
            |  Router   | (Cisco 2901)
            +-----+-----+
                  |
            +-----+-----+
            |  Switch   | (Cisco Catalyst 2960)
            +-----+-----+
        _____|_____|_____
       |     |     |     |
  +----+ +---+ +---+ +---+
  |PC1 | |PC2| |PC3| |PC4|
  +----+ +---+ +---+ +---+
```

## 3. Penjelasan Perangkat

- **Router Cisco 2901**: Sebagai gateway yang menghubungkan jaringan lokal ke internet.
- **Switch Cisco Catalyst 2960**: Menghubungkan semua perangkat komputer dalam jaringan lokal.
- **PC1, PC2, PC3, PC4**: Komputer client yang terhubung ke switch.

## 4. Contoh Konfigurasi Cisco

### Konfigurasi Router Cisco

```shell
enable
configure terminal
hostname Router
interface GigabitEthernet0/0
 ip address 192.168.1.1 255.255.255.0
 no shutdown
exit
```

### Konfigurasi Switch Cisco

```shell
enable
configure terminal
hostname Switch
interface FastEthernet0/1
 switchport mode access
 switchport access vlan 10
exit
```

### Konfigurasi IP pada PC (Windows)

- **PC1**:  
  IP Address: 192.168.1.10  
  Subnet Mask: 255.255.255.0  
  Default Gateway: 192.168.1.1

- **PC2**:  
  IP Address: 192.168.1.11  
  Subnet Mask: 255.255.255.0  
  Default Gateway: 192.168.1.1

- **PC3**:  
  IP Address: 192.168.1.12  
  Subnet Mask: 255.255.255.0  
  Default Gateway: 192.168.1.1

- **PC4**:  
  IP Address: 192.168.1.13  
  Subnet Mask: 255.255.255.0  
  Default Gateway: 192.168.1.1

## 5. Catatan

- Topologi ini dapat dikembangkan dengan menambah perangkat atau VLAN sesuai kebutuhan.
- Untuk dokumentasi lebih profesional, Anda bisa menggunakan aplikasi Cisco Packet Tracer atau draw.io untuk membuat diagram dengan ikon Cisco.
