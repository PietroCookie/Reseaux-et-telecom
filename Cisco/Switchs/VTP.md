# VTP

---

VTP (VLAN Trunk Protocol) permet de simplifier la gestion des VLAN dans un réseau. Grâce à ce protocole on peut configurer un VLAN sur un serveur VTP et celui-ci se propagera sur tous les commutateurs du domaine VTP.
Néanmoins, les switchs NEXUS ne prennent pas en compte le VTP. Il ne faut donc pas oublier ce point si votre réseau dispose de switch NEXUS.

> Plus d'informations sur le VTP : [Cisco VTP](https://www.cisco.com/c/fr_ca/support/docs/lan-switching/vtp/10558-21.html)

Pour mettre en place le VTP, il faut qu'au moins un commutateur soit le serveur VTP (généralement le coeur de réseau), les autres seront des clients.
A noter que les clients ne pourront pas créer, modifier ou supprimer de VLAN.

### Configuration du serveur VTP

Afin de configurer le serveur VTP, il faut déterminer un nom de domaine ainsi qu'un mot de passe (optionnel). Une fois cela déterminer, on se rend sur notre serveur VTP (ou coeur de réseau).

1. configuration de la version VTP
```
Switch(config)#vtp version 2
```

2. Configuration du nom de domaine VTP
```
Switch>enable
Switch#conf t
Switch(config)#vtp domain TOTO
```

3. Configuration du mode serveur
```
Switch(config)#vtp mode server
```

4. Configuration d'un mot de passe VTP
```
Switch(config)#vtp password PASSWORD
```

Après ces étapes, lorsque l'on configure un VLAN sur le serveur VTP, celui-ci est automatiquement créé sur les clients du domaine VTP.

### Configuration d'un client VTP

Pour configurer un client, on réaliser les mêmes étapes à part le `3.` que l'on modifier par cette ligne :
```
Switch(config)#vtp mode client
```
