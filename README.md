# Simulateur de CPU - LU2IN006 (Sorbonne Université)

[![Note](https://img.shields.io/badge/Note-17%2F20-brightgreen.svg)](#)
[![Language](https://img.shields.io/badge/Language-C-blue.svg)](#)

Ce projet consiste en la conception et l'implémentation d'un **simulateur de processeur (CPU)** complet en langage C. Il couvre la gestion de la mémoire, l'interprétation d'instructions assembleur, et la manipulation de structures de données complexes (tables de hachage et listes chaînées).

## 🏆 Évaluation
Ce projet a été réalisé dans le cadre de l'unité **LU2IN006 (Structures de Données)** et a obtenu la note de **17 / 20**.

---

## 🚀 Fonctionnalités Clés

### 1. Gestion de la Mémoire (Memory Handler)
* **Segmentation :** Gestion des segments standards (`CS` pour le code, `DS` pour les données, `SS` pour la pile) et d'un segment dynamique (`ES`).
* **Stratégies d'Allocation :** Implémentation des algorithmes de recherche d'espace libre :
    * `First-Fit` (Stratégie 0)
    * `Best-Fit` (Stratégie 1)
    * `Worst-Fit` (Stratégie 2)
* **Gestion des segments libres :** Utilisation d'une `free_list` (liste chaînée) pour suivre les blocs mémoire disponibles.

### 2. Unité d'Exécution & Registres
* **Registres supportés :** `AX`, `BX`, `CX`, `DX` (généraux), `IP` (Instruction Pointer), `SP`/`BP` (Stack), `ZF`/`SF` (Flags) et `ES`.
* **Modes d'Adressage :**
    * Immédiat (ex: `MOV AX, 10`)
    * Direct / Registre (ex: `MOV AX, BX`)
    * Indirect (ex: `MOV AX, [BX]`)
    * Adressage par segment (ex: `[DS:BX]`, `[ES:10]`)

### 3. Jeu d'Instructions
* **Arithmétique :** `ADD`, `SUB`, `MUL`, `DIV`, `CMP`.
* **Contrôle de flux :** `JMP`, `JZ`, `JNZ`, `JS`, `JNS`.
* **Pile :** `PUSH`, `POP`.
* **Gestion dynamique :** `ALLOC` (allocation du segment ES), `FREE`.
* **Système :** `HALT`.

---

## 🛠 Architecture Technique

Le simulateur repose sur des structures de données robustes :
* **Table de Hachage (HashMap) :** Utilisée pour stocker le contexte des registres, les labels de saut, et les variables du segment de données. Elle utilise une gestion des collisions par **sondage linéaire** et gère les `TOMBSTONE` pour les suppressions.
* **Analyseur Syntaxique (Parser) :** Traduit les fichiers `.asm` en structures d'instructions exploitables, gère la résolution des constantes et des labels.

---

## 📁 Organisation du Code

| Fichier | Description |
| :--- | :--- |
| `hachage.c/h` | Implémentation de la Table de Hachage. |
| `memorymanager.c/h` | Logique d'allocation et gestion de la fragmentation. |
| `data_seg.c/h` | Initialisation du CPU et gestion du segment de données. |
| `exercice5.c` | Implémentation des modes d'adressage (Regex). |
| `exercice6.c` | Cycle de Fetch/Execute et résolution des labels. |
| `exercice7.c` | Gestion de la pile (Stack Segment). |
| `exercice8.c` | Allocation dynamique (ES) et stratégies Best-Fit/Worst-Fit. |

---

## 💻 Compilation et Exécution

### Compilation
Le projet inclut un **Makefile**. Pour compiler l'intégralité du simulateur, utilisez la commande suivante dans votre terminal :
```bash
make
