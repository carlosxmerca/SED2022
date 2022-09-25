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

> Practica realizada en Kali Linux