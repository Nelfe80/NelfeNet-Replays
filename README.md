# NelfeNet-Replays

Point de départ de la diffusion des replays de records certifiés.

## Ce que c'est

Un replay est un objet **immuable, adressé par son contenu** (SHA-256). Les objets publiés ici
sont déposés en **assets de release**, nommés par leur hash :

```
https://github.com/<ce dépôt>/releases/download/<tag>/<sha256>.replay
```

Le téléchargement est public et anonyme. N'importe quelle borne peut venir chercher un objet par
une simple requête sortante, ce qui est la seule chose qu'une machine derrière un routeur
domestique sait faire.

## Ce que ce n'est pas

**Pas une bibliothèque.** Les replays vivent sur les bornes, qui se les répliquent entre elles.
Ce dépôt existe parce qu'une borne installée chez un particulier ne peut pas être jointe en
entrant : sans un premier dépôt joignable, personne ne pourrait aller chercher le record chez
celui qui vient de l'établir, et la diffusion ne démarrerait jamais. C'est une **amorce**.

**Pas une autorité.** Rien de ce qui est servi ici n'est cru sur parole. La borne qui récupère un
objet vérifie sa taille et son SHA-256 contre le manifeste du replay, et rejette tout ce qui ne
correspond pas. Ce dépôt peut disparaître sans qu'aucun replay déjà répliqué devienne invalide ou
introuvable.

**Pas un dépôt de code.** Les objets ne sont jamais commités dans l'historique git : ils seraient
alors impossibles à retirer, et le dépôt grossirait sans fin. Ils vivent en assets, donc
supprimables.

## Ce qui ne s'y trouve jamais

Un objet replay ne porte aucune donnée de la machine qui l'a produit : ni chemin de fichier, ni
cartographie de panneau, ni identifiant de périphérique, ni configuration d'émulateur, ni nom
d'utilisateur. Le manifeste n'emploie que des identifiants canoniques et des empreintes.

Un replay privé n'est jamais publié ici.

## Cycle de vie

Un objet est déposé quand le score correspondant entre dans un classement qui justifie sa
diffusion. Il peut être retiré une fois que le réseau en détient assez de copies : ce dépôt est
l'amorce de la diffusion, pas sa destination.
