# Simulateur de CPU - LU2IN006 (Sorbonne Université)

[![Note](https://img.shields.io/badge/Note-17%2F20-brightgreen.svg)](#)
[![Language](https://img.shields.io/badge/Language-C-blue.svg)](#)

[cite_start]Ce projet consiste en la conception et l'implémentation d'un **simulateur de processeur (CPU)** complet en langage C[cite: 2, 5]. [cite_start]Il couvre la gestion de la mémoire, l'interprétation d'instructions assembleur, et la manipulation de structures de données complexes comme les tables de hachage et les listes chaînées[cite: 99, 119].

## 🏆 Évaluation
Ce projet a été réalisé dans le cadre de l'unité **LU2IN006 (Structures de Données)** et a obtenu la note de **17 / 20**.

---

## 🚀 Fonctionnalités Clés

### 1. Gestion de la Mémoire (Memory Handler)
* [cite_start]**Segmentation :** Gestion des segments `CS` (code), `DS` (données), `SS` (pile) et `ES` (extra-segment)[cite: 131, 160, 253, 309].
* [cite_start]**Stratégies d'Allocation :** Implémentation des algorithmes `First-Fit`, `Best-Fit` et `Worst-Fit` pour trouver des blocs libres[cite: 301].
* [cite_start]**Gestion des segments libres :** Utilisation d'une `free_list` (liste chaînée) pour suivre les blocs disponibles et fusion des segments adjacents pour limiter la fragmentation[cite: 28, 112].

### 2. Unité d'Exécution & Registres
* [cite_start]**Registres supportés :** `AX`, `BX`, `CX`, `DX` (généraux), `IP` (Instruction Pointer), `SP`/`BP` (Stack), `ZF`/`SF` (Flags) et `ES` (Error/Extra segment)[cite: 148, 218, 255, 305].
* **Modes d'Adressage :**
    * [cite_start]Immédiat (ex: `42`)[cite: 166].
    * [cite_start]Direct par registre (ex: `AX`)[cite: 170].
    * [cite_start]Mémoire directe (ex: `[5]`)[cite: 170].
    * [cite_start]Indirect par registre (ex: `[AX]`)[cite: 170].
    * [cite_start]Adressage avec segment explicite (ex: `[ES:BX]`)[cite: 295].

### 3. Jeu d'Instructions
* [cite_start]**Manipulation :** `MOV` (copie de valeur)[cite: 202].
* [cite_start]**Arithmétique & Comparaison :** `ADD` et `CMP` (mise à jour des flags ZF/SF)[cite: 234, 324].
* [cite_start]**Contrôle de flux :** `JMP`, `JZ`, `JNZ` (sauts conditionnels et inconditionnels)[cite: 235].
* [cite_start]**Pile :** `PUSH` et `POP` pour la gestion de la pile d'exécution[cite: 275].
* [cite_start]**Gestion dynamique :** `ALLOC` et `FREE` pour le segment `ES`[cite: 325].

---

## 🛠 Architecture Technique

Le simulateur repose sur des structures de données optimisées :
* [cite_start]**Table de Hachage (HashMap) :** Utilisée pour le contexte des registres, les labels, les adresses mémoire et le pool de constantes[cite: 52, 45, 47, 60]. [cite_start]Elle gère les collisions par **sondage linéaire**[cite: 84].
* [cite_start]**Analyseur Syntaxique (Parser) :** Découpe le code source en sections `.DATA` et `.CODE`, extrait les mnémoniques et résout les labels/variables en adresses réelles[cite: 118, 129, 211].

---

## 💻 Compilation et Exécution

### Compilation
Pour compiler le projet, utilisez simplement le `Makefile` fourni en tapant dans votre terminal :
```bash
make
