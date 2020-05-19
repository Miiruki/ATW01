
Pour Installer la base de nedit : Aller sur le site officiel et télécharger le tar.gz correspondant à nedit

Ensuite le décompresser avec tar -xvzf

Une fois dans le dossier, faire un make linux.

Et la, c'est balo, il manque des librairies, pas de soucis on va les installer.

Rechercher la librairie sur google (packages.debian.org c'est cool pour ca), ensuite on installe la librairie avec un wget.

Le problème maintenant, c'est que le Makefile ne vas pas chercher les librairies au bon endroit, donc on va aller le modifier pour qu'il n'y est plus de problème : 

CFLAGS=-O -I/usr/X11R6/include -I /home/atw01/.env/usr/include -DUSE_DIRENT -DUSE_LPR_PRINT_CMD

LIBS=-L/usr/X11R6/lib -L /home/atw01/.env/lib/ -lXm -lXt -lX11 -lm

Il va maintenant chercher les librairies et les includes dans /home/atw01/.env/

----------------------------------------------------------------------------------------------------------------------------------------

ATTENTION AU VERSIONS DES FICHIERS CA PEUT POSER PROBLEME

En cas de Probleme : ln -s nom_du_fichier_buguer nom_du_bon_fichier ( on crée juste un lien symbolique entre les deux fichiers ) 

----------------------------------------------------------------------------------------------------------------------------------------

Pour changer la variable d'environnement : LD_LIBRARY_PATH ----> export LD_LIBRARY_PATH=/home/atw01/.env/usr/lib/

Pour la mettre direct dans le bashrc --> echo "export LD_LIBRARY_PATH=/home/atw01/.env/usr/lib" >> ~/.bashrc

 
