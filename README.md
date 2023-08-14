# Minishell

Le dépôt actuel comprend le fichier README de l'exécuteur. Si vous souhaitez obtenir des informations sur le parsing, je vous recommande de consulter le compte GitHub de mon coéquipier, accessible via ce lien : https://github.com/EthanPasquier/minishell.

## Introduction

Le projet Minishell de l'école 42 consiste en la création d'un programme de shell simplifié en langage C. L'objectif de ce projet est de comprendre le fonctionnement d'un shell et de mettre en pratique les connaissances en manipulation de processus et en gestion de fichiers (fd).

## Répartition des tâches

- Parsing : réalisé par mon coéquipier [Ethan Pasquier](https://github.com/EthanPasquier)
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
2. Compiler le programme (avec l'aide de curl, le Makefile télécharge automatiquement la librairie Readline nécessaire pour le bon fonctionnement du programme) :
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

```
.
├── include
├── libft
├── srcs
│   ├── built
│   ├── exec
│   ├── main
│   ├── parsing
│   └── tools
└── Makefile 
```

### Parsing
Réalisé par [@EthanPasquier](https://github.com/EthanPasquier)
- [Parsing](https://github.com/EthanPasquier/minishell)
### Exécuteur
Réalisé par [@Jalevesq](https://github.com/Jalevesq)

Ceci est mon tout premier gros projet en C. Si je devais le refaire, il y aurait certainement des ajustements à faire, notamment au niveau des fonctions intégrées (builtins) et de la gestion des heredocs. L'expérience forge la progression !
