# Exercices de mise en pratique de l'algorithmique
Il s'agira dans les exercices suivants d'écrire une (ou plusieurs) fonction(s) répondant à la problématique.

## Permutation
Écrire une fonction qui permute les valeurs attribuées à deux variables.

## Parité
Écrire une fonction qui détermine la parité de la valeur attribuée à une variable.

## Tableaux
Les exercices suivants porteront sur des tableaux, structure de donnée composite abordée pendant le cours.
Par exemple `tabl = [1, 2, 3]` est un tableau de longueur 3.
Pour accéder à ses éléments, on utilisera la notation suivante : `tabl[i]` (avec `i` commençant à 0)
Ainsi : `tabl[0]` vaut `1` et `tabl[3]` n'existe pas.

Dans les exercices suivants, on considèrera un tableau de nombres entiers et de longueur `long`.

### Somme
Écrire une fonction qui calcule la somme de tous les éléments du tableau

### Maximum
Écrire une fonction qui calcule le maximum de tous les éléments du tableau

### Minimum
Écrire une fonction qui calcule le minimum de tous les éléments du tableau

### Moyenne
Écrire une fonction qui calcule la moyenne des éléments du tableau

### Médiane
Écrire une fonction qui calcule la médiane des éléments du tableau

### Tri
Écrire une procédure qui trie les valeurs du tableau dans l'ordre croissant et renvoie un nouveau tableau


## Factorielle
La factorielle du nombre n, notée `n!` est le produit de tous les nombres entiers consécutifs jusqu'à n.

Écrire une fonction qui calcule la factorielle du nombre n.
Réécrire cette fonction en mode récursif.


## Nombre mystère (jeu de "plus ou moins")
> Nouvelles instructions : Afficher et Entrer
Pour afficher de la donnée, un algorithme pourra utiliser l'instruction Afficher
`Afficher ma_variable`
Pour affecter une valeur entrée par l'utilisateur à une variable, on pourra utiliser l'instruction Entrer
`Entrer ma_variable`

Exemple : le programme suivant affiche la somme de 2 et d'un nombre entré par l'utilisateur
```
Entrer nombre
Afficher nombre + 2
```

À l'aide de ces nouvelles instructions, créer une procédure qui prend en entrée un nombre n, qui calcule un nombre aléatoire entre 0 et n, et qui tente de le faire deviner à l'utilisateur en lui indiquant si la valeur à deviner est plus élevée ou plus faible que la dernière valeur entrée.
> On pourra utiliser la fonction nombre_aleatoire(inf, sup) qui renvoie un nombre entier aléatoire entre inf et sup
