# VLAN et VTP

---

## VLAN

La base dans l'administration de switchs est la création de VLAN. Les VLAN permettent de découper de manière logique le réseau, c'est à dire que pour chaque réseau il n'est pas nécessaire d'avoir un switch pour interconnecter les équipements de ce réseau. 
Le switch pourra identifier quel port est dans quel réseau, évitant ainsi à un équipement de pouvoir communiquer avec un autre équipement qui n'est pas dans le même réseau mais branché sur le même switch.

**EXEMPLE**

Nous disposons de deux réseaux :
- 192.168.1.0/24
- 192.168.2.0/24

Un PC en 192.168.1.1 et un en 192.168.1.2