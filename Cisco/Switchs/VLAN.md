# VLAN

---

La base dans l'administration de switchs est la création de VLAN. Les VLAN permettent de découper de manière logique le réseau, c'est à dire que pour chaque réseau il n'est pas nécessaire d'avoir un switch pour interconnecter les équipements de ce réseau. 
Le switch pourra identifier quel port est dans quel réseau, évitant ainsi à un équipement de pouvoir communiquer avec un autre équipement qui n'est pas dans le même réseau mais branché sur le même switch.

**EXEMPLE**

Nous disposons de deux réseaux :
- 192.168.50.0/24
- 192.168.51.0/24

Si nous ne gérerions pas ce cas avec des VLAN ou des switchs non manageable, il nous faudrait un switch par réseau. Avec un switch manageable, nous allons créer un VLAN par réseau.

Pour créer un VLAN il faut se mettre en mode ``conf t`` et taper la commande suivant (où XX est le numéro du VLAN):

```
vlan XX
```

Généralement le numéro du VLAN utilisé est la valeur du troisième octet de l'adresse du réseau. Ici nous aurions le VLAN 50 et 51. (Il s'agit d'une recommandation et d'une convention largement répandu mais pas obligatoire)
/!\ Il est déconseillé d'utiliser le VLAN 1 puisque ce dernier est le VLAN par défaut des switchs.

Une fois que l'on a créer notre VLAN nous pouvons lui donner un nom :

```
name NOM_VLAN
```

Pour obtenir la liste des VLANS (uniquement en mode ```enable```) :

```
show vlan
```

Pour supprimer un VLAN rien de plus simple (en ```conf t```):

```
no vlan XX
```

Une fois que nous avons créer nos vlans, nous pouvons les attribuer aux ports du switch que nous souhaitons.

Pour attribuer un VLAN (et uniquement un seul) à un port, se mettre en ```conf t``` puis sur le port souhaité (par exemple pour Gi1/0/24) :
```
conf t
int Gi1/0/24 
```
Vous êtes maintenant sur la configuration port et pour l'ajouter dans un vlan :

```
switchport access vlan XX
```

Si vous mettez deux équipements dans le même réseau (en terme de configuration IP) mais qu'ils ne sont pas dans le même VLAN alors ils ne pourront pas communiquer ensemble.