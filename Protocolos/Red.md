# Conceptos Básicos de Red

## 1. Direcciones IP

### ¿Qué es?

Por sus siglas **Internet Protocol (Protocolo de Internet)** es un identificador único asignado a cada dispositivo conectado a una red que utiliza el Protocolo de Internet para comunicarse. Se puede pensar en ella como la dirección de una casa, que permite que los datos lleguen a su destino correcto.

### Tipos

* **IPv4:** Es la versión más común y utiliza una representación de 32 bits, lo que permite aproximadamente 4.3 mil millones de direcciones únicas. Se representa en formato decimal con cuatro octetos (por ejemplo *192.168.1.1*).

* **IPv6:** Debido al agotamiento de direcciones IPv4, se introdujo IPv6, que utiliza 128 bits y permite un número prácticamente infinito de direcciones. Se representa en formato hexadecimal y es más complejo (por ejemplo *2001:0db8:85a3:0000:0000:8a2e:0370:7334*).

### Clases

* **Direcciones Públicas:** Son accesibles desde cualquier lugar de Internet.

* **Direcciones Privadas:** Usadas dentro de una red local, no son accesibles directamente desde Internet. Ejemplos son 192.168.x.x, 10.x.x.x, y 172.16.x.x a 172.31.x.x.

## 2. Puertos

### ¿Qué es?

Un puerto es un número que se utiliza para identificar aplicaciones específicas en un dispositivo. Permite que múltiples aplicaciones o servicios se comuniquen simultáneamente a través de la misma dirección IP. Se puede pensar en un puerto como una puerta en un edificio; cada puerta lleva a una sala específica.

### Rangos

* **Puertos bien conocidos (0-1023):** Utilizados por servicios estándar como [HTTP](https://github.com/JohnFRivera/Practicas/blob/master/HTTP.md "Protocolo HTTP") (puerto 80), [HTTPS](https://github.com/JohnFRivera/Practicas/blob/master/HTTPS.md "Protocolo HTTPS") (puerto 443), FTP (puerto 21), etc.

* **Puertos registrados (1024-49151):** Usados por aplicaciones específicas registradas, pero no son tan universalmente reconocidos como los bien conocidos.

* **Puertos dinámicos o efímeros (49152-65535):** Asignados temporalmente para conexiones de cliente, como al navegar por la web.

## 3. Conexiones en Red

### Modelo Cliente-Servidor

* **Cliente:** Es el dispositivo que inicia la solicitud (por ejemplo, un navegador web).

* **Servidor:** Es el dispositivo que responde a la solicitud (por ejemplo, un servidor web que entrega páginas).

### Comunicación y Cierre

Una vez establecida la conexión, los datos pueden ser transmitidos. Al finalizar la comunicación, se debe cerrar la conexión de manera ordenada, utilizando un proceso de finalización que también involucra mensajes de reconocimiento.