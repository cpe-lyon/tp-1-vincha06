Vincent CHAVES - 3ICS

# TP 1 - Installation d’Ubuntu Server et prise en main du shell

# ~~Exercice 1. Installation du serveur~~
Seulement pour les IRC et ETI.

# Exercice 2. Prise en main de l’interpréteur de commandes

## Manuel

### 1.	A l’aide du manuel, identifiez le rôle de la commande which
- Elle sert à localiser le chemin d’une commande

### 2. Quand on consulte une page du manuel, comment peut-on rechercher un terme (par exemple, chercherle terme option dans la page de manuel de which ?
- <code> man -k option </code>

### 3. Comment quitte-t-on le manuel ?
- avec "q"

### 4. Chaque section du manuel a une première page, qui présente le contenu de la section. Afficher la première page de la section 6 ; de quoi parle cette section ?
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

### 16. Que fait la commande dmesg | less ?
- Celà indique qu'il n'est pas possible d'éxecuter cette commande, et le symbole ~ s'affiche constamment.

### 17. Affichez à l’écran le fichier /etc/passwd ; que contient-il ? Quelle commande permet d’afficher la page de manuel de ce fichier ?
- Il contient les informations des utilisateurs.
- Pour afficher la page de manuel il faut entrer <code> man passwd </code>

### 18. Affichez seulement la première colonne triée par ordre alphabétique inverse
- <code> cut -d: -f1 /etc/passwd | sort -r </code>

### 19. Quelle commande nous donne le nombre d’utilisateurs ayant un compte sur cette machine (pas seulement les utilisateurs connectés) ?
<code> cut -d: -f1 /etc/passwd | sort -r | wc -w </code>

### 20. Combien de pages de manuel comportent le mot-clé conversion dans leur description ?
<code> man -k conversion | wc -l </code>
> 141

### 21. A l’aide de la commande find, recherchez tous les fichiers se nommant passwd présents sur la machine
- <code> find / -name passwd </code>

### 22. Modifiez la commande précédente pour que la liste des fichiers trouvés soit enregistrée dans le fichier ~/list_passwd_files.txt et que les erreurs soient redirigées vers le fichier spécial /dev/null
- <code> find / -name passwd > ~/list_passwd_files.txt 2> /dev/null </code>

### 23. Dans votre dossier personnel, utilisez la commande grep pour chercher où est défini l’alias ll vu précédemment
- <code> cat .bashrc | grep 11 </code>

### 24. Utilisez la commande locate pour trouver le fichier history.log.
- <code> sudo apt install plocate </code>
- <code> locate history.log </code>
- ![Capture](https://user-images.githubusercontent.com/113091304/189549811-86ab8e02-557a-4996-9fda-9236b20facb3.JPG)

### 25. Créer un fichier dans votre dossier personnel puis utilisez locate pour le trouver. Apparaît-il ? Pourquoi ?
- Non il n'apparaît pas puisque la commande locate utilise une base de donnée qui n'est pas mise à jour en temps réel.
- Puisqu'on vient de créer le fichier, il faut donc faire <code> sudo updatedb </code> pour la mettre à jour.
- On fait ensuite <code> locate nom_du_fichier </code>
- J'obtiens :
- ![12](https://user-images.githubusercontent.com/113091304/189550192-abbf80da-2d10-4996-8f0c-1b6bc3873b30.JPG)

# Exercice 3. Prise en main de l’interpréteur de commandes

### 1. Copiez le fichier /var/log/syslog dans votre dossier personnel sous le nom log.txt, puis ouvrez-le avec nano
- <code> cp /var/log/syslog ~/log.txt </code>
- <code> nano log.txt </code>
- ![image](https://user-images.githubusercontent.com/113091304/189610261-68ed036a-c256-4ad0-840a-d1207bdfb97c.png)

### 2. Remplacez toutes les occurrences du mot kernel par le mot noyau
- <code> cat log.txt | tr kernel noyau </code>
- Ou alors en utilisant l'éditeur nano :
- "Ctrl + 6"
- On remplace "kernel" par "noyau"
- ![image](https://user-images.githubusercontent.com/113091304/189617114-d7e6e26f-fb4c-4fa4-9100-f06a5d5e4968.png)
- puis "A" pour l'appliquer à tous les mots "kernel"
- ![image](https://user-images.githubusercontent.com/113091304/189620222-208d2cde-a5bf-44b5-bde5-bf97718226be.png)

### 3. Déplacer les 10 premières lignes à la fin du fichier
- Il faut faire Ctrl + K pour couper, puis Ctrl + ↓ pour aller à la fin du fichier, puis Ctrl + U pour coller.
- ![image](https://user-images.githubusercontent.com/113091304/189622347-f86de8c2-b77f-4398-93cc-deadeca5e4c6.png)

### 4. Annulez cette action
- Il faut faire Alt + U pour annuler

### 5. Enregistrez le fichier avant de quitter nano
- Il faut faire Ctrl + O puis Enter

# Exercice 4. Personnalisation du shell

### 1. Commencez par créer une copie de ce fichier, que vous appellerez .bashrc_bak
- <code> cat ~/.bashrc > ~/.bashrc_bak </code>

### 2. Editez le fichier .bashrc avec nano et décommentez la ligne force_color_prompt=yes pour activer la couleur. Enregistrez le fichier et quittez nano.
- <code> nano .bashrc </code>
- ![image](https://user-images.githubusercontent.com/113091304/190159825-1a2688d6-efae-402a-a78f-6be0282f7f51.png)

### 3. Le fichier .bashrc est lu au démarrage du shell ; pour le recharger, il faudrait donc se déconnecter puis se reconnecter ; mais il existe un autre moyen : la commande source .bashrc. Testez-la, l’invite de commande devrait immédiatement passer en couleurs.
- ![image](https://user-images.githubusercontent.com/113091304/190161061-0af8bcdf-c43e-4140-871e-2cd5ce70c7ce.png)

### 4. Les couleurs par défauts (surtout celle du dossier courant) ne sont pas très visibles. Dans .bashrc, cherchez les lignes commençant par PS1= ; elles indiquent la mise en forme de l’invite de commande (selon que l’on est en couleurs ou non). Sur cette ligne, on peut distinguer un certain nombre de raccourcis.Modifiez l’invite de commande pour qu’elle s’affiche sous la forme suivante : [heure] - user@host:chemin_courant$
- <code> PS1='${debian_chroot:+($debian_chroot)}[\033[01;31m]\A[\033[01;30m]] - [\033[01;32m]\u@\h[\033[01;36m]\w[\033[30m]$' </code>
- ![image](https://user-images.githubusercontent.com/113091304/190175134-91aabaa6-158f-41eb-81a8-15e1843022ce.png)













  

  
 







