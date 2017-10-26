# Conventions
## Git
-----------
### Formattage
- Toujours faire un nom de commit explicite !! :
  - NON ! :
    - correction
    - loadMusic fait
    - ghrksj,gksdnkgj
    - test
    - IHM fini
    - wallah
    - meh
    - ...
          
  - OUI :) :
    - [FONCTIONAL] Correction du lancement de l'IHM (image apparait)
    - [ToTEST] ajout de la coloration syntaxique (juste pour quelque mots)

- En plus du nom du commit explicite, il faut souvent une description (les listes c'est bien) !! ex :
```
[ToTEST] ajout de la coloration syntaxique (juste pour quelque mots)
# ligne a laisser blanche
    - coloration pour :
      - si
      - sinon
      - fin
      - else
```
ou
```
[ToTEST] ajout de la coloration syntaxique (juste pour quelque mots)
# ligne a laisser blanche
    - coloration pour :
      - les mots clés
      - quelques fonctions importantes (avancer, reculer ...)
      - commencement pour les variables (juste la recupération pas encore la coloration)
```

- Toujours mettre un flag avant chaque message parmis ceux-ci (si il en manques, venez me voir) :
  - [FONCTIONAL] : fonctionnel
  - [ToTEST] : à tester
  - [INSTABLE] : instable, on sait que ca marche pas, mais on a du commit
- Vous pouvez créer des alias (-e : permet l'edition meme avec un message) /!\ le nom de l'alias est à changer (ex cFonct ou commitFonct ...): 
<pre>
git config --global alias.<b>nomAlias</b> 'git commit -m "[FONCTIONNAL] " -e'
git config --global alias.<b>nomAlias</b> 'git commit -m "[ToTEST] " -e'
git config --global alias.<b>nomAlias</b> 'git commit -m "[INSTABLE] " -e'
</pre>

- Apres le flag, mettre le mot qui resume votre commit :
  - add/ajout
  - fix
  - modify/modifie

###  Workflow
- Commit dès qu'une tache est terminée !
- Si vous n'arrivez pas à resumer un commit dans son nom, qu'il manques des choses,\
  c'est qu'il faut diviser en plusieurs commit (vous pouvez utiliser git commit -p ou -i)
- une branche par fonctionnalité !!
- dès que vous pensez que votre branche est prête, faite un pull-request (pas un merge) donc sur GitHub dans develop
- Rappel du workflow :
![GitFlow](https://www.braintime.de/wp-content/uploads/2014/09/4-2-1-1-gitflow.png)
La branche principale est develop, mais on passe en fait par les branches thématiques feature/??? et des Pull-Request.\
Puis on merge dans release pour préparer la prochaine version public et enfin on merge dans master pour le public (et on tag genre : v1.1).\
Parfois il faut corriger un bogue rapidement et on par par hotfix et on remerge dans master directement.

## Formattage du code :
-----------
Un fichier xml de formattage est fournie pour [eclipse](https://github.com/SpaceBoxInk/Conventions), de là vous pouvez cloner ou télécharger le repo.\
Ensuite dans Eclipse > Window > preferences > C/C++ > Code Style > Formatter > bouton import
### 1. Indentation :
1. NE PAS UTILISER DE TABULATIONS !! utiliser des espaces (dans les IDE regarder dans les parametres de formattage).
1. L'indentation est de 4 caractères.

### 2. Espaces :
3. Ne laisser pas d'espaces en fin de ligne.
1. Faites des sauts de ligne pour grouper des instructions/declarations.
1. Utiliser seulement un saut de ligne pour grouper.
1. Utiliser un espace après chaque mot clé.\
          Example:
```cpp
if(   // wrong
if (  // correct
```
7. Usage des espace dans les parentheses
      (e.g. if- et for-, function calls) faite comme vous voulez.\
          Example:
```cpp
if (i < 5)                    <->  if ( i < 5 )
calculateSalary(age, years);  <->  calculateSalary( age, years ); 
```
8. Pour les pointers ou les references, Utiliser\
      un simple espace après '*' ou après '&', mais pas avant (C++ style),\
          Example:
```cpp
T* v;
T& v;
```
**Attention:**
          
```cpp
char* i, j;  // i is declared pointer to char, while j is declared char, donc à ne pas faire
```
9. Pas d'espace après un cast.
1. Pas d'espaces autours de '.' ou '->',
      ni entre les operateurs unaires ni les operandes.

### 3. Accolades :
 11. Les implementations de fonction, les classes, les struct et les declarations de namespace\
      on toujours leurs accolade ouvrante sur le debut de la ligne (suivante) :
```c++
class Test
{
  cout<<"test";
}
```
 12. Pour tous les autres (if, switch, for, ...), l'accolade ouvrante\
      va sur la meme ligne que le debut de l'expression : 
```c++
if (true) {
  cout<<"test";
}
```
 13. Utiliser toujours des blocs (accolades) meme s'il n'y a qu'une instruction (si jamais on doit en rajouter, cela reste consistant).

### 4. Instructions :
 14. Ne pas mettre plusieurs instructions sur la meme ligne.

### 5. Switch :
 15. Les case sont sur la meme colonne que le switch.

### 6. Retour à la ligne :
 16. Try to keep lines shorter than 100 characters, inserting line breaks
      as necessary [4].

### 7. Pointeurs :
 17. En C++, un pointeur nul est
```cpp 
nullptr
```
et pas
```cpp 
0l ou 0L ou NULL
```

## Declaration de variable :
---------------------
 18. Declarer chaque variable sur une nouvelle ligne.
 19. les variables et les fonctions commencent par une minuscule.
 20. Les classes commences toujours par une **Majuscule** (n'est ce pas Jessy ;) ).
 21. Chaque nouveau mot dans un nom commence par une **Majuscule** :
```cpp
int varTest;
class TestExemple{
  public:
  void methodeDeClasse();
};
```
 22. N'utiliser des enderscores "_" **que** pour les constantes `static int const TEST_CONSTANT;` sauf :
 23. Les attributs membre/fields/champs commence tous par "_" comme `string _nom;`.
 24. Ne pas utiliser du pseudo Hungarian style.\
          Example:
```cpp
_bSomeBoolean, _pSomePointer  // wrong
_someBoolean, _somePointer    // correct
```
 25. 
 26. Utiliser un alignement vertical pour faciliter la lecture des declarations :\
          Example:
```cpp
QString  aStringToUse;
int      anInt;
double   aDoubleNumberToUse;
```
 27. Utiliser les static const pour les constantes !\
          Raison:\
              Pour la sureté des types.

## Casting :
--------
 28. Utiliser les cast du C++ comme static_cast, dynamic_cast au lieu de ceux du C
```cpp
Class* t = static_cast<Class*>(object);
SubClass* t = dynamic_cast<SubClass*>(object);
```
et pas :
~~SubClass* t = (SubClass*)object;~~

## Includes :
---------
 29. Inclure ses headers d'abord.
 30. Inclure ensuite les headers systemes
 31. Les includes des headers doivent etre minimale, du au temps de compilation.\
          Cela peut etre fait par des "forward declare" puis ensuite inclure dans les sources(.cpp)\
      les "Forward declarations" marchent pour les pointers et les const references.


## Include guards :
---------------
 32. Les include macro doivent etre toutes en majuscules.\
          Example:
```cpp
#ifndef MyFileName_h    // wrong
#ifndef MY_FILE_NAME_H  // correct
```
 33. Do not use leading or trailing underscores on the include guard macro
      as they are reserved for compiler/libc use (checked by Krazy [6]?).
          Example:
              #ifndef _MY_FILE_NAME_H_  // wrong
              #ifndef MY_FILE_NAME_H    // correct


## Commantaires Doxygen :
-----------------
 38.) Every public item must have a doxygen comment.
 39.) Doxygen comments look like (see also [9]):
      /**
       * Here is the description...
       * @param ...   ...
       * @return      ...
       */
 40.) The comments for methods should be written in the implementation file (cpp).
      The comments for the class should be written in the header file.
          Rational:
              The header files can be overviewed easier and read quicker.


## Structure de header :
-----------------
 41.) According to policy, a C++ header file should contain only 1 publicly
      visible class.
 42.) Use the following layout:

      <license>
      <include guard>
      <includes>

      namespace
      {

      /**
       * description
       */
      class <name> : public <parent>
      {
      public:

      protected:

      private:

      };

      }


## C++ :
----
 43.) "const correctness" should be preserved as much as possible.
      Make all getters const.
 44.) It might be a good idea to make the constructors explicit
      (checked by Krazy [6]).


## Metrics :
--------
- loc = lines of code
- Refactor classes, which have more than 1000 loc per class.
- Refactor methods, which have more than  200 loc per method.
