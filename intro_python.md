# Programmation avec Python

Si vous voulez approfondir le cours, vous pouvez lire le [cours de Python de Clément Delgrange](Cours_Python.pdf) qui rentre dans beaucoup de détails et dont cette page est un extrait.

## Introduction

Ce cours est une initiation au langage de programmation Python. Il n'est pas nécessaire de déjà connaître ce langage, ni d'avoir des notions avancées en programmation, pour pouvoir l'aborder. Dans la mesure du possible, chaque notion est illustrée d'exemple. Le cours se concentre sur la description du fonctionnement du langage et des syntaxes employées.

La version 3 de Python est la seule utilisée tout au long du cours.

Pour installer Python chez vous, il peut être pratique d'installer [Anaconda](https://www.anaconda.com/distribution/), ce qui permet d'avoir un environnement semblable à celui de l'école, avec notamment Spyder comme [IDE](https://fr.wikipedia.org/wiki/Environnement_de_d%C3%A9veloppement) pour profiter des fonctionnalités vues en cours.

On choisira le package pour la version 3 de Python (3.7 au moment de l'écriture de ce texte) qui correspont à notre système d'exploitation.

## Types et opérations

Ce chapitre va nous permettre de commencer à utiliser le langage Python. Nous nous limiterons pour commencer à des opérations basiques comme des opérations mathématiques ou des manipulations de chaînes de caractères. Plus précisément, nous nous limiterons dans ce chapitre aux opérations sur des types de base définis dans le langage.


Avant cela, nous définirons ce que sont une variable et un type en informatique. Nous introduirons un concept important en Python, le typage dynamique, et montrerons comment sont gérées données dans ce langage.


### Variables et types en Python
#### Généralités
La programmation consiste essentiellement à manipuler des données. Ces données de natures diverses sont stockées sous forme binaire dans la mémoire de l'ordinateur. Pour y accéder, un programme définit des __variables__.


Nous définirons ainsi une variable comme l'association d'un nom et d'une valeur. Le nom est utile au programmeur pour savoir quelle donnée il manipule, tandis que l'ordinateur utilise la valeur associée. De manière imagée, le nom peut être vu comme une simple étiquette sur une donnée.


En Python, le nom (on parle parfois d'identificateur) :
  + ne peut contenir que des lettres, des chiffres et des blancs soulignés;
  + ne peut pas contenir d'espace ou de caractères spéciaux (&, ;...);
  + ne peut pas commencer par un chiffre; 
  + distingue minuscules et majuscules (on dit que le langage est sensible à la casse); 
  + doit être unique. Par convention, pour les noms de variable, on séparera les mots par des blancs soulignés : mon_nom_de_variable. Les noms de variable commençant par deux _ et se terminant par deux _ sont réservés au langage (exemple : __str__). Certains mots-clé sont également réservés par le langage. Il n'est pas possible de créer une variable portant l'un de ces noms : `and else in return as except is true assert false lambda try break finally none while class for nonlocal with continue from not yield def global or del if pass elif import raise` ([liste exhaustive sur la documentation officielle](https://docs.python.org/3.3/reference/lexical_analysis.html#keywords))


En Python, la valeur d'une variable est une référence vers une adresse mémoire (un emplacement précis dans la mémoire vive de l'ordinateur). Le contenu de la variable est stocké à cette adresse mémoire sous forme d'une suite de nombres binaires. Pour distinguer les différents contenus, les langages de programmation utilisent des types de variable qui permettent de spécifier le contenu attendu.

Contrairement à d'autres langages, il n'est pas nécessaire de déclarer le type d'une variable avant de pouvoir l'utiliser. Plus précisément, l'interpréteur Python détecte lui-même le type de l'objet en référence lorsque la variable est utilisée dans une expression.

Par exemple, lorsque l'on écrit `x = 3`, on crée une variable `x` à laquelle on associe l'objet 3 qui est stocké dans la mémoire de l'ordinateur. L'interpréteur Python détecte que 3 est un nombre entier et associe donc ce type à la variable `x`.

À retenir :
 + une variable est créée lorsqu'on lui affecte pour la première fois une valeur; 
 + une variable n'est jamais associée à un type en Python. C'est l'objet qu'elle référence qui porte le type; 
 + une variable est automatiquement remplacée par l'objet qu'elle référence dans une expression.


#### Types de base
Python met à disposition du programmeur un certain nombre de types ou structures de données. On parle de types intégrés (builtins). Il est également possible de définir ses propres structures de données.

Quel est donc l'intérêt d'utiliser les structures de données intégrés au langage ? Tout d'abord, nous remarquerons que ces types de base sont des composants naturels des structures manipulées dans les programmes (on manipule naturellement des entiers, des chaînes de caractères). Cela facilite donc grandement la programmation : il n'y a pas besoin de tout redéfinir pour chaque nouveau programme. Enfin, ces structures de données sont plus effcaces que des structures de données que l'on aurait reconstruites (les algorithmes ont été optimisés, écrit dans des langages performants comme le C).

| Type | Exemples de valeur |
| Nombre | 3, 1.1456, -3.5 |
| Chaîne de caractères | 'mot', 'petit texte' |
| Liste | [1, 2, 3], ['a', 'b'], ['a', 5, 2.3, 'f'] |
| Tuple | (1, 3), ('a', 'b', 'c') |
| Ensemble | set('abc'), 'a', 'b', 'c' |
| Dictionnaire | 1 :'a', 2 :'b'  |
| Fichier | open('fichier.txt') |
| Booléen | True, False |
| Rien | None |


### Les types numériques

Les nombres sont des objets relativement basiques et dont l'utilisation est assez naturelle. Python inclus les types numériques "classiques", que l'on retrouve dans la plupart des langages de programmation : nombres entier, nombres à virgule; mais également d'autres moins courants : nombres complexes, nombres rationnels. Ces types couvrent la plupart des besoins standards.

| Type | Exemple de valeur |
| Integer | 2, -3, 156235789 |
| Float | 2.3, -4.12, 1.0, 189489.23891 |
| Complex | 2 + 3j |
| Decimal | Decimal('0.1') |
| Fraction | Fraction(1, 3) |


Les nombres Python supportent les opérations mathématiques classiques listées dans la table c-dessous. Dans le cas d'expression avec des parenthèses, Python applique la règle mathématique classique et calcule en premier les sous-expressions entre parenthèses.

| Opérateur | Signification |
| \+ | Addition |
| \- | Soustraction |
| \* | Multiplication |
| ** | Puissance |
| / | Division |
| // | Division entière |
| % | Reste d'une division entière (modulo) |

On pourra convertir un nombre quelconque en nombre entier via la fonction `int()` ou en nombre réel via la fonction `float()`

### Les booléens


### Le type 'rien'

### Les chaînes de caractères

### Les listes

### Les dictionnaires

### Les fichiers

## Syntaxe du langage


## Modules et fonctions



## Documentation et tests