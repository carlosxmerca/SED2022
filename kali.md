## kali linux

### Nmap
Nmap is a network scanner created by Gordon Lyon. Nmap is used to discover hosts and services on a computer network by sending packets and analyzing the responses. Nmap provides a number of features for probing computer networks, including host discovery and service and operating system detection.

Busca vulnerabilidades como puertos abiertos y información sobre estos

`nmap [address]`

Obtener la versión de los protocolos utilizados en los puetos

`nmap -sV [address]`

Obtener la versión del sistema operativo del servidor

`sudo nmap -O [address]`

### Spiderfoot
SpiderFoot is a reconnaissance tool that automatically queries over 100 public data sources (OSINT) to gather intelligence on IP addresses, domain names, e-mail addresses, names and more. You simply specify the target you want to investigate, pick which modules to enable and then SpiderFoot will collect data to build up an understanding of all the entities and how they relate to each other.

Levantar spiderfoot en el puerto 50000

`spiderfoot -l 0.0.0.0:5000`

Creamos un nuevo escaneo, agregamos el dominio y el nivel de investigación que deseamos

### Legion
This package contains an open source, easy-to-use, super-extensible and semi-automated network penetration testing tool that aids in discovery, reconnaissance and exploitation of information systems.

### SET
The Social-Engineer Toolkit (SET) is an open-source penetration testing framework designed for social engineering. SET has a number of custom attack vectors that allow you to make a believable attack in a fraction of time. These kind of tools use human behaviors to trick them to the attack vectors.

- Social Engineering Atacks
- Website Atack Vectors
- Metasploit Browser Exploit Method
   - Site cloner
- Credential Harvester Atack Method
   - Site cloner

### Metasploit Framework
The Metasploit Project is a computer security project that provides information about security vulnerabilities and aids in penetration testing and IDS signature development. 

1. `use auxiliary`
2. `use auxiliary/gather/search_email_collector`
3. `show options`
4. `set DOMAIN [address]`
5. `run`
6. `back`

### Burp suite
Is an integrated platform/graphical tool for performing security testing of web applications. Its various tools work seamlessly together to support the entire testing process, from initial mapping and analysis of an application's attack surface, through to finding and exploiting security vulnerabilities.

## Linea de ataques dentro de la red

###  Mac Spoofing
Suplantación de MAC

Es necesaria la MAC de un equipo, en este caso para encontrarla (Linux), se utiliza:   
```ifconfig -a``` 

visualizar la mac asignada actualmente y la mac permanente
```macchanger -s eth0```

```
OUTPUT:
Current MAC:   08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
Permanent MAC: 08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
```

Comando utilizado para cambiar la direccion MAC
```sudo macchanger -r eth0```

```
[sudo] password for xmerca: 
Current MAC:   08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
Permanent MAC: 08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
New MAC:       72:5d:0b:7e:eb:16 (unknown)
```

Obtener los proveedores de componentes asociados a las direcciones utilizando los primeros 3 pares de las direcciones para asociarlos
```sudo macchanger -l```

```
EXAMPLES:
18816 - f8:1e:df - Apple
18817 - f8:22:85 - Cypress Technology CO., LTD.
18818 - f8:27:93 - Apple, Inc
```

Cambiar la mac asociada a una interfaz en base a un registro de una empresa
```sudo macchanger -m 00:00:00:00:00:00:00:00 eth0```

Reiniciar la mac de una interfaz a la mac permanente
```sudo macchanger -p eth0```

```
OUTPUT:
Current MAC:   72:5d:0b:7e:eb:16 (unknown)
Permanent MAC: 08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
New MAC:       08:00:27:f6:5e:xx (CADMUS COMPUTER SYSTEMS)
```

### MAC flooding

### WireShark
Wireshark is a free and open-source packet analyzer. It is used for network troubleshooting, analysis, software and communications protocol development, and education. 

Para realizar practica:

`Sudo apt-get update`

`Sudo apt-get install dsniff`

Hacer una inundacion en la red 
```sudo macof -i eth0 -n 10```

### ARP poisoning
ARP Poisoning (also known as ARP Spoofing) is a type of cyber attack carried out over a Local Area Network (LAN) that involves sending malicious ARP packets to a default gateway on a LAN in order to change the pairings in its IP to MAC address table. ARP Protocol translates IP addresses into MAC addresses. Because the ARP protocol was designed purely for efficiency and not for security, ARP Poisoning attacks are extremely easy to carry out as long as the attacker has control of a machine within the target LAN or is directly connected to it.

*Corromper tabla de ARP*

```
Interface: 192.168.x.xxx --- 0xa
  Internet Address      Physical Address      Type
  192.168.x.x           xx-3d-xx-cd-xx-8e     dynamic
  192.168.x.xxx         xx-ff-xx-ff-xx-ff     static
```

### Ettercap
Ettercap is a free and open source network security tool for man-in-the-middle attacks on a LAN. It can be used for computer network protocol analysis and security auditing. 

Acciones:
`Options > Hosts > Scan hosts`
`Options > Hosts > Hosts lists`
`MITM > ARP poisoning`
`View > Statistics`
`View > Conections`

### Ataque DHCP 
### Yersinia
Yersinia is a framework for performing layer 2 attacks. It is designed to take advantage of some weakeness in different network protocols. It pretends to be a solid framework for analyzing and testing the deployed networks and systems.

 - Send DISCOVER packet
 - send RELEASE packet

*Saturara la red de solicitudes con paquetes DCHP*

### Hydra
Hydra is a parallelized login cracker which supports numerous protocols to attack. It is very fast and flexible, and new modules are easy to add. This tool makes it possible for researchers and security consultants to show how easy it would be to gain unauthorized access to a system remotely.

##### Atque de diccionario de fuerza bruta a cualquiera de los protocolos disponibles.

Directorio por defecto:
`usr/share/wordlists/fasttrack.txt`

Flags:
``` 
-L lista de usuarios
-l usuario
-P archivo
-s puerto
protocolo
-f terminar
-vV mostrar proceso
-t hilos en paralelo
```

Comando:
```
hydra -L /usr/share/wordlists/fasttrack.txt -P /usr/share/wordlists/sqlmap.txt -s 22 ssh://192.168.40.10 -V -t 4  
```

Ejemplo de ataque a puerto FTP
```
OUTPUT:
[DATA] attacking ftp://75.52.185.xxx:21/
[ATTEMPT] target 75.52.xxx.132 - login "Spring2017" - pass "Spring2017" - 1 of 49284 [child 0] (0/0)
[ATTEMPT] target 75.52.xxx.132 - login "Spring2017" - pass "Spring2016" - 2 of 49285 [child 0] (0/1)
```

### John the Ripper
John the Ripper is a free password cracking software tool. Originally developed for the Unix operating system, it can run on fifteen different platforms.

1. Crear hash
```
prueba1.txt (MD5)
202447d5d44ce12531f7207cb33b6bf7
```

2. Identificar tipo de hash
Usar: `Hash-identifier`

3. Utilizar John

- `john --help`
- `john --list=formats`

```
OUTPUT:
descrypt, bsdicrypt, md5crypt, md5crypt-long, bcrypt, scrypt, LM, AFS, 
tripcode, AndroidBackup, adxcrypt, agilekeychain, aix-ssha1, aix-ssha256, 
aix-ssha512, andOTP, ansible, argon2, as400-des, as400-ssha1, asa-md5, 
AxCrypt, AzureAD, BestCrypt, bfegg, Bitcoin, BitLocker, bitshares, Bitwarden, 
```

- `john --format=RAW-MD5 prueba1.txt`
- `john --show --format=RAW-MD5 prueba1.txt`

```
OUTPUT:
?:casa

1 password hash cracked, 0 left
```

Ejemplo 2:

```
prueba2.txt (SHA3 384)
a02effaf9361021e4b3e04180105e41ee8f9eb65704abbad60128d25544de600c94b671524c3735bfb8350c197270a8f
```

- `john --format=Raw-SHA384 prueba2.txt`

Archivos de configuracion de john: `/etc/john`

`john.conf  john-mail.conf  john-mail.msg
`

> Practica realizada en Kali Linux