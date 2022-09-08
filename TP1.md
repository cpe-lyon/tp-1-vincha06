
#Manuel

**1.	A l’aide du manuel, identifiez le rôle de la commande which**
- Elle sert à localiser le chemin d’une commande

**2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?**
- man -k option

**3. Comment quitte-t-on le manuel ?**
- avec "q"

**4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?**
- man 6 intro
- La section 6 du manuel décrit les "jeux et petits programmes amusants" disponibles sur le système.

#Navigation dans l’arborescence des fichiers

**1. allez dans le dossier /var/log**
- cd /var/log

**2. remontez dans le dossier parent (/var) en utilisant un chemin relatif**
- cd ..

**3. retournez dans le dossier personnel**
- cd

**4. revenez au dossier précédent (/var) sans utiliser de chemin**
- cd -

**5. essayez d’accéder au dossier /root ; que se passe-t-il ?**
- Permission refusée
- -bash: cd: /root: Permission denied

**6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez**
- 
