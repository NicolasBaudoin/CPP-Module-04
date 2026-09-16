# CPP-Module-04

![C++](https://img.shields.io/badge/C++-98-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Top language](https://img.shields.io/github/languages/top/NicolasBaudoin/CPP-Module-04?style=flat-square)
![Last commit](https://img.shields.io/github/last-commit/NicolasBaudoin/CPP-Module-04?style=flat-square)

> Subtype Polymorphism, Abstract Classes, and Interfaces.

Cinquième module du parcours C++ à 42. Polymorphisme dynamique (`Animal`/`Dog`/`Cat`), classes abstraites et interfaces (`AMateria`). Tout le code suit la norme **C++98**, classes en **Orthodox Canonical Form**.

---

- [Règles générales](#règles-générales)
- [Exercice 00 — Polymorphism](#exercice-00--polymorphism)
- [Exercice 01 — I don't want to set the world on fire](#exercice-01--i-dont-want-to-set-the-world-on-fire)
- [Exercice 02 — Abstract class](#exercice-02--abstract-class)
- [Exercice 03 — Interface & recap](#exercice-03--interface--recap)
- [Rendu et évaluation](#rendu-et-évaluation)

## Règles générales

- Compiler avec `c++` et les flags `-Wall -Wextra -Werror`, compatible `-std=c++98`
- Dossiers d'exercices : `ex00`, `ex01`, ..., `exn`
- Classes en **Orthodox Canonical Form** (sauf mention contraire)
- STL interdite avant les Modules 08/09 ; `using namespace` et `friend` interdits
- Constructeurs/destructeurs de **chaque** classe doivent afficher un message **spécifique** (pas le même partout)

---

## Exercice 00 — Polymorphism

| | |
|---|---|
| **Dossier** | `ex00/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `*.cpp`, `*.{h, hpp}` |
| **Interdit** | Aucun |

Classe de base `Animal` avec un attribut **protégé** `std::string type`. `Dog` et `Cat` en héritent et fixent `type` à `"Dog"` / `"Cat"` respectivement.

Méthode `makeSound()` sur chaque animal, avec le **son approprié** — y compris quand on manipule les objets via un `Animal*` (polymorphisme dynamique, donc `makeSound()` **virtuelle**).

Pour vérifier la compréhension : implémenter `WrongAnimal`/`WrongCat` où `makeSound()` n'est **pas** virtuelle, et constater que `WrongCat` sonne comme `WrongAnimal`.

---

## Exercice 01 — I don't want to set the world on fire

| | |
|---|---|
| **Dossier** | `ex01/` |
| **Fichiers à rendre** | Fichiers précédents + `*.cpp`, `*.{h, hpp}` |
| **Interdit** | Aucun |

Classe `Brain` contenant un tableau de 100 `std::string` (`ideas`). `Dog` et `Cat` ont un attribut privé `Brain*`, créé (`new`) au constructeur et détruit (`delete`) au destructeur.

Dans `main` : créer un tableau d'`Animal*` (moitié `Dog`, moitié `Cat`), puis tout supprimer via des pointeurs `Animal*` — les destructeurs corrects doivent s'enchaîner. Vérifier l'absence de fuites mémoire et que la copie d'un `Dog`/`Cat` est une **copie profonde** de son `Brain`.

---

## Exercice 02 — Abstract class

| | |
|---|---|
| **Dossier** | `ex02/` |
| **Fichiers à rendre** | Fichiers précédents + `*.cpp`, `*.{h, hpp}` |
| **Interdit** | Aucun |

Rendre `Animal` **non instanciable** (classe abstraite, au moins une méthode virtuelle pure) sans rien casser d'autre. Renommer éventuellement en `AAnimal`.

---

## Exercice 03 — Interface & recap

| | |
|---|---|
| **Dossier** | `ex03/` |
| **Fichiers à rendre** | `Makefile`, `main.cpp`, `*.cpp`, `*.{h, hpp}` |
| **Interdit** | Aucun |
| **Optionnel** | Le module passe sans cet exercice |

Système d'inventaire de "Materia" façon RPG :

- `AMateria` (classe abstraite / interface) : type, `getType()`, `clone()` (virtuelle pure), `use(ICharacter&)` (virtuelle)
- `Ice` (`"ice"`) et `Cure` (`"cure"`), concrètes, avec leur propre `clone()` et message `use()`
- `ICharacter` (interface pure) : `getName()`, `equip()`, `unequip()`, `use()`
- `Character` : inventaire de **4 slots**, équipement dans le premier slot libre, `unequip()` ne détruit **pas** la Materia, copie **profonde**
- `IMateriaSource` / `MateriaSource` : apprend jusqu'à 4 "modèles" de Materia (`learnMateria`) et en crée des copies à la demande (`createMateria`)

Attention à la gestion mémoire : chaque `new` doit avoir son `delete` correspondant (inventaire, source, floor items...).

---

## Rendu et évaluation

- Rendu sur le dépôt Git ; seul le contenu du repo est évalué
- Une petite modification peut être demandée en soutenance pour vérifier la compréhension réelle du code
