## Practica openssl
### Generando llave

`openssl enc -aes-128-cbc -k aloha -P -md sha1`

```
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
salt=24DC32E92A97BA1D
key=223AE06B972A05711494CBDA0BA5F098
iv =F367F7627A1D2FFEE6C201492E4694A1
```

### Encriptar por flujo

#### Encriptar
Encriptamos el archivo de texto, utilizando la **k** y el **iv**, que generamos al crear la llave 
```
openssl enc -e -aes-128-cbc -K 223AE06B972A05711494CBDA0BA5F098 -iv F367F7627A1D2FFEE6C201492E4694A1 -in enigma.txt -out salidaflujo.enc 
```

#### Desencriptar

```
openssl enc -d -aes-128-cbc -K 223AE06B972A05711494CBDA0BA5F098 -iv F367F7627A1D2FFEE6C201492E4694A1 -in salidaflujo.enc -out enigma1.txt
```

### Encriptar por bloques

#### Encriptar
`openssl enc -aes-256-cbc -in enigma.txt -out bloque.enc` 

Despues, ingresar una frase para crear la llave y con esa encriptar el archivo, posteriormente sera usada para desencriptarlo.


#### Desencriptar
`openssl enc -aes-256-cbc -d -in bloque.enc -out enigma3.txt` 

Solicitara la frase para desencriptar el archivo.

### Certificado

1. Creamos la llave privada 

`openssl genrsa -des3 -out almuerzo.key 2048`

2. Nos va a solicitar una «pass phrase» para acceder a la clave privada. 

3. Creamos nuestro certificado 

`openssl req -new -x509 -days 420 -key almuerzo.key -out jueves.crt`

Nos solicitará la «pass phrase» del paso anterior, y los siguientes datos de nuestra organización: 
```
– Country Name (2 letter code) [AU]: SV 
– State or Province Name (full name) [Some-State]: San Salvador 
– Locality Name (eg, city) []: Antiguo Cuscatlán 
– Organization Name (eg, company) : UCA 
– Organizational Unit Name (eg, section) []: TI 
– Common Name (e.g. server FQDN or YOUR name) []: 
– Email Address []: seguridad@dominio.com 
```

4. Verificamos los datos del certificado 

`openssl x509 -in jueves.crt -text -noout`

> Practica realizada en Ubuntu Desktop