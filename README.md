# Conventions
## Formattage:
-----------
### 1. Indentation:
1. Do not use tabs [4]
1. Indentations are 4 characters deep [4].

### 2. Whitespace:
3. Do not leave whitespaces at the end of lines.
1. Use blank lines to group statements [4].
1. Use only one empty line to separate items [4].
1. Use one space after each keyword [4].\
          Example:
```cpp
if(   // wrong
if (  // correct
```
7. Usage of whitespaces between an opening and closing parenthesis
      (e.g. if- and for-statments, function calls) is up to the developer.\
          Example:
```cpp
if (i < 5)                    <->  if ( i < 5 )
calculateSalary(age, years);  <->  calculateSalary( age, years ); 
```
8. For pointers or references, use
      a single space after '*' or '&', but not before (C++ style),\
          Example:
```cpp
T* v and T& v
```
**Attention:**
          
```cpp
char* i, j;  // i is declared pointer to char, while j is declared char, donc à ne pas faire
```
9. No space after a cast [4].
1. Do not use spaces around '.' or '->',
      nor between unary operators and operands.

### 3. Braces:
 11. Function implementations, class, struct and namespace declarations
      always have the opening brace on the start of a line [4].
 12. For all other constructs (if, switch, for, ...), the left curly brace
      goes on the same line as the start of the statement [4].
 13. Use curly braces even when the body of a conditional statement contains
      only one line [4].

### 4. Statements:
 14. Do not put multiple statements on a single line.

### 5. Switch statements:
 15. Case labels are on the same column as the switch [4].

### 6. Line breaks:
 16. Try to keep lines shorter than 100 characters, inserting line breaks
      as necessary [4].

### 7. Pointeurs:
 17. En C++, un pointeur nul est 
```cpp 
0 ou nullptr
```
et pas
```cpp 
0l ou 0L ou NULL
```

## Variable declaration:
---------------------
 18. Each variable declaration on a new line [4].
 19. Variables and functions start with a lowercase letter.
 20. Classes always start with a capital letter.
 21. Each new word in a name starts with a capital letter [4].
 22. Member variables start with "m_".
 23. Do not use pseudo Hungarian style.\
          Example:
```cpp
m_bSomeBoolean, m_pSomePointer  // wrong
m_someBoolean, m_somePointer    // correct
```
 24. Variables (objectName) in ui files start with "ui_".
          Rationale:
              This makes it possible to identify the source of the variable
              (defined in class or in ui file).
 25. Use vertical alignment to ease scanning of declarations.
          Example:
              QString  aStringToUse;
              int      anInt;
              double   aDoubleNumberToUse;
 26. Use static const variables instead of defining integers or floats.
          Rationale:
              This provides type-safety.


## Casting:
--------
 27. Use C++ style cast like static_cast, dynamic_cast instead of C style
      cast as it asserts the purpose of the cast.
```cpp
Class* t = static_cast<Class*>(object);
SubClass* t = dynamic_cast<SubClass*>(object);
```
et pas :
~~SubClass* t = (SubClass*)object;~~
      Also try to use Qt casts like qobject_cast, qgraphicsitem_cast in 
      place of dynamic_cast wherever possible as the Qt style casts succeeds
      even across libraries.
      It doesn't mean dynamic casts shouldn't be used though. Use them
      wherever it is impossible to use Qt's cast.

Includes:
---------
 29.) Include own header first (checked by Krazy [6]).
 30.) Include Qt QClasses in angle brackets (checked by Krazy [6]).
      But do not add the QtModule like QtGui, because this will change
      in Qt5 and compilation will break.
          Example:
              #include <QtGui/QMenu>  // wrong
              #include <QMenu>        // correct
 31.) Include KDE KClasses in angle brackets (checked by Krazy [6]).
          Example:
              #include <kmessagebox.h>
 32.) Do not add a path to the include statement.
          Example:
              #include "../uml.h"  // wrong
              #include "uml.h"     // correct
          Rationale:
              Paths are set in the make files. Rearranging or moving files
              should not be followed by source code editing.
 33.) Header includes should be listed in the following order and grouped:
        - own header
        - Umbrello includes
        - KDE includes
        - Qt includes
 34.) The headers inside each group should be sorted.
          Rationale:
              For ease of locating them.
          Tip: 
              Kate/KDevelop users can sort the headers automatically.
              Select the lines you want to sort, then
              Tools -> Filter Selection Through Command -> "sort".
              In vim the same can be achieved by marking the block, and then
              doing ":sort". 
              In emacs, you can mark the block and then do "M-x sort-lines".	
 35.) Includes in a header file should be kept to the absolute minimum, as
      to keep compile times low. This can be achieved by using forward
      declarations.
      Forward declarations work for pointers and const references.


Include guards:
---------------
 36.) Include macro characters are all in uppercase letters.
          Example:
              #ifndef MyFileName_h    // wrong
              #ifndef MY_FILE_NAME_H  // correct
 37.) Do not use leading or trailing underscores on the include guard macro
      as they are reserved for compiler/libc use (checked by Krazy [6]?).
          Example:
              #ifndef _MY_FILE_NAME_H_  // wrong
              #ifndef MY_FILE_NAME_H    // correct


Doxygen comments:
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


Header structure:
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


C++:
----
 43.) "const correctness" should be preserved as much as possible.
      Make all getters const.
 44.) It might be a good idea to make the constructors explicit
      (checked by Krazy [6]).


Metrics:
--------
- loc = lines of code
- Refactor classes, which have more than 1000 loc per class.
- Refactor methods, which have more than  200 loc per method.
