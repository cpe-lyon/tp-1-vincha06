## > Vincent CHAVES - 3ICS

# TP 1 - Installation d’Ubuntu Server et prise en main du shell

## ~~Exercice 1. Installation du serveur~~
Serveur déjà installé

## Exercice 2. Prise en main de l’interpréteur de commandes

### Manuel

**1.	A l’aide du manuel, identifiez le rôle de la commande which**
- Elle sert à localiser le chemin d’une commande

**2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?**
> man -k option

**3. Comment quitte-t-on le manuel ?**
- avec "q"

**4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?**
> man 6 intro
- La section 6 du manuel décrit les "jeux et petits programmes amusants" disponibles sur le système.


# Navigation dans l’arborescence des fichiers

**1. allez dans le dossier /var/log**
> cd /var/log

**2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**
> cd ..

**3. retournez dans le dossier personnel**
> cd

**4. revenez au dossier précédent (/var) sans utiliser de chemin**
> cd -

**5. essayez d’accéder au dossier /root ; que se passe-t-il ?**
- Permission refusée
- -bash: cd: /root: Permission denied

**6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez**
- Commande non trouvée parce que "cd est une commande built in du bash, ce n'est pas un programme comme ls qui peut être lancé directement".

**7. à partir de votre dossier personnel, créez l’arborescence suivante**
> cd
> mkdir dossier1
> cd dossier1
> touch fichier1
> cd ..
> mkdir dossier2
> cd dossier2
> mkdir dossier2.1
> mkdir dossier2.2 
> cd dossier2.2
> touch fichier2
> touch fichier3

**8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis
Dossier1 ; que se passe-t-il ?**
> rm dossier1/fichier1
- ça marche pour supprimer le fichier, mais pas pour le dossier.

**9. quelle commande permet de supprimer un dossier ?**
> rmdir

**10. que se passe-t-il quand on applique cette commande à Dossier2 ?**
- ça ne fonctionne pas puisque le dossier2 n'est pas vide

**11. comment supprimer en une seule commande Dossier2 et son contenu ?**
> rm -r dossier2
