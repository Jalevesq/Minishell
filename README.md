# Minishell

Le repo actuel contient un README en anglais, mais une version française est disponible sur le repo original, situé sur le compte GitHub de mon coéquipier : https://github.com/EthanPasquier/minishell.

## Introduction

Le projet Minishell de l'école 42 consiste en la création d'un programme de shell simplifié en langage C. L'objectif de ce projet est de comprendre le fonctionnement d'un shell et de mettre en pratique les connaissances en manipulation de processus et en gestion de fichiers (fd).

## Répartition des tâches

- Parsing : réalisé par mon coéquipier Ethan Pasquier
- Exécuteur & Builtins: réalisé par moi-même

## Fonctionnalités

- Lecture des commandes de l'utilisateur. (Main)
- Gestion des erreurs de saisie d'utilisateur. (Parsing)
- Lancement des exécutables (en utilisant les chemins relatifs et absolus ainsi que la variable d'environnement PATH). (Exécuteur)
- Gestion de l'historique des commandes. (Main)
- Gestion des variables d'environnement (substitution de la variable d'environnement $ par sa valeur). (Parsing)
- Implémentation des builtins (Exécuteur) :
  - echo avec l'option -n.
  - cd uniquement avec un chemin relatif ou absolu.
  - pwd sans aucune option.
  - export sans aucune option.
  - unset sans aucune option.
  - env sans aucune option ni argument.
  - exit sans aucune option.
- Gestion des redirections (<, >, >>, <<). (Exécuteur)
- Gestion des pipes (|). (Exécuteur)
- Gestion des signaux (ctrl-C, ctrl-D, ctrl-\\). (Main)
- Support des single quotes (') qui empêchent l'interprétation des méta-caractères dans la séquence entre guillemets. (Parsing)
- Support des double quotes (") qui empêchent l'interprétation des méta-caractères dans la séquence entre guillemets sauf pour le signe dollar $. (Parsing)
- Support de la substitution de $? par le statut de sortie de la dernière commande exécutée au premier plan. (Parsing)
## Utilisation
1. Cloner le dépôt :
   ```
   git clone https://github.com/Jalevesq/Minishell
   ```
2. Compiler le programme (le Makefile télécharge automatiquement la librairie Readline nécessaire pour le bon fonctionnement du programme) :
   ```
   make
   ```
   *Note : Veuillez noter que le téléchargement et la compilation de la librairie Readline peuvent prendre un certain temps, en fonction de votre connexion internet et des performances de votre ordinateur. Si vous rencontrez des problèmes lors du téléchargement ou de la compilation, vous pouvez réessayer en exécutant à nouveau la commande make ou make re.
3. Lancer le shell :
   ```
   ./minishell
   ```
4. Utiliser le shell en tapant des commandes standard ou en utilisant les fonctionnalités spécifiques.
## Fonctionnement
Le programme se décompose en plusieurs fichiers source :
1. `main.c` : contient la boucle principale du programme qui gère la saisie, l'exécution et l'affichage des résultats.
2. `parsing.c` : contient les fonctions qui traitent les commandes saisies par l'utilisateur et les séparent en arguments, redirections, pipes, etc.
3. `execution.c` : contient les fonctions qui exécutent les commandes et gèrent les redirections, les pipes et les signaux.
4. `builtins.c` : contient les fonctions qui gèrent les commandes spécifiques au shell (comme `cd`, `env`, `echo`, etc.).
5. `signals.c` : contient les fonctions qui gèrent les signaux.
## Conclusion
Minishell est un projet intéressant pour se familiariser avec la programmation en C et la manipulation de processus. Il est également utile pour comprendre le fonctionnement d'un shell et les fonctionnalités de base telles que l'environnement système, les redirections et les pipes.
