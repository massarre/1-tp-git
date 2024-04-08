B1-Git - Partie 1 : Création du dépôt et commits
Ouvrir un terminal (terminal Git Bash à privilégier)


1
Créer, en ligne de commande, un répertoire tp-git
mkdir tp-git1


2
Se déplacer dans le répertoire
cd 1-tp-git

3
Vérifier qu'on est dans le bon répertoire en affichant le chemin du répertoire courant
pwd

4
Initialiser un dépôt Git
git init

5
Lister tous les fichiers du répertoire (y compris les fichiers cachés) pour s'assurer que le répertoire .git à été créé
ls -a

6
Ouvrir ce répertoire sous VS Code
code .

7
Exécuter git status et copier/coller la sortie
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)

Cette sortie signifie que sur la branche master  il n’y a pas de commit et dailleurs rien à committer


8
Créer le fichier fichier1.md avec un contenu quelconque et l'enregistrer (vous pouvez utiliser VS Code pour créer et éditer des fichiers)

Attention, il s'agit bien de créer un nouveau fichier, et non un répertoire. Il en sera de même tout au long de ce TP.

touch fichier1.md
nano fichier1.md


9
Créer le fichier fichier2.md avec un contenu quelconque et l'enregistrer

touch fichier2.md
nano fichier2.md


10
Exécuter git status et copier/coller la sortie

On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier1.md
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)

Explication : 
Sur la branche master il n’y a pas de commit mais il y a deux fichiers (fichier 1 et 2) qui sont pas suivis. Il faut utiliser git add pour les ajouter dans la zone index.


11
Ajouter fichier1.md à l'index de Git (zone de Staging)
git add fichier1.mdgit 

12
Exécuter git status et copier/coller la sortie


On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

Explication : Contrairement au fichier 2, le fichier 1 est ajouté dans la zone index mais non validé.

13
Créer un commit avec pour message : "Ajout de fichier1.md"

git add fichier2.md  d’abord
git commit -m "Ajout de fichier1.md"




VALIDATION PROF01

1
Exécuter git status et copier/coller la sortie

git status

On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

nothing added to commit but untracked files present (use "git add" to track)

explication : Il n’y a rien à committer sur la branche principale

2
Modifier fichier1.md et enregistrer

nano fichier1.md 

3
Exécuter git status et copier/coller la sortie

git status

On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   fichier1.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        fichier2.md

no changes added to commit (use "git add" and/or "git commit -a")

Explication : sur la branche mère, aucune modification n’est pas prévue pour committer. 
Le fichier1 se trouvant dans la zone index est modifié mais la nouvelle version n’y est pas. 



4 
Ajouter fichier1.md et fichier2.md à la zone de Staging

git add fichier1.md
git add fichier2.md

5
Créer un commit "Ajout de fichier2.md et modification de fichier1.md"

git commit -m "Ajout de fichier2.md et modification de fichier1.md"





6
Exécuter git status et copier/coller la sortie

git status

On branch master
nothing to commit, working tree clean


7
Copier/coller l'ID des deux premiers commits (utiliser log) :

ID commit 1 : de7c44da95a0d2698c51e569122bb58494b8f4dd 
ID commit 2 : 83886196372fc7bfa871473d1308259e9da08494


Que signifie qu'un fichier est "tracked" ou "untracked" ?

Un fichier untracked signifie que le fichier en question est ajouté dans le dépôt git mais n’est pas ajouté à l’index est considéré donc il n’est pas non suivi. 
Quant au fichier tracked signfie le fichier en question est ajouter dans la zone d’indexation et qu’il est suivi c'est à dire git garde un œil sur evolution.

Pourquoi doit-on passer les fichiers par la zone de Staging (l'index) avant de les committer ?

La zone de standing est une zone intermédiaire entre le dépôt local et le dépôt distant. Il permet de préparer et d’organiser les modifications des données avant de les enregistrer dans l’historique du projet avec un commit, de vérifier toutes les modifications avant de les committer afin d'éviter les erreurs etc


B1-Git - Partie 2 : Gestion de branches
Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite.

1
Créer une branche fonctionnalité 1
git branch fonctionnalité 1

2
Lister les branches
git branch

3
Se déplacer sur la branche fonctionnalité 1
git checkout fonctionnalité 1

4
Lister les branches
git branch

5
Que représente l'étoile à côté des noms des branches ?

Cette étoile montre montre la branche sur laquelle l'utilisateur se trouve. 

6
Créer un nouveau fichier fichier3.md
nano fichier3.md

7
Modifier le fichier fichier2.md
nano fichier2.md

8
Comment utiliser VS Code pour qu'il nous montre les différences entre l'ancienne version de fichier2.md et la version courante que l'on vient d'éditer ?

- Taper sur le terminal bash pour ouvrir VS code : code .
- Se rendre dans VS code
- Sur les onglets sur qui se trouvent en haut du coin gauche, tapez sur le troisième nommé : contrôle de code source 
- Enfin taper sur le fichier qu’on souhaite voir ses modifications


10
Committer ces deux modifications : "Fonctionnalité 1 - première phase"

d’abord l’indexer en taper git add fichier fichier3.md 

11
Créer un nouveau fichier fichier4.md
touch fihcier4.md

12
Modifier de nouveau le fichier fichier2.md
nano fichier2.md

13
Committer ces deux modifications : "Fonctionnalité 1 - terminée"

git add fichier4.md dabord
git commit -m "Fonctionnalité 1 - terminée"

VALIDATION PROF 03


1
Afficher la liste des fichiers du répertoire
ls 

2
Se déplacer sur la branche master
git checkout master

3
Afficher la liste des fichiers du répertoire
ls 
fichier1.md  fichier2.md 

4
Pourquoi les deux sorties sont-elles différentes ? Les fichiers ont-ils disparus ?
Les deux sorties sont différentes parce que les branches sont indépendantes l’une de l’autre.
Non, les fichiers ne sont pas disparus.

5
Créer une nouvelle branche fonctionnalité 2
git branch fonctionnalité 2

6
Cette branche ne va pas avoir toutes les données incluses dans fonctionnalite 1. Pourquoi ?
Cela s'explique par le fait qu’elles soient créées de manière séparées sur la branche principale master.


Qu'aurait-il fallu faire si on avait souhaité démarrer la branche fonctionnalité 2 en intégrant les modifications récentes de fonctionnalité 1 ?
Pour quoi cela soit possible il fallait les fusionner en tapant git merge fonctionnalité 1 tout en se déplaçant d’abord dans la fonctionnalité 1


7
Se déplacer sur la nouvelle branche fonctionnalité 2

git checkout fonctionnalite2

8
Créer un nouveau fichier fichier5.md
touch fichier5.md

9
Faire un commit intégrant cette ajout : "Ajout fichier5.md"
git add fichier5.md d’abord
git commit - m "Ajout fichier5.md"

10
Entrer la commande git log --oneline --decorate --graph --all pour visualiser, sur le terminal, le graphe des commits sur toutes les branches

Les branches fonctionnalités 1 et 2 sont précédées par un asterix et des chiffres et des lettres de la même manière que la branche principale master (identifiant, peut-être). Elles sont en parallèle avec cette dernière. La déviation est marqué par un slash. 

11
Installer l'extension VS Code Gitgraph et visualiser le graphe actuel des commits à l'aide de cette extension
 

Sur cette représentation, que représente les points ?
ils représentent les branches

Les points représentent les commits qui sont réalisés.

13
Comment voit-on sur quelle branche on est actuellement ?
Quand on voit que la branche est entourée par une couleur bleue et qu’il y a un petit rond devant elle. 

VALIDATION PROF04

Partie 3 - Fusionner des branches
Cette partie est à faire sur le même dépôt que la partie précédente. C'est la suite.
On considère que la branche originale (master ou main) est la branche d'intégration, c'est-à-dire celle qui va contenir l'historique de toutes les modifications développées au fur et à mesure dans les branches annexes
Se déplacer sur la branche master
git checkout master

Noter le changement dans l'onglet Gitgraph
On constate que la branche fonctionnalité 1 s’est détachée de la branche principale. ensuite ses modifications sont marquées par des pointillés.
Or la branche fonctionnalité 2 est la sur même ligne que la branche principale.

On va maintenant intégrer la branche fonctionnalité 1, qui est terminée, dans la branche d'intégration (ça s'appelle une fusion, ou un merge) : fusionner avec la branche fonctionnalité 1
se déplacer d’abord sur la branche principale
git merge fonctionnalité 1

git merge fonctionnalite1

Noter le changement dans l'onglet Gitgraph. Que signifie la mention Fast-forward indiquée par la sortie de la commande ?

Updating 9ed91f8..5866ba6
Fast-forward
 fichier2.md | 4 +++-
 fichier3.md | 0
 fichier4.md | 0
 3 files changed, 3 insertions(+), 1 deletion(-)
 create mode 100644 fichier3.md
 create mode 100644 fichier4.md


La mention Fast-forward dans Git indique qu’il n’y a pas eu de divergence entre la branche que vous fusionnez et la branche de réception.
De surcroît cela signifie que les commits de fonctionnalité 1  seront simplement ajoutés à master, et que ce dernier sera mis à jour pour les prendre en compte

On constate que les branches master et fonctionnalité1  sont cote à cote




On veut maintenant fusionner fonctionnalité 2 dans la branche d'intégration (master). Effectuer cette fusion.
git merge fonctionnalité 2

Noter le changement dans l'onglet Gitgraph. Que signifie la mention Merge made by the ... strategy indiquée par la sortie de la commande ?
Merge made by the 'ort' strategy.
 fichier5.md | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 fichier5.md

La mention “Merge made by the … strategy” fait référence à la stratégie de fusion utilisée lors d’une opération de fusion (merge) dans Git. Git propose plusieurs stratégies de fusion dont : ort ; theirs ; ours. Et dans ce cas présent celui utilisé est ort.

Quelle est la différence fondamentale avec la fusion précédente ?
Dans la première fusion la branche fonctionnalité1 et celle master étaient au même niveau. La branche fonctionnalite1 ne s’est ralliée vers la branche principale. 


Quant à la deuxième fusion, la branche fonctionnalite2 se rallie c'est-à- dire se courber à la branche master. 


Créer une nouvelle branche fonctionnalité 3, se déplacer dessus, et modifier le fichier fichier1.md en y ajoutant une ligne de texte. 

Committer : "Modification fichier1 pour fonctionnalité 3"

git branch fonctionnalite3
git checkout fonctionnalite3
nano fichier1.md
git add fichier1.md
git commit -m "Modification fichier1 pour fonctionnalité 3"

Comment utiliser Git Graph pour qu'il nous montre les différences entre l'ancienne version de fichier1.md et la version courante que l'on vient de committer ?

Se rendre dans VS code
se diriger en haut en gauche et taper le premier onglet nommé explorateur
taper le  fichier1.md
taper sur Git Graph


Repartir sur master, et modifier fichier1.md en y ajoutant aussi une ligne (différente de celle qu'on a ajoutée sur l'autre branche) ; ajouter à l'index et commit

git checkout master
nano fichier1.md (ecrire quelque chose pour apporter une modifiction)
git add
git commit -m “modification du fichier1.md" 

Tenter de fusionner la branche fonctionnalité 3 avec master
git checkout master
git merge fonctionnalite3

Auto-merging fichier1.md
CONFLICT (content): Merge conflict in fichier1.md
Automatic merge failed; fix conflicts and then commit the result.


Que se passe-t-il et pourquoi ?
error: you need to resolve your current index first
fichier1.md: needs merge

Cette erreur s’explique par le fait que le même est modifié dans les branches concernées différents

Lancer un git status
git status

On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)


Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   fichier1.md


no changes added to commit (use "git add" and/or "git commit -a")


Que doit-on faire si on veut annuler la fusion en cours ? (ne pas lancer la commande)
 Utilisez la commande git merge --abort 

On veut résoudre le conflit. Plusieurs possibilités :
Conserver uniquement les modifications faites dans fonctionnalite 3
Conserver uniquement les modifications faites dans master
Conserver les deux modifications
Supprimer les deux modifications ou remanier sensiblement le fichier pour les intégrer correctement

Git nous laisse totalement la main et ne va pas essayer d'imposer l'un de ces choix pour nous, ni nous assister dans l'application automatique de l'un d'entre eux : il faut examiner le(s) fichier(s) en conflit et éditer nous-mêmes

Ouvrir le fichier en question sous VS Code
La chaîne <<<<<<<<<< marque le début du conflit
La chaîne >>>>>>>>>> marque la fin du conflit
La chaîne ========== sépare les deux versions

Éditer le fichier pour faire en sorte d'intégrer les deux modifications ; à la fin de l'édition :
I
nano fichier1
supprimer les caractères spéciaux (traits..etc)

Sauvegarder


Ajouter les modification à l'index et committer

git add fichier1.md
git commit -m “Suppression des signes dans fichier1”


Supprimer les trois branches fonctionnalités (attention : on ne peut pas supprimer une branche sur laquelle on est)
git branch -d fonctionnalité1 fonctionnalité2 fonctionnalité3

VALIDATION PROF05


