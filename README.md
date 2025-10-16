# lab02industrialescorte2
# 🧪 Laboratorio #2 – Conexión de Router, Switch y PC

## 🧰 Descripción General

En este laboratorio se realizó la **interconexión entre un switch, un router y un computador**, con el fin de **verificar la comunicación, revisar las tablas MAC y ARP**, y configurar los parámetros básicos de red en los dispositivos.

Se usó la misma configuración base del switch empleada en los laboratorios anteriores (VLAN1 activa con todos los puertos habilitados y direccionamiento DHCP automático).

Las evidencias visuales de esta práctica se encuentran en las imágenes:
**`punto1-0.png` a `punto1-4.png`**.

---

## ⚙️ Configuración del Switch

**Hostname:** `SW-LAB`

El switch se configuró con todos los puertos en modo *access* y dentro de la VLAN1.  
Además, se estableció la dirección IP de gestión y el *gateway* predeterminado.

```bash
SW-LAB#show vlan brief
VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/1 – Fa0/24, Gi0/1, Gi0/2
Configuración IP del Switch:

interface Vlan1
 ip address 192.168.1.2 255.255.255.0
!
ip default-gateway 192.168.1.1
Con esta configuración, el switch obtuvo conectividad hacia el router a través del gateway 192.168.1.1.

🌐 Conexión con el Router

El router se conectó al switch mediante uno de los puertos FastEthernet, configurado para asignar direcciones IP por DHCP al resto de los dispositivos conectados.

Esto permitió que el computador obtuviera su dirección IP automáticamente, confirmando la correcta propagación del servicio DHCP desde el router a través del switch.

🧩 Verificación de Tablas MAC y ARP

Se revisó la tabla MAC del switch para verificar el aprendizaje de direcciones asociadas a los dispositivos conectados:

SW-LAB#show mac address-table
Vlan    Mac Address       Type        Ports
----    -----------       --------    -----
1       00d0.97c1.a3b2    DYNAMIC     Fa0/1
1       0015.5d2f.44aa    DYNAMIC     Fa0/2
All     0180.c200.0000    STATIC      CPU
...


Esto confirmó que las interfaces estaban activas y comunicándose correctamente dentro de la VLAN1.

También se inspeccionó la tabla ARP del router, observando las asociaciones IP ↔ MAC de los dispositivos conectados.

🔍 Comprobaciones Realizadas

Se comprobó conectividad mediante ping entre el router, el switch y el PC.

Se verificó el aprendizaje dinámico de direcciones MAC en el switch.

Se comprobó que las interfaces FastEthernet estaban en estado up/up.

El servicio DHCP funcionó correctamente, asignando IPs dentro del rango configurado.

Se visualizó el tráfico en las tablas MAC y ARP para comprobar la correcta propagación.

📸 Evidencias

Imágenes asociadas al laboratorio:

Imagenes
punto1-0.png	
punto1-1.png
punto1-2.png	
punto1-3.png	
punto1-4.png	
