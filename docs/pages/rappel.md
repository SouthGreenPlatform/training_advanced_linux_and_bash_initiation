# Rappel Commandes de Base

![](img/survival_kit.png){: style="height:200px;width:200pxt"}

## Commands 

!!! note
    * `pwd`	Affiche le chemin (où je suis)
    * `ls -alrt`	Liste le contenu d’un répertoire 
    * `cd`		Change de répertoire

!!! note
    * `mkdir`	Crée un répertoire
    * `rmdir`	Supprime un répertoire vide	
    * `rm`		Supprime un fichier
    * `rm -r` 	Supprime répertoire &  fichiers
    * `cp <source> <cible>`	Copie/renomme 
    * `mv` 		Déplace un fichier/répertoire 

!!! note
    * `cat`			Affiche fichier (court)
    * `less` 		Affiche fichier (long)
    * `head/tail`	Affiche début/fin fichier
    * `wc -l` 		Compte nombre de lignes

!!! note
    * `(z)grep -icv`	rechercher un motif
    * `cut	-d -f`		Extrait colonnes d‘un fichier
    * `sort	-t -kgr`    Trie une colonne d’un fichier
    * `uniq	`       Garder les valeurs uniques

!!! note
    * `chmod`	Change les droits
    * `chown`	Change le propriétaire
    * `chgrp`	Change le groupe

!!! note
    * `history`			zcat, zgrep	
    * `tar / gzip`	Compresser, Décompresser
    * `df -h`			
    * `du -sh`
    * `wget`			
    * `ln -s`
 
!!! note
    * `find`    recherche d'un fichier

## Caractères joker 

* `*`       N’importe quel caractère
* `[sb]`	Caractère de l’ensemble

## Redirection Entrés/sorties

* `>`       vers un fichier (overwrite)
* `>>`		vers un fichier (append)
* `|`		vers une commande

## Interagir avec les processus

`<Ctrl> + C`	Arrêter le processus en cours sous le terminal

## Tab completion

* `<Tab>`	Complète automatiquement le nom d’un fichier/	répertoire qui est en 
cours de saisie (choix unique)
* `<Tab><Tab>` 	Affiche la liste des différentes possibilités si le choix n'est pas unique

## Interagir avec l’historique de commandes

* `Flèche bas/haut`	Afficher la commande précédente/suivante. Presser plusieurs fois pour naviguer dans l’historique

* `<Ctrl> + R`  	Afficher la dernière commande qui contient les caractères saisis. Presser les touches et commencer à taper la commande recherchée

## Nomenclature fichiers

 * Linux = sensible à la casse
 * PAS d’espaces, accents et caractères spéciaux  ``` & ~ # ”  ' { ( [ | ` \ ^ @ ) ] } $ * % ! / ; , ?```
 * Suffixe des noms de fichiers (.txt, . fasta, .fa, .fq etc.) optionnel
