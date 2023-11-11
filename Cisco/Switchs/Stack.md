# Stack

---

Les switchs peuvent être mis en stack. Cela permet à plusieurs switchs d'être vu comme un seul. Simplifiant ainsi la configuration, l'administration et pouvant permettre la redondance de certains liens ou d'éviter la multipliciter d'autres. La connexion entre les switchs stackés ne se ferait pas via un port mais via des modules dédiés branchés à l'arrière des switchs ce qui améliore la bande passante entre les switchs.

### Branchement d'une stack

Afin de relier les switchs qui devront être stacké il faut que chacun d'entre eux disposent des modules de stack. Vous aurez également besoin de câble de stack.

L'idée est que le branchement des switchs fassent une boucle afin d'avoir toujours une patte de secours pour éviter de perdre un switch en cas de dysfonctionnement d'un câble ou d'un module.

### Fonctionnement et configuration de la pile (stack)

Il faut savoir que les switchs d'une stack sont numérotés et qu'un seul switch est désigné comme maître de la stack.
Le maître peut être changé en fonction de la priorité attribué aux switchs (nous verrons cela plus loin).

Etant donné que nos switchs sont numérotés, les ports du troisième switch seront sous le format ``3/0/X``. Le premier chiffre correspond au numéro du switch.
Ainsi pour afficher la configuration du port numéro 24 du troisième switch de la stack il faut utiliser la commande suivant :

```
sh run Gi3/0/24
```