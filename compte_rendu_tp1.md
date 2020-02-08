GALLAND Cyprien
VATIN Clément

# Compte rendu TP1
### Installation d’Ubuntu Server et prise en main du shell

## Exercice 2. Prise en main de l’interpréteur de commandes
### Manuel
**1)** La commande which sert à localiser une commande ou un fichier exécuté dans l'environnement courant en utilisant la variable *path*
**2)** Pour rechercher un terme dans une page de manuel, il suffit de taper */terme_cherché* pour que ce terme soit mis en surbrillance dans le manuel.
**3)** Il est possible de quitter le manuel en appuyant sur q
**4)** Pour aficher la premiere page de la section 6 du manuel, il faut taper *man 6 intro* en ligne de commande. On apprends alors que la section 6 concerne tout les mini jeux du système.
### Navigation dans l’arborescence des fichiers

**1)** *cd /var/log* (pour aller dans le dossier /var/log).
**2)** Pour remonter dans le dossier parent par un chemin relatif : *cd . .*
**3)** retour dans le dossier personnel : *cd ~*
**4)** retour au dossier précédent (/var) sans utiliser de chemin : *cd -*
**5)** si on tape juste *cd /root*, l'accès nous est refusé.
**6)** en essayant *sudo cd /root*, on nous demande le mot de passe administrateur, puis on nous informe que la commande *sudo cd* n'existe pas. Il faut taper *sudo su* (pour garder les droits administrateurs sur plusieurs commandes), entrer notre mot de passe, et taper ensuite la commande voulue, à savoir *cd /root*.
**7)** Création d'une arborescence : 
*cd ~* // retour à la racine
*mkdir Dossier1* // mkdir permet de creer un dossier
*mkdir Dossier2*
*touch Dossier1/Fichier1* // touch permet de creer un fichier
*mkdir Dossier2/Dossier2.1*
*mkdir Dossier2/Dossier2.2*
*touch Dossier2/Dossier2.1/Fichier2*
*touch Dossier2/Dossier2.2/Fichier3*
**8) - 9)** *rm Fichier1* supprime le fichier 1. En revanche, *rm Dossier1* renvoie un message d'erreur. Pour supprimer un dossier, il faut utiliser *rmdir* au lieu de *rm*.
**10)** Il n'est pas possible de supprimer Dossier2 avec *rmdir Dossier2* car Dossier2 est plein.
**11)** Pour supprimer simultanément Dossier2 et son contenu, on utilise la commande *rm -R Dossier2*.
### Commandes importantes :
**1)** Pour afficher l'heure, on utilise la commande *date*. La commande *time*, elle, affiche le temps nécessaire pour executer une commande : (exemple : *time ls*).
Le real time renvoie le temps réel du système. User time correspond au temps nécessaire au processus, et sys time donne le temps mis par le système pendant l’exécution pour exécuter d'autres commandes.
**2)** *ls* affiche les fichiers visibles. *la* affiche tout les dossiers, y compris ceux cachés (dossier caché = dossier commençant par un point). *la* est en fait un allias de *ls*, utilisant l'argument -A.
**3)** On utilise *which ls* pour trouver l'emplacement de la commande ls (à savoir /user/bin/ls).
**4)** En cherchant la commande *ll* dans le manuel, on remarque qu'il n'existe pas d'entrée correspondante. Cela s'explique par le fait que *ll* est un alias de *ls* utilisant l'argument -alF. 
alF désignes les 3 options suivantes : 
a : liste tous les fichiers, même ceux cachés
l : liste utilisant un long listing incluant les droits , les tailles, les mois de création, etc.
F : classification de la sortie
**5)** Pour aﬀicher les fichiers contenus dans le dossier /bin, on tape la commande suivante : *ls /bin*
**6)** la commande *ls . .* affiche le contenu du répertoire parent (d'une manière générale, . . est un raccourci pour désigner le répertoire parent).
**7)** Pour afficher le chemin absolu du répertoire courant, on utilise la commande *pwd*
**8) 9)** la commande *echo 'yo' > plop* permet d'envoyer la sortie de la commande (ici, yo) dans le fichier plop (créé par la même occasion).
si on ajoute un chevron (*echo 'yo' > plop*) : on ajoute à la fin du fichier. Si on en met un seul, on écrase le contenu éventuel du fichier.
**10)** La commande *file* renvoie le type du fichier.
**11)** On commence par créer un fichier toto qui contient la chaîne Hello Toto !. On crée ensuite un lien (titi) vers ce fichier, avec la commande *ln toto titi*. On modifie le contenu de toto, et on affiche le contenu de titi. On remarque alors que la modification de toto à également modifié le contenu de titi.
On supprime ensuite le fichier toto. Cela n'entraîne pas la suppression de titi.
**12)** On crée à présent un lien symbolique tutu sur titi, avec la commande *ln -s titi tutu*. Comme précédemment, la modification de tutu entraîne celle de titi, et vice versa. 
Cependant, cette fois, la suppression de titi entraîne la suppression de tutu. 
**13)** On exécute la commande *cat /var/log/syslog*. Le résultat est long, et un texte se met à défiler sur l'écran. Pour interrompre le défilement, on exécute CTRL + S. Pour le reprendre, CTRL + Q.
**14)** pour afficher les 5 premières lignes du fichier /var/log/syslog : *head /var/log/syslog -n 5*. Pour afficher les 15 dernières, *tail /var/log/syslog -n 15*. Enfin, pour afficher les lignes 10 à 20, on exécute *head -10 /var/log/syslog | tail -n -20*
**15)** la commande *dmesg | less* permet d'afficher lamémmoire tampon du noyau (*dmesg*), et d'afficher une interface CLI permettant de se déplacer dans le fichier obtenu (*less*).
Le pipe | permet d'amener la sortie d'une commande dans une autre commande.
**16)** On affiche le fichier /etc/passwd (*cat /etc/passwd*). Il contient la liste des utilisateurs, et leurs numéros (les utilisateurs commencent avec un numéro à 1000, les administrateurs à 500).
Pour afficher la page de manuel de ce fichier, on exécute la commande *man /etc/passwd*.
**17)** On souhaite afficher seulement la première colonne, par ordre alphabétique inverse :
*cut -c1 /etc/passwd |sort -r*
La commande *sort* permet de trier la sortie : -d par ordre alphabétique, -r par ordre inverse. Quand la la commande *cut -c X*, elle sélectionne et affiche les X premières colonnes.
**18)** Pour connaître le nombre d’utilisateurs ayant un compte sur cette machine (et pas seule-ment les utilisateurs connectés), il faut entrer la commande *wc -l /etc/passwd*. En effet, *wc -l* affiche le nombre de lignes d'un fichier, et le fichier passwd contient un utilisateur par ligne.
**19)** On souhaite savoir combien de pages de manuel comportent le mot-clé **conversion** dans leur description. Pour ce faire on utilise *man -k 'conversion'*, qui recense toutes les occurrences de **conversion** dans les pages de descriptions du manuel.
**20)** On veut désormais chercher tous les fichiers se nommant passwd présents sur la machine. Pour ce faire, la commande est *find / -name "passwd"*.
**21)** En modifiant la commande comme ceci : *find / -name 'passwd > ~/list_passwd_files.txt 2> /dev/null*, la liste des fichiers trouvés est enregistrée dans le fichier~/list_passwd_files.txt, et les erreurs sont redirigées vers le fichier spécial /dev/null.
**22)** On utilise grep pour rechercher le mot **alias** (Car ll est un alias de ls) : *grep -rl alias ~/.bash** *~/.profile /etc/profile /etc/bash.bashrc*.
Cela nous indiquera dans quel fichier est utilisé le mot **alias**, ce qui nous permettra de rechercher la définition de *ll* dedans.
**23)** Pour trouver history.log, on execute *locate history.log*. Cependant, locate n'est pas installée par défaut : On l'installe donc (*sudo apt install mlocate*), on ré exécute la commande et on obtient le chemin d'accés : /var/log/apt/history.log
**24)** On crée un fichier dans notre répertoire personnel, puis on cherche à le trouver grâce à *locate*. Mais il n'apparait pas... En effet, *locate* utilise la base updatedb pour trouver les fichiers. 
Or cette base n'est actualisée qu'une fois par jour... Le fichier ayant été crée à l'instant, la commande ne peut donc pas le trouver.
## Exercice 3 : découverte de l'éditeur de texte nano
**1)** On commence par copier le fichier /var/log/syslog dans notre dossier personnel sous le nom log.txt : *cp /var/log/syslog ~*.
Pour l'ouvrir avec nano : *nano syslog*.
**2)** On souhaite remplacer toutes les occurrences du mot **kernel** par le mot noyau : Pour ce faire, on utilise la commande suivante : *CTRL + \*, puis on tape **kernel** puis **noyau**. Il ne reste plus qu'a approuver le remplacement pour chaque occurrence.
**3)** On déplace ensuite les 10 premières lignes en fin de fichier : On sélectionne les 10 premieres lignes (avec SHIFT + MAJ), puis on tape *CTRL + K*, on descend à la fin du fichier *CTRL + _ 500000* et on tape *CTRL + U*.
**4)** Pour annuler l'action, on utilise *ALT+ U*.
**5)** Enfin, on utilise *CTRL + X + Y + ENTRER* pour enregistrer le fichier et quitter nano. (le Y sert à confirmer l'enregistrement, le entrer sert au nom du fichier).
## Exercice 4 : Personnalisation du shell
**1)** on crée une copie du fichier ~/.bashrc, que l'on nomme ~/.bashrc_bak (*cp .bashrc bashrc_bak*).
**2)** On édite le fichier.bashrc avec vim (*vim .bashrc*), et on décommente la ligne *force_color_prompt=yes*, pour activer la couleur. (*/force* permet de chercher ce qui commence par force, puis *I* pour écrire, et on supprime le #). On enregistre et on quitte (*echap:wq*).
**3)** En utilisant la commande *source .bashrc*, l'invite de commande passe en couleur automatiquement, sans avoir eu à redemarrer la machine.
**4)** On souhaite modifier l’invite de commande pour qu’elle s’aﬀiche sous la forme suivante : l’heure en violet et entre crochets, le chemin du dossier courant en cyan.
Pour ce faire on utilise les commandes suivantes :
*vim .bashrc* // Ouvre le fichier avec vim.
*I*// Pour pouvoir écrire dedans
On modifie la premiere ligne PS1 comme suit :
PS1 = '\${debian_chroot:+(\$debian_chroot)}\[\033[01;323m\]\u@\h\[\033[00m]:\[\033;34m\]\w\[\033[00m\]\$
*echap:wq* // Enregistre et quitte vim.

GALLAND Cyprien
VATIN Clément

# Compte rendu TP1
### Installation d’Ubuntu Server et prise en main du shell

## Exercice 2. Prise en main de l’interpréteur de commandes
### Manuel
**1)** La commande which sert à localiser une commande ou un fichier exécuté dans l'environnement courant en utilisant la variable *path*
**2)** Pour rechercher un terme dans une page de manuel, il suffit de taper */terme_cherché* pour que ce terme soit mis en surbrillance dans le manuel.
**3)** Il est possible de quitter le manuel en appuyant sur q
**4)** Pour aficher la premiere page de la section 6 du manuel, il faut taper *man 6 intro* en ligne de commande. On apprends alors que la section 6 concerne tout les mini jeux du système.
### Navigation dans l’arborescence des fichiers

**1)** *cd /var/log* (pour aller dans le dossier /var/log).
**2)** Pour remonter dans le dossier parent par un chemin relatif : *cd . .*
**3)** retour dans le dossier personnel : *cd ~*
**4)** retour au dossier précédent (/var) sans utiliser de chemin : *cd -*
**5)** si on tape juste *cd /root*, l'accès nous est refusé.
**6)** en essayant *sudo cd /root*, on nous demande le mot de passe administrateur, puis on nous informe que la commande *sudo cd* n'existe pas. Il faut taper *sudo su* (pour garder les droits administrateurs sur plusieurs commandes), entrer notre mot de passe, et taper ensuite la commande voulue, à savoir *cd /root*.
**7)** Création d'une arborescence : 
*cd ~* // retour à la racine
*mkdir Dossier1* // mkdir permet de creer un dossier
*mkdir Dossier2*
*touch Dossier1/Fichier1* // touch permet de creer un fichier
*mkdir Dossier2/Dossier2.1*
*mkdir Dossier2/Dossier2.2*
*touch Dossier2/Dossier2.1/Fichier2*
*touch Dossier2/Dossier2.2/Fichier3*
**8) - 9)** *rm Fichier1* supprime le fichier 1. En revanche, *rm Dossier1* renvoie un message d'erreur. Pour supprimer un dossier, il faut utiliser *rmdir* au lieu de *rm*.
**10)** Il n'est pas possible de supprimer Dossier2 avec *rmdir Dossier2* car Dossier2 est plein.
**11)** Pour supprimer simultanément Dossier2 et son contenu, on utilise la commande *rm -R Dossier2*. Le -R permet d'ajouter de la recursivité et ainsi de supprimer tout le contenu d'un dossier, soit tous les sous dossiers et tous les fichiers.
### Commandes importantes :
**1)** Pour afficher l'heure, on utilise la commande *date*. La commande *time*, elle, affiche le temps nécessaire pour executer une commande : (exemple : *time ls*).
Le real time renvoie le temps réel du système. User time correspond au temps nécessaire au processus, et sys time donne le temps mis par le système pendant l’exécution pour exécuter d'autres commandes.
**2)** *ls* affiche les fichiers visibles. *la* affiche tout les dossiers, y compris ceux cachés (dossier caché = dossier commençant par un point). *la* est en fait un allias de *ls*, utilisant l'argument -A.
**3)** On utilise *which ls* pour trouver l'emplacement de la commande ls (à savoir /user/bin/ls).
**4)** En cherchant la commande *ll* dans le manuel, on remarque qu'il n'existe pas d'entrée correspondante. Cela s'explique par le fait que *ll* est un alias de *ls* utilisant l'argument -alF. 
alF désignes les 3 options suivantes : 
a : liste tous les fichiers, même ceux cachés
l : liste utilisant un long listing incluant les droits , les tailles, les mois de création, etc.
F : classification de la sortie
**5)** Pour aﬀicher les fichiers contenus dans le dossier /bin, on tape la commande suivante : *ls /bin*
**6)** la commande *ls . .* affiche le contenu du répertoire parent (d'une manière générale, . . est un raccourci pour désigner le répertoire parent).
**7)** Pour afficher le chemin absolu du répertoire courant, on utilise la commande *pwd*
**8) 9)** la commande *echo 'yo' > plop* permet d'envoyer la sortie de la commande (ici, yo) dans le fichier plop (créé par la même occasion).
si on ajoute un chevron (*echo 'yo' > plop*) : on ajoute à la fin du fichier. Si on en met un seul, on écrase le contenu éventuel du fichier.
**10)** La commande *file* renvoie le type du fichier.
**11)** On commence par créer un fichier toto qui contient la chaîne Hello Toto !. On crée ensuite un lien (titi) vers ce fichier, avec la commande *ln toto titi*. On modifie le contenu de toto, et on affiche le contenu de titi. On remarque alors que la modification de toto à également modifié le contenu de titi.
On supprime ensuite le fichier toto. Cela n'entraîne pas la suppression de titi.
**12)** On crée à présent un lien symbolique tutu sur titi, avec la commande *ln -s titi tutu*. Comme précédemment, la modification de tutu entraîne celle de titi, et vice versa. 
Cependant, cette fois, la suppression de titi entraîne la suppression de tutu. 
**13)** On exécute la commande *cat /var/log/syslog*. Le résultat est long, et un texte se met à défiler sur l'écran. Pour interrompre le défilement, on exécute CTRL + S. Pour le reprendre, CTRL + Q.
**14)** pour afficher les 5 premières lignes du fichier /var/log/syslog : *head /var/log/syslog -n 5*. Pour afficher les 15 dernières, *tail /var/log/syslog -n 15*. Enfin, pour afficher les lignes 10 à 20, on exécute *head -10 /var/log/syslog | tail -n -20*
**15)** la commande *dmesg | less* permet d'afficher la mémmoire tampon du noyau (*dmesg*), et d'afficher une interface CLI permettant de se déplacer dans le fichier obtenu (*less*).
Le pipe | permet d'amener la sortie d'une commande dans une autre commande.
**16)** On affiche le fichier /etc/passwd (*cat /etc/passwd*). Il contient la liste des utilisateurs, et leurs numéros (les utilisateurs commencent avec un numéro à 1000, les administrateurs à 500).
Pour afficher la page de manuel de ce fichier, on exécute la commande *man /etc/passwd*.
**17)** On souhaite afficher seulement la première colonne, par ordre alphabétique inverse :
*cut -c1 /etc/passwd |sort -r*
La commande *sort* permet de trier la sortie : -d par ordre alphabétique, -r par ordre inverse. Quand la la commande *cut -c X*, elle sélectionne et affiche les X premières colonnes.
**18)** Pour connaître le nombre d’utilisateurs ayant un compte sur cette machine (et pas seule-ment les utilisateurs connectés), il faut entrer la commande *wc -l /etc/passwd*. En effet, *wc -l* affiche le nombre de lignes d'un fichier, et le fichier passwd contient un utilisateur par ligne.
**19)** On souhaite savoir combien de pages de manuel comportent le mot-clé **conversion** dans leur description. Pour ce faire on utilise *man -k 'conversion'*, qui recense toutes les occurrences de **conversion** dans les pages de descriptions du manuel.
**20)** On veut désormais chercher tous les fichiers se nommant passwd présents sur la machine. Pour ce faire, la commande est *find / -name "passwd"*.
**21)** En modifiant la commande comme ceci : *find / -name 'passwd > ~/list_passwd_files.txt 2> /dev/null*, la liste des fichiers trouvés est enregistrée dans le fichier~/list_passwd_files.txt, et les erreurs sont redirigées vers le fichier spécial /dev/null.
**22)** On utilise grep pour rechercher le mot **alias** (Car ll est un alias de ls) : *grep -rl alias ~/.bash** *~/.profile /etc/profile /etc/bash.bashrc*.
Cela nous indiquera dans quel fichier est utilisé le mot **alias**, ce qui nous permettra de rechercher la définition de *ll* dedans.
**23)** Pour trouver history.log, on execute *locate history.log*. Cependant, locate n'est pas installée par défaut : On l'installe donc (*sudo apt install mlocate*), on ré exécute la commande et on obtient le chemin d'accés : /var/log/apt/history.log
**24)** On crée un fichier dans notre répertoire personnel, puis on cherche à le trouver grâce à *locate*. Mais il n'apparait pas... En effet, *locate* utilise la base updatedb pour trouver les fichiers. 
Or cette base n'est actualisée qu'une fois par jour... Le fichier ayant été crée à l'instant, la commande ne peut donc pas le trouver.
## Exercice 3 : découverte de l'éditeur de texte nano
**1)** On commence par copier le fichier /var/log/syslog dans notre dossier personnel sous le nom log.txt : *cp /var/log/syslog ~*.
Pour l'ouvrir avec nano : *nano syslog*.
**2)** On souhaite remplacer toutes les occurrences du mot **kernel** par le mot noyau : Pour ce faire, on utilise la commande suivante : *CTRL + \*, puis on tape **kernel** puis **noyau**. Il ne reste plus qu'a approuver le remplacement pour chaque occurrence.
**3)** On déplace ensuite les 10 premières lignes en fin de fichier : On sélectionne les 10 premieres lignes (avec SHIFT + MAJ), puis on tape *CTRL + K*, on descend à la fin du fichier *CTRL + _ 500000* et on tape *CTRL + U*.
**4)** Pour annuler l'action, on utilise *ALT+ U*.
**5)** Enfin, on utilise *CTRL + X + Y + ENTRER* pour enregistrer le fichier et quitter nano. (le Y sert à confirmer l'enregistrement, le entrer sert au nom du fichier).
## Exercice 4 : Personnalisation du shell
**1)** on crée une copie du fichier ~/.bashrc, que l'on nomme ~/.bashrc_bak (*cp .bashrc bashrc_bak*).
**2)** On édite le fichier.bashrc avec vim (*vim .bashrc*), et on décommente la ligne *force_color_prompt=yes*, pour activer la couleur. (*/force* permet de chercher ce qui commence par force, puis *I* pour écrire, et on supprime le #). On enregistre et on quitte (*echap:wq*).
**3)** En utilisant la commande *source .bashrc*, l'invite de commande passe en couleur automatiquement, sans avoir eu à redemarrer la machine.
**4)** On souhaite modifier l’invite de commande pour qu’elle s’aﬀiche sous la forme suivante : l’heure en violet et entre crochets, le chemin du dossier courant en cyan.
Pour ce faire on utilise les commandes suivantes :
*vim .bashrc* // Ouvre le fichier avec vim.
*I*// Pour pouvoir écrire dedans
On modifie la premiere ligne PS1 comme suit :
PS1 = '\${debian_chroot:+(\$debian_chroot)}\[\033[01;323m\]\u@\h\[\033[00m]:\[\033;34m\]\w\[\033[00m\]\$
*echap:wq* // Enregistre et quitte vim.

