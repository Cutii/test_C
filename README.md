# C++ Test

Pousser le projet avec un fichier par problème ainsi qu'un Makefile permettant de le compiler
N'hésitez pas à commenter le code.

## Exercice 1 : carrés dans un rectangle

Le but de ce problème est de découper un vrai rectangle (le cas du carré est hors périmètre) en carrés de côté maximum.

Vous devez écrire une fonction `squaresInRect` qui prend deux paramètres :

- `length` : un entier positif
- `width` : un entier positif

Et qui retourne qui retourne une liste d'entiers, représentant le côté de chaque carré.

_std::list<int> squaresInRect(unsigned int length, unsigned int width)_

Exemples :

```C++
squaresInRect(5,3); // devrait retourner {3,2,1,1}
squaresInRect(3,5); // devrait retourner {3,2,1,1}
squaresInRect(5,1); // devrait retourner {1,1,1,1,1}
squaresInRect(2,4); // devrait retourner {2,2}
```

Note : le cas `length == width` est un cas différent, qui n'est pas à traiter ici. Dans ce cas, nous convenons de retourner une liste vide `{}`.

## Exercice 2 : la somme maximuum dans l'arbre ?

Un arbre binaire est une structure de données qui pour chaque noeud a au plus deux fils.
Le but de cet exercice la route possédant la somme maximale entre la racine et une feuille de l'arbre.
Ainsi pour cet arbre

```
   17
   /  \
  3   -10
 /    /  \
2    16   1
         /
        13
```

La fonction **maxSum** devrait retourner 23, puisque la route la plus longue de la racine à une feuille est [17, -10, 16].

Nous utiliserons cette classe pour représenter un arbre binaire :

```C++
class TreeNode
{
    public:
        static TreeNode* leaf(int value=0)
        {
            return new TreeNode(value);
        }

        static TreeNode* join(int valueRoot, TreeNode* left, TreeNode* right)
        {
            return (new TreeNode(valueRoot))->withChildren(left, right);
        }

        TreeNode* withLeft(TreeNode* left)
        {
            this->left = left;
            return this;
        }

        TreeNode* withRight(TreeNode* right)
        {
            this->right = right;
            return this;
        }

        TreeNode* withChildren(TreeNode* left, TreeNode* right)
        {
            this->left = left;
            this->right = right;
            return this;
        }

        TreeNode* withLeftLeaf(int value)
        {
            return withLeft(leaf(value));
        }

        TreeNode* withRightLeaf(int value=0)
        {
            return withRight(leaf(value));
        }

        TreeNode* withLeaves(int valueLeft, int valueRight)
        {
            return withChildren(leaf(valueLeft), leaf(valueRight));
        }

    private:
        TreeNode* left;
        TreeNode* right;
        int value;

        TreeNode(int value, TreeNode* left = nullptr, TreeNode* right = nullptr)
        {
        this->value = value;
        this->left = left;
        this->right = right;
        }
};
```

Implémenter la fonction maxSum :
_int maxSum(TreeNode\* root)_

Exemples :

```C++
TreeNode* root1 = NULL;
maxSum(root1); //devrait retourner 0
    /**
     *      5
     *    /   \
     *  -22    11
     *  / \    / \
     * 9  50  9   2
     */
TreeNode* left = TreeNode::leaf(-22)->withLeaves(9, 50);
TreeNode* right = TreeNode::leaf(11)->withLeaves(9, 2);
TreeNode* root2 = TreeNode::join(5, left, right);
maxSum(root2); //devrait retourner 33 car [5, -22, 50]
```

## Exercice 3 : dessiner un cube

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
