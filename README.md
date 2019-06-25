# C++ Test

Pousser le projet avec un fichier par problème ainsi qu'un Makefile permettant de le compiler.
Si vous utiliser un outils complémentaire (CMake, Ninja, ...) indiquer les commandes permettant de compiler / exécuter le code.
N'hésitez pas à commenter le code.

## Exercice 1 : carrés dans un rectangle

Le but de ce problème est de découper un vrai rectangle (le cas du carré est hors périmètre) en carrés de côté maximum.

Vous devez écrire une fonction `squaresInRect` qui prend deux paramètres :

- `length` : un entier positif
- `width` : un entier positif

Et qui retourne qui retourne une liste d'entiers, représentant le côté de chaque carré.

_std::list\<int\> squaresInRect(unsigned int length, unsigned int width)_

Exemples :

```C++
squaresInRect(5,3); // devrait retourner {3,2,1,1}
squaresInRect(3,5); // devrait retourner {3,2,1,1}
squaresInRect(5,1); // devrait retourner {1,1,1,1,1}
squaresInRect(2,4); // devrait retourner {2,2}
```

Note : le cas `length == width` est un cas différent, qui n'est pas à traiter ici. Dans ce cas, nous convenons de retourner une liste vide `{}`.

## Exercice 2 : dessiner un cube

Le but de ce problème est de coder une fonction `drawCube` qui dessine un cube de côté `n` passé en paramètre, en ASCII :

- Pour `n<=0` renvoyer un chaine vide
- Les contours du cube sont `#`
- La face avant du cube doit avoir le caractère ``
- Les autres faces du cube doit avoir le caractère `*`
- le cube doit se terminer par le caractère `\n``

Exemples :

```
n=1
#\n

n=2
 ##\n
###\n
##\n

n=3
  ###\n
 #*##\n
###*#\n
# ##\n
###\n

n=4
   ####\n
  #**##\n
 #**#*#\n
####**#\n
#  #*#\n
#  ##\n
####\n

n=5
    #####\n
   #***##\n
  #***#*#\n
 #***#**#\n
#####***#\n
#   #**#\n
#   #*#\n
#   ##\n
#####\n
```

_std::string drawCube(int size)_
