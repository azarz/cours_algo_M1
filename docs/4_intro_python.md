# Programmation avec Python

## Introduction

Ce cours est une initiation au langage de programmation Python. Il n'est pas nécessaire de déjà connaître ce langage, ni d'avoir des notions avancées en programmation, pour pouvoir l'aborder. Dans la mesure du possible, chaque notion est illustrée d'exemple. Le cours se concentre sur la description du fonctionnement du langage et des syntaxes employées.


On utilisera l'[IDE](https://fr.wikipedia.org/wiki/Environnement_de_d%C3%A9veloppement) Visual Studio Code [(lien)](https://code.visualstudio.com/), qui permet d'écrire du code pour Python mais aussi bien d'autres langages (web, etc). On installera Python et l'extension Python pour VS Code en suivant le tutotriel suivant : [https://code.visualstudio.com/docs/languages/python](https://code.visualstudio.com/docs/languages/python).

La version 3 de Python est la seule utilisée tout au long du cours. Les exemples présentés ici sont compatibles avec Python 3. On privilégiera la dernière version stable (Python 3.15 au 21 octobre 2026).

## Environnements virtuels

Un environnement virtuel est un espace isolé pour les paquets Python d'un projet. Il évite que les dépendances de plusieurs projets se mélangent. Depuis la racine du projet, le créer avec :

```bash
python -m venv .venv
```

Activer ensuite l'environnement dans le terminal utilisé pour le TP :

- macOS ou Linux (bash/zsh) : `source .venv/bin/activate`
- Windows PowerShell : `.\.venv\Scripts\Activate.ps1`
- Windows Invite de commandes : `.venv\Scripts\activate.bat`

Une fois l'environnement activé, installer les paquets nécessaires avec `python -m pip install nom_du_paquet`. Dans VS Code, sélectionner aussi l'interpréteur situé dans `.venv` (commande **Python: Select Interpreter**). Pour quitter l'environnement, exécuter `deactivate`. Le dossier `.venv` est local au projet et ne doit pas être versionné.

## Types et opérations

Ce chapitre va nous permettre de commencer à utiliser le langage Python. Nous nous limiterons pour commencer à des opérations basiques comme des opérations mathématiques ou des manipulations de chaînes de caractères. Plus précisément, nous nous limiterons dans ce chapitre aux opérations sur des types de base définis dans le langage.


Avant cela, nous définirons ce que sont une variable et un type en informatique. Nous introduirons un concept important en Python, le typage dynamique, et montrerons comment sont gérées données dans ce langage.


### Variables et types en Python
#### Généralités
La programmation consiste essentiellement à manipuler des données. Ces données de natures diverses sont stockées sous forme binaire dans la mémoire de l'ordinateur. Pour y accéder, un programme définit des __variables__.


Nous définirons ainsi une variable comme l'association d'un nom et d'une valeur. Le nom est utile au programmeur pour savoir quelle donnée il manipule, tandis que l'ordinateur utilise la valeur associée. De manière imagée, le nom peut être vu comme une simple étiquette sur une donnée.


En Python, le nom (on parle parfois d'identificateur) :
  + peut contenir des lettres, des chiffres et des blancs soulignés; de nombreuses lettres non ASCII sont également acceptées;
  + ne peut pas contenir d'espace ou de caractères spéciaux (&, ;...);
  + ne peut pas commencer par un chiffre;
  + distingue minuscules et majuscules (on dit que le langage est sensible à la casse);
  + peut être réutilisé ou réaffecté; sa portée détermine où cette liaison de nom est visible. Par convention, pour les noms de variable, on séparera les mots par des blancs soulignés : `mon_nom_de_variable`. Les noms de la forme `__nom__` sont réservés aux usages définis par Python (exemple : `__str__`). Les mots-clés ne peuvent pas être utilisés comme identificateurs ordinaires. La liste dépend de la version et figure dans la [documentation officielle](https://docs.python.org/3/reference/lexical_analysis.html#keywords).

Certains mots sont des mots-clés contextuels : `match` et `case` dans une instruction `match`, `_` dans un motif, `type` dans une déclaration de type et `lazy` avant un import.


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

`Decimal` et `Fraction` sont fournis par les modules `decimal` et `fractions` : on les utilise après les imports `from decimal import Decimal` et `from fractions import Fraction`.


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

Les opérations logiques retournent des booléens. La table suivante liste les opérateurs de comparaison. Ils s'appliquent aux objets dont les types définissent la comparaison correspondante; comparer un nombre et une chaîne avec `<`, par exemple, provoque une erreur en Python 3.


| Opérateur | Signification |
| \> | Supérieur |
| < | Inférieur |
| \>= | Supérieur ou égal |
| <= | Inférieur ou égal |
| == | Egal |
| != | Différent de |
| is | Même objet (identité) |
| is not | Objets distincts (identité) |

Pour tester l'égalité des valeurs, on utilise `==`. `is` et `is not` servent notamment à tester une valeur unique comme `None` (`x is None`).

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

Cette valeur est notamment renvoyée par une fonction qui ne contient pas de `return` explicite. Elle sert aussi à représenter l'absence de valeur; une erreur est généralement signalée par une exception, pas par `None`.


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
| `[i:j]` | Caractères de la position i à la position j exclue |

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

Les dictionnaires sont des objets semblables aux listes mais plus souples en ce qui concerne le référencement des valeurs. Alors qu'une liste référence les éléments qu'elle contient à l'aide de leur position, un dictionnaire associe une valeur à une clé. Une clé doit être hachable (par exemple un nombre, une chaîne ou un tuple dont les éléments sont eux-mêmes hachables); une liste ou un dictionnaire ne peut pas servir de clé.

Les dictionnaires conservent l'ordre d'insertion des clés, mais on y accède par leurs clés plutôt que par position. La structure d'un dictionnaire est modifiable : on peut ajouter, modifier ou supprimer des éléments.

La syntaxe de création d'un dictionnaire est la suivante :
```python
>>> dico = {cle1: valeur1 , cle2: valeur2...}
```

On peut créer un dictionnaire vide de l'une de ces façons :
```python
dico = {}
dico = dict()
```

Pour accéder à la valeur d'un élément, la syntaxe est semblable à celle d'une liste, mais l'indice n'est plus uniquement un entier : `dico[cle]` retourne la valeur associé à la clé.
```python
>>> dico = {'prenom': 'paul', 'age': 24} >>> dico['prenom'] 'paul'
```

L'ajout d'une nouvel élément est assez aisé :
```python
>>> dico[0] = 'rouge' >>> dico {0: 'rouge', 'age': 24, 'prenom': 'paul'}
```

Les dictionnaires implémentent aussi des méthodes qui retournent des vues dynamiques :
+ `d.items()` : couples (clé, valeur) du dictionnaire;
+ `d.keys()` : clés du dictionnaire;
+ `d.values()` : valeurs du dictionnaire.


### Les fichiers

Dans ce paragraphe, nous nous attarderons sur le dernier type de base qui sera présenté dans ce cours : les fichiers. Nous montrerons comment lire ou écrire dans un fichier.

#### Chemin d'accès aux fichiers

Avant de commencer à manipuler les fichiers, précisons qu'il existe deux possibilités pour parcourir l'arborescence d'un système : utiliser des chemins absolus ou relatifs.
Lorsque l'on utilise des chemins absolus, on décrit le fichier en partant de la racine du disque. Les chemins prennent la forme : `/home/user/cours-python/toto.txt`.


Avec les chemins relatifs, on tient compte du répertoire courant du processus Python, qui dépend de la façon dont le programme est lancé et n'est pas nécessairement le dossier du script ni celui de l'interpréteur. Ainsi, si le répertoire courant est `/home/user/cours-python/`, on peut désigner un fichier de ce répertoire avec `resultat.txt`.

#### Ouverture d'un fichier

Pour ouvrir un fichier, on utilise la fonction open(). Elle prend en paramètre :
+ le chemin du fichier;
+ le mode d'ouverture :
  - 'r' pour lire uniquement;
  - 'w' pour écrire uniquement (le contenu précédent est écrasé);
    - 'a' pour écrire à la fin uniquement (le contenu précédent est conservé);
    - 'r+' pour lire et écrire sans tronquer le fichier;
    - 'a+' pour lire et écrire en ajoutant les écritures à la fin.


Lorsque le fichier n'est plus utilisé, il faut le fermer afin de libérer les ressources et de vider les données encore en mémoire tampon. Cela ne signifie pas qu'un verrou empêchera nécessairement les autres programmes de l'utiliser. On peut fermer le fichier avec `close()` ou, de préférence, utiliser `with`.


#### Lecture d'un fichier

Plusieurs modes de lecture d'un fichier sont possibles. Les plus courants sont :
+ la lecture de tout le contenu avec la méthode `read()`;
+ la lecture d'une ligne avec la méthode `readline()`.

Un exemple de lecture :
```python
fichier = open("fichier.txt", 'r', encoding='utf-8')
contenu = fichier.read()
fichier.close()
```

#### Ecriture dans un fichier

Pour écrire dans un fichier, on utilise la méthode write(texte) en lui passant en paramètre la chaîne de caractères à écrire. Elle renvoie le nombre de caractères qui ont été écrits. Cette fonction peut être appelée plusieurs fois pour écrire plusieurs chaînes. Elle fonctionne que le fichier soit ouvert en mode 'w' ou 'a'.

```python
fichier = open("fichier.txt", 'w', encoding='utf-8')
fichier.write("J'écris pour la première fois dans un fichier texte via Python")
fichier.close()
```

#### L'ouverture avec `with`
L'ouverture et la manipulation de fichiers est une opération source d'erreurs en programmation. De plus, il est facile d'oublier de refermer un fichier après son utilisation, ce qui peut être problématique également.


Pour simplifier l'utilisation des fichiers, Python permet d'utiliser un mot clé : `with`. Avec cette forme d'ouverture d'un fichier, la fermeture du fichier est automatique :
```python
with open("fichier.txt", 'r', encoding='utf-8') as fichier:
  contenu = fichier.read()
```

## Syntaxe du langage

Au chapitre précédent, nous avons étudié les structures de base intégrées dans le langage Python. Maintenant que nous maîtrisons les différents types de données, nous pouvons commencer à construire nos premières expressions en Python.

Dans ce chapitre, nous allons commencer par rappeler les règles générales de construction des expressions en Python, puis nous apprendrons à construire les structures élémentaires du langage.


### Structure du code en Python

En Python, la règle générale est que **la fin d’une ligne correspond à la fin d’une instruction**. Il n’y a pas de symbole de fin d’instruction comme dans d’autres langages.

Exemple en Java :

```java
instruction1 ;
instruction2 ;
```

En Python :

```python
instruction1
instruction2
```

Pour définir un **bloc de code**, Python utilise l’**indentation**. De plus la ligne d’en-tête du bloc se termine par `:` :

```python
ligne_d_en_tete:
    bloc_d_instructions
```

Par exemple, un test en Java :

```java
if (condition) {
    instruction1;
    instruction2;
}
```

devient en Python :

```python
if condition:
    instruction1
    instruction2
```

Les lignes vides sont ignorées, mais l'indentation délimite les blocs et fait partie de la syntaxe. À l'intérieur de parenthèses, crochets ou accolades, une expression peut s'étendre sur plusieurs lignes. Par exemple, les lignes vides entre les instructions suivantes ne changent pas le programme :

```python
ligne_d_en_tete:

    instruction1

    instruction2
```

est équivalent à :

```python
ligne_d_en_tete:
    instruction1
    instruction2
```

#### Commentaires

- Commentaire simple : commence par `#`
- Docstrings : chaînes placées au début d'un module, d'une fonction ou d'une classe pour en documenter le rôle; les triples guillemets sont une convention courante.

---

### Les affectations

Pour affecter une valeur à une variable :

```python
a = 3
```

Affectations multiples :

```python
a, b = 3, 2
a = b = c = 3
```

#### Affectations augmentées

```python
a = 3
a += 3  # équivalent à a = a + 3
```

Opérateurs disponibles : `+=`, `-=`, `*=`, `/=`, `//=`, `%=`, etc.

---

### Les tests

```python
if condition:
    instruction1
    instruction2
```

#### Avec `else`

```python
if x >= 0:
    print("x positif")
else:
    print("x négatif")
```

#### Avec `elif`

```python
if x > 0:
    print("x positif")
elif x < 0:
    print("x négatif")
else:
    print("x est nul")
```

---

### Les boucles

#### Boucle `while`

```python
i = 0
while i < 3:
    print(i)
    i += 1
```

#### Boucle `for`

```python
for i in [1, 2, 3]:
    print(i)
```

Avec `range` :

```python
for i in range(5):
    print(i)
```

#### `break`

Interrompre la boucle :

```python
for i in range(10):
    if i == 3:
        break
    print(i)
```

#### `continue`

Passer à l’itération suivante :

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

## Modules et fonctions

### Modules

Python propose une grande quantité de **modules** standards. Pour les utiliser, il suffit de les **importer**.

Exemple avec le module `math` :

```python
import math
print(math.sqrt(16))  # racine carrée
```

On peut aussi importer une **fonction spécifique** :

```python
from math import sqrt
print(sqrt(25))
```

Ou tout le module (**fortement déconseillé**) :

```python
from math import *
```

Il est également possible de **renommer** un module à l’import :

```python
import math as m
print(m.sqrt(36))
```

### Création de modules

Un module Python est simplement un **fichier `.py`** contenant du code (fonctions, classes, etc.).

Exemple dans `monmodule.py` :

```python
def bonjour():
    print("Bonjour depuis monmodule")
```

Utilisation :

```python
import monmodule
monmodule.bonjour()
```

Le module doit être **dans le même dossier** ou dans le **PYTHONPATH**.

### Fonctions

Les fonctions s’écrivent avec le mot-clé `def` :

```python
def salut():
    print("Salut !")
```

Appel :

```python
salut()
```

Avec arguments :

```python
def dire_bonjour(nom):
    print("Bonjour", nom)

dire_bonjour("Alice")
```

Avec valeur de retour :

```python
def carre(x):
    return x * x

print(carre(4))  # 16
```

### Paramètres par défaut

```python
def saluer(nom="inconnu"):
    print("Salut", nom)

saluer()
saluer("Bob")
```

### Arguments nommés

```python
def personne(nom, age):
    print(f"{nom} a {age} ans")

personne(age=30, nom="Alice")
```

### Portée des variables

- Variables **locales** : définies dans une fonction
- Variables **globales** : définies hors fonction

```python
x = 5  # globale

def afficher():
    x = 10  # locale
    print(x)

afficher()  # 10
print(x)    # 5
```

Pour modifier une variable globale depuis une fonction :

```python
x = 5

def modifier():
    global x
    x = 20

modifier()
print(x)  # 20
```


## Documentation et tests

### La documentation

La documentation est essentielle pour expliquer le rôle, le fonctionnement, et les paramètres d’une fonction ou d’un module.

Python permet d’associer une **chaîne de documentation** à une fonction, classe ou module grâce aux **docstrings** :

```python
def addition(a, b):
    """Retourne la somme de a et b."""
    return a + b
```

On peut consulter cette documentation avec :

```python
help(addition)
```

Ou encore :

```python
print(addition.__doc__)
```

Les docstrings peuvent suivre la convention [PEP 257](https://peps.python.org/pep-0257/) pour être lisibles par des outils de génération de documentation.

### Les tests

#### Test simple avec `assert`

Pour des tests légers, on peut aussi utiliser `assert` directement dans le code :

```python
def somme(a, b):
    return a + b

assert somme(2, 3) == 5
assert somme(-1, 1) == 0
```

Si l’assertion échoue, Python lève une exception `AssertionError`.

#### Contexte d'exécution des tests

Une manière d'exécuter les tests est d'appeler les fonctions et de faire des assertions au niveau du module, dans un bloc `if __name__ == "__main__"`:

```python
# fichier somme.py
def somme(a, b):
    return a + b

if __name__ == "__main__": # exécuté avec `python somme.py`, pas lors de l'import de somme depuis main.py
    print("Testing somme.py...")
    assert somme(2, 3) == 5
    assert somme(-1, 1) == 0
```
```python
# fichier main.py
import somme as s

print(s.somme(3, 4))
```
