# Minishell

Le repo actuel contient un README en anglais, mais une version française est disponible sur le repo original, situé sur le compte GitHub de mon coéquipier : https://github.com/EthanPasquier/minishell.

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
- ....
### Exécuteur
Réalisé par [@Jalevesq](https://github.com/Jalevesq)

L'exécuteur (ft_executor) reçoit une liste chaînée contenant toutes les informations nécessaires pour l'exécution. Chaque nœud de la liste contient une chaîne de caractères et un entier qui définit le type de nœud (voir parsing).

En utilisant cette liste, plusieurs variables sont initialisées, telles que le nombre de pipes, le nombre de processus enfants, le chemin d'accès des commandes, etc. Ces variables sont définies dans la fonction ft_command.

- Après l'initialisation des variables, le programme prépare le nombre de child process et le nombre de pipe qu'il y a.
Au départ, le nombre de processus enfants était défini par le nombre de commandes. 
```
pid = (pid_t *)malloc(sizeof(pid_t) * (child->cmd_nbr));
```
- Cependant, j'ai réalisé que lorsque l'entrée ne contenait pas de commandes:
```
> abc
```
Elle devait être exécutée dans un processus enfant car les fonctions de redirection sont dans les fonctions de processus enfant. J'ai donc modifié le code pour que le nombre de processus enfants soit égal au nombre de pipes plus un (+1 pour quand il n'y a pas de pipe).
```
pid = (pid_t *)malloc(sizeof(pid_t) * (child->pipe_nbr + 1));
```
- Ensuite, toujours dans la fonction ft_command, si des pipes sont présents, un tableau de pipes est défini pour être utilisé dans les processus enfants. Vous pouvez trouver plus d'informations sur le fonctionnement de ce tableau de pipes dans le code source, en particulier dans les fichiers executor.c et exec_utils.c.

- Lorsque tout est initialisé, la fonction ft_exec_command est appelé. Cette fonction va itérer à travers la liste chaîné et lancer un child process lorsque la variable i est égale à 0 ou lorsque que le type de la node est égale à "PIPE". Pour les redirections, chaque "groupe de commande" est analysé de gauche à droite. Pour le STDOUT, si il y a une redirection, Dup2 sera effectué qu'une seule fois sur la redirection (>) le plus à droite ou sur le pipe si aucun ">". Pour le STDIN,
## Conclusion
Minishell est un projet intéressant pour se familiariser avec la programmation en C et la manipulation de processus. Il est également utile pour comprendre le fonctionnement d'un shell et les fonctionnalités de base telles que l'environnement système, les redirections et les pipes.
