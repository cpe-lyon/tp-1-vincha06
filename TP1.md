Vincent CHAVES - 3ICS

# TP 1 - Installation d’Ubuntu Server et prise en main du shell

# ~~Exercice 1. Installation du serveur~~
Seulement pour les IRC et ETI.

# Exercice 2. Prise en main de l’interpréteur de commandes

## Manuel

### 1.	A l’aide du manuel, identifiez le rôle de la commande which
- Elle sert à localiser le chemin d’une commande

### 2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercher
le terme option dans la page de manuel de which ?
- <code> man -k option </code>

### 3. Comment quitte-t-on le manuel ?
- avec "q"

### 4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la
première page de la section 6 ; de quoi parle cette section ?
- <code> man 6 intro </code>
- La première page de la section 6 du manuel est une introduction décrivant les "jeux et petits programmes amusants" disponibles dans le système.


## Navigation dans l’arborescence des fichiers

### 1. allez dans le dossier /var/log
- <code> cd /var/log </code>

### 2. remontez dans le dossier parent (/var) en utilisant un chemin relatif
- <code> cd .. </code>

### 3. retournez dans le dossier personnel
- <code> cd </code>

### 4. revenez au dossier précédent (/var) sans utiliser de chemin
- <code> cd - </code>

### 5. essayez d’accéder au dossier /root ; que se passe-t-il ?
- Permission refusée :
> -bash: cd: /root: Permission denied

### 6. essayez la commande sudo cd /root ; que se passe-t-il ? Expliquez
- Commande non trouvée parce que "cd est une commande built in du bash, ce n'est pas un programme comme ls qui peut être lancé directement".

### 7. à partir de votre dossier personnel, créez l’arborescence suivante
- <code> cd </code>
- <code> mkdir dossier1 </code>
- <code> cd dossier1 </code>
- <code> touch fichier1 </code>
- <code> cd .. </code>
- <code> mkdir dossier2 </code>
- <code> cd dossier2 </code>
- <code> mkdir dossier2.1 </code>
- <code> mkdir dossier2.2 </code>
- <code> cd dossier2.2 </code>
- <code> touch fichier2 </code>
- <code> touch fichier3 </code>

### 8. revenez dans votre dossier personnel ; à l’aide de la commande rm, essayez de supprimer Fichier1, puis Dossier1 ; que se passe-t-il ?
- <code> rm dossier1/fichier1 </code>
- ça marche pour supprimer le fichier, mais pas pour le dossier.

### 9. quelle commande permet de supprimer un dossier ?
- <code> rmdir </code>

### 10. que se passe-t-il quand on applique cette commande à Dossier2 ?
- ça ne fonctionne pas puisque le dossier2 n'est pas vide

### 11. comment supprimer en une seule commande Dossier2 et son contenu ?
- <code> rm -r dossier2 </code>

## Commandes importantes

### 1. Quelle commande permet d’afficher l’heure ? A quoi sert la commande time ?
- Pour afficher l'heure:
- <code> date </code>
- La commande "time" sert à afficher le temps d'exécution d'une commande, par exemple:
- <code> time date  </code>
- pour afficher le temps d'éxecution de la commande "date".

### 2. Dans votre dossier personnel, tapez successivement les commandes ls puis la ; que peut-on en déduire
sur les fichiers commençant par un point ?
- Ce sont les fichiers cachés. "la" est l'alias de "ls -a".

### 3. Où se situe le programme ls ?
- Dans le dossier /user/bin/ls

### 4. Essayez la commande ll. Existe-t-il une entrée de manuel pour cette commande ? Utilisez les commandes alias ou alias pour en savoir plus sur la nature de cette commande.
- Non il n'existe pas d'entrée manuel. Cependant en faisant :
- <code> alias ll </code>
- la commande affiche que "ll" = "ls -alF"

### 5. Quelle commande permet d’afficher les fichiers contenus dans le dossier /bin ?
- <code> ls /bin </code>

### 6. Que fait la commande ls .. ?
- Elle affiche ce que contient le dossier précedent du dossier actuel (dans l'arborescence).
- C'est un peu comme si on faisait "cd .." puis "ls"

### 7. Quelle commande donne le chemin complet du dossier courant ?
- <code> pwd </code>

### 8. Que fait la commande echo 'bip' > plop exécutée 2 fois ?
- Elle écrit "bip" 2 fois dans un nouveau fichier "plop", ou remplace son contenu si le fichier existe déjà.

### 9. Que fait la commande echo 'bip' >> plop exécutée 2 fois ?
- Elle ajoute deux "bip" à la fin du fichier "plop".

### 10. Interprétez le comportement de la commande sleep 10 | echo 'toto' ?
- Le shell affiche d'abord "toto", puis il se met en pause/veille pendant 10 secondes.

### 11. A quoi sert la commande file ? Essayez la sur des fichiers de types différents.
- A afficher plus d'informations sur un fichier notament sur les propriétés de texte, par exemple : "Bourne-Again shell script, ASCII text executable"

### 12. Créez un fichier original qui contient la chaîne Hello Toto ! ; créer ensuite un lien lien_phy vers
ce fichier avec la commande ln original lien_phy. Modifiez à présent le contenu de original et
affichez le contenu de lien_phy : qu’observe-t-on ? Supprimez le fichier original ; quelle conséquence
cela a-t-il sur lien_phy ?
- <code> echo 'Hello Toto !' > original </code>
- <code> cd </code>
- <code> ln original lien_phy </code>
- <code> cat lien_phy </code>
- lien_phy contient "Hello Toto !"
- <code> echo 'goodbye' > original </code>
- lien_phy contient "goodbye", cela veut dire que lien_phy est une copie liée à original.
- En supprimant original, lien_phy n'est pas supprimé et contient toujours "goodbye". 

### 13. Créez à présent un lien symbolique lien_sym sur lien_phy avec la commande ln -s lien_phy lien_sym.
Modifiez le contenu de lien_phy ; quelle conséquence pour lien_sym ? Et inversement ? Supprimez le
fichier lien_phy ; quelle conséquence cela a-t-il sur lien_sym ?
- Modifier lien_phy modifie aussi lien_sym.
- Pareillement en sens inverse.
- Lorsque l'on supprime lien_phy, lien_sym est affiché en rouge et ne peut plus être ouvert.

### 14. Affichez à l’écran le fichier /var/log/syslog. Quels raccourcis clavier permettent d’interrompre et
reprendre le défilement à l’écran ?
- Ctrl + S permet d'interrompre le défilement à l'écran, puis Ctrl pour le reprende.

### 15. Affichez les 5 premières lignes du fichier /var/log/syslog, puis les 15 dernières, puis seulement les
lignes 10 à 20.
- Pour les 5 premières lignes : <code> head -n 5 var/log/syslog </code>
- Pour les 15 dernières : <code> tail -n 15 var/log/syslog </code>
- Pour les lignes 10 à 20 : <code> sed -n 10,20p /var/log/syslog </code>






