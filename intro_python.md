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

Une variable de type booléen ne pourra prendre que deux valeurs : `True` (vrai) et `False` (faux).

Les opérations logiques retournent des booléens. La table suivante liste les opérateurs de comparaison. Ces opérateurs s'appliquent à tous les types de données, à condition que les types soient comparables (comparer 5 à "toto" n'a pas vraiment de sens).


| Opérateur | Signification |
| \> | Supérieur |
| < | Inférieur |
| \>= | Supérieur ou égal |
| <= | Inférieur ou égal |
| == | Egal |
| != ou <> | Différent de |
| is | Objet identique |
| is not | Objet différent |

Dans l'exemple ci-dessous, nous affectons à `x` le résultat de la comparaison `3 != 5`. Ce résultat est un booléen :
```python
>>> x = (3 != 5)
>>> x 
True
```

Le booléens peuvent être combinées entre eux à l'aide des mots clé `and`, `or` et `not`.

Mini-exo : table de vérité


### Le type 'rien'

Python propose un type spécial qui ne peut prendre qu'une seule valeur possible, `None`, et qui est utilisé pour signifier qu'une variable ne contient rien. Ou plus exactement, elle référence un objet et cet objet est l'objet "rien".

Il s'agit d'une valeur qui est utilisée par défaut lorsqu'une opération n'a pas de retour explicite ou n'a pas pu être menée à son terme. Le type "rien" est ainsi utilisé pour vérifier que des parties de programme ont correctement fonctionné.


### Les chaînes de caractères

#### Création d'une chaîne de caractères

Les apostrophes et guillemets s'utilisent indifféremment pour définir une chaîne de caractères `"..."` ou `'...'`.


L'intérêt d'utiliser l'une ou l'autre des deux formes est de pouvoir intégrer des apostrophes ou guillemets dans une chaîne :
```python
"aujourd'hui", 'le type "rien"'
```

Le caractère d'échappement dans une chaîne de caractères est le backslash `\`.
```python
'aujourd\'hui'
```

Python propose un troisième mode de définition de chaînes de caractères qui commence et se termine par trois guillemets : `"""..."""`. Cette syntaxe permet de conserver la mise en forme d'un bloc de texte.
```python
 """Les trois quotes : permettant d'enregistrer la mise en forme.

=> y compris les sauts de ligne
, les tabulations..."""
```

#### Manipulation de chaînes de caractères

Les opérateurs suivants sont applicables aux chaînes de caractères.

| Opérateur | Signification |
| \+ | Concaténation de chaînes de caractères |
| \* | Répétition d'une chaîne de caractères |
| `in` | Inclusion d'une chaîne dans une autre |
| `not in` | Non inclusion d'une chaîne dans une autre |
| `[i]` | Caractère à la i-ième position dans la chaîne |
| `[i:j]` | Caractères compris entre les i-ième et j-ième positions |

De plus, on peut appliquer de nombreuses fonctions aux chaînes de caractères, qui sont décrites dans [la documentation officielle](https://docs.python.org/3/library/stdtypes.html#string-methods)


### Les listes

Une liste est un tableau d'objets qui peuvent être de n'importe quel type. Il est possible de modifier, ajouter ou supprimer des éléments d'une liste sans avoir à la redéfinir.

Une liste est définie par un ensemble de valeurs entre deux crochets :
```python
>>> a = [2016, "ENSG", 'Géomatique']
>>> type(a)
<class 'list'>
>>> a
[2016, 'ENSG', 'Géomatique']
```

Les listes peuvent également être imbriquées :
```python
>>> b = [a, [1, 2, 3, 4]]
>>> b
[[2016, 'ENSG', 'Géomatique'], [1, 2, 3, 4]]
```

Pour créer une liste vide, nous utilisons des crochets sans rien à l'intérieur :
```python
>>> c = []
>>> type(c)
<class 'list'>
```

Les listes supportent les opérateurs suivants :

| Opérateur | Signification |
| x in s | x est dans s |
| x not in s | x n'est pas dans s |
| s + t | concaténation de s et t |
| s * n | ajouter n fois s à lui-même |
| s[i] | élément à la i-ème position |
| s[i:j] | sous-liste de s, de la i-ème à la (j-1)-ème position |
| s[i:j:k] | sous-liste de s, de la i-ème à la (j-1)-ème position avec un pas de k |
| len(s) | nombre d'éléments de la liste s |
| min(s) | plus petit élément de la liste s (lorsque cela à un sens) |
| max(s) | plus grand élément de la liste s (lorsque cela à un sens) |
| sum(s) | somme des éléments de la liste s (lorsque cela à un sens) |
| s.index(x, i, j) | index de la première occurence de x dans s, à partir de l'indice i et jusqu'à j |
| s.count(x) | nombre d'occurence de x dans s |
| L[i] = x | Elément à la position i remplacé par x |
| L[i:j] = t | Partie entre les position i et j remplacé par la liste t |
| del(L[i:j]) | Suppression des éléments entre les positions i et j. Equivalent à L[i:j] = [] |
| L[i:j:k] = t | Partie entre les position i et j avec un pas de k remplacé par la liste t |
| del(L[i:j:k]) | Suppression des éléments entre les positions i et j avec un pas de k. Equivalent à L[i:j:k] = [] |
| L += t | Ajoute t à L |
| L *= n | Ajoute n-1 fois L à elle-même |

De plus, les listes implémentent un certain nombre de de fonctions, en voici quelques-unes :
+ `l.append(x)` : Ajoute l'élément x à la fin de la liste l
+ `l.reverse()` : Inverse l'ordre des éléments de la liste
+ `l.pop(i)` : Retourne et supprime de la liste l'élément à la position i 
+ `l.insert(i, x)` : Insertion de l'élément x à la position i

D'autre fonctions existent, à l'aide d'un IDE une liste est disponible.


### Les dictionnaires

Les dictionnaires sont des objets semblables aux listes mais plus souples en ce qui concerne le référencement des valeurs. Alors qu'une liste référence les éléments qu'elle contient à l'aide de leur position (un entier compris entre 0 et la taille de la liste), un dictionnaire se contente d'associer l'élément à __un autre élément de type immuable__ (entier, réel, chaîne, tuple). On dit que le dictionnaire __associe une valeur à une clé__.

Les éléments d'un dictionnaire ne sont pas ordonnés (il n'est pas possible de les trier) et on y accède uniquement par leurs clés. La structure d'un dictionnaire n'est pas figée, on peut ajouter/modifier/supprimer des éléments sans avoir besoin de recréer le dictionnaire : le dictionnaire est modifiable.

La syntaxe de création d'un dictionnaire est la suivante :
```python
>>> dico = {cle1: valeur1 , cle2: valeur2...}
```

On peut créer un dictionnaire vide :
```python
>>> dico = {} >>> dico = dict()
```

Pour accéder à la valeur d'un élément, la syntaxe est semblable à celle d'une liste, mais l'indice n'est plus uniquement un entier : `dico[cle]` retourne la valeur associé à la clé.
```python
>>> dico = {'prenom': 'paul', 'age': 24} >>> dico['prenom'] 'paul'
```

L'ajout d'une nouvel élément est assez aisé :
```python
>>> dico[0] = 'rouge' >>> dico {0: 'rouge', 'age': 24, 'prenom': 'paul'}
```

Les dictionnaires implémentent aussi un certain nombre de fonctions, dont en voici quelques unes :
+ `d.items()` : retourne une séquence des couples (clé, valeur) du dictionnaire
+ `d.keys()` : retourne une séquence des clés du dictionnaire
+ `d.values()` : retourne une séquence des valeurs du dictionnaire


### Les fichiers

Dans ce paragraphe, nous nous attarderons sur le dernier type de base qui sera présenté dans ce cours : les fichiers. Nous montrerons comment lire ou écrire dans un fichier.

#### Chemin d'accès aux fichiers

Avant de commencer à manipuler les fichiers, précisons qu'il existe deux possibilités pour parcourir l'arborescence d'un système : utiliser des chemins absolus ou relatifs.
Lorsque l'on utilise des chemins absolus, on décrit le fichier en partant de la racine du disque. Les chemins prennent la forme : `/home/user/cours-python/toto.txt`.


Avec les chemins relatifs, on tient compte du répertoire courant, c'est à dire celui depuis lequel l'interpréteur Python est exécuté (si l'on exécute un fichier .py directement, le répertoire courant est celui contenant le programme; si on utilise l'interpréteur Python, le répertoire courant est celui contenant l'interpréteur). Ainsi, si on est dans le répertoire `/home/user/cours-python/` , on appellera la fichier `resultat.txt` de ce répertoire en saisissant tout simplement `resultat.txt`.

#### Ouverture d'un fichier

Pour ouvrir un fichier, on utilise la fonction open(). Elle prend en paramètre :
+ le chemin du fichier; 
+ le mode d'ouverture : 
  - 'r' pour lire uniquement; 
  - 'w' pour écrire uniquement (le contenu précédent est écrasé); 
  - 'a' pour écrire à la finn uniquement (le contenu précédent est conservé);
 Il est possible de combiner les modes pour, par exemple, lire et ajouter à la fin (en écrivant `ra`).


Lorsque le fichier n'est plus utilisé par le programme, il est nécessaire de le fermer, sans quoi un verrou persiste empêchant son utilisation par une autre personne/un autre programme. On utilise la fonction close().


#### Lecture d'un fichier

Plusieurs modes de lecture d'un fichier sont possible. Les plus courants sont : 
+ la lecture en entier avec la fonction read() 
+ la lecture ligne par ligne avec la fonction readline()

Un exemple de lecture :
```python
fichier = open("fichier.txt", 'r')
contenu = fichier.read()
fichier.close()
```

#### Ecriture dans un fichier

Pour écrire dans un fichier, on utilise la méthode write(texte) en lui passant en paramètre la chaîne de caractères à écrire. Elle renvoie le nombre de caractères qui ont été écrits. Cette fonction peut être appelée plusieurs fois pour écrire plusieurs chaînes. Elle fonctionne que le fichier soit ouvert en mode 'w' ou 'a'.

```python
fichier = open("fichier.txt", 'w')
fichier.write("J'écris pour la première fois dans un fichier texte via Python")
fichier.close()
```

#### L'ouverture avec `with`
L'ouverture et la manipulation de fichiers est une opération source d'erreurs en programmation. De plus, il est facile d'oublier de refermer un fichier après son utilisation, ce qui peut être problématique également.


Pour simplifier l'utilisation des fichiers, Python permet d'utiliser un mot clé : `with`. Avec cette forme d'ouverture d'un fichier, la fermeture du fichier est automatique :
```python
with open("fichier.txt", 'r') as fichier:
  contenu = fichier.read()
```

## Syntaxe du langage


## Modules et fonctions



## Documentation et tests