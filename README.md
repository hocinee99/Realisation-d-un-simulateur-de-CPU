# Simulateur de CPU - LU2IN006 (Sorbonne Université)

[![Note](https://img.shields.io/badge/Note-17%2F20-brightgreen.svg)](#)
[![Language](https://img.shields.io/badge/Language-C-blue.svg)](#)

[cite_start]Ce projet consiste à coder le fonctionnement d'un CPU de manière simplifiée, en se basant sur un nombre réduit de registres et de modes d'adressage[cite: 5]. [cite_start]Il aborde des principes importants tels que la gestion de la mémoire ou encore le traitement des instructions[cite: 5].

## 🏆 Évaluation
[cite_start]Ce projet a été réalisé par **Hocine Boukhemza** et **Kaouane Walid**. Il a été validé avec la note de **17 / 20**.

---

## 🚀 Fonctionnalités Clés

### 1. Gestion de la Mémoire (Memory Handler)
* [cite_start]**Initialisation :** Allocation d'un tableau représentant la mémoire disponible[cite: 101].
* [cite_start]**Segmentation :** Gestion de segments spécifiques tels que `DS` (données), `CS` (code), `SS` (pile) et `ES` (extra-segment)[cite: 139, 223, 255, 309].
* [cite_start]**Stratégies d'Allocation :** Recherche d'un segment de mémoire libre selon les stratégies **First Fit**, **Best Fit** ou **Worst Fit**[cite: 301].
* [cite_start]**Optimisation :** Tentative de fusion d'un segment avec les segments adjacents s'ils sont libres, afin d'éviter la fragmentation et maximiser l'espace libre[cite: 112].

### 2. Unité d'Exécution & Registres
* [cite_start]**Registres Standards :** Création des registres `AX`, `BX`, `CX` et `DX`, initialisés à zéro[cite: 148].
* [cite_start]**Contrôle et Flags :** Gestion des registres `IP` (Instruction Pointer), `ZF` (Zero Flag) et `SF` (Sign Flag), tous initialisés à zéro[cite: 218].
* [cite_start]**Gestion de la Pile :** Utilisation des registres `SP` pour le pointeur de pile et `BP` pour le base pointer[cite: 255].
* **Modes d'Adressage :**
    * [cite_start]**Immédiat :** Constante numérique (ex. 42)[cite: 166].
    * [cite_start]**Registre :** (ex. BX)[cite: 170].
    * [cite_start]**Mémoire Directe :** Format `[N]` où N représente une adresse mémoire (ex. [5])[cite: 170, 191].
    * [cite_start]**Indirect par Registre :** Format `[REG]` (ex. [AX])[cite: 170, 195].
    * [cite_start]**Segment Explicite :** Utilisation d'une adresse spéciale du type `[DS: BX]`[cite: 288].

### 3. Jeu d'Instructions
* [cite_start]**Manipulation :** `MOV` en copiant la valeur pointée par la source vers la destination[cite: 202].
* [cite_start]**Arithmétique et Comparaison :** `ADD` et `CMP`[cite: 324].
* [cite_start]**Sauts :** Instructions de saut comme `JMP`, `JZ` et `JNZ`[cite: 235].
* [cite_start]**Pile :** Mnémoniques `PUSH` et `POP` pour empiler et dépiler des valeurs[cite: 275].
* [cite_start]**Mémoire Dynamique :** `ALLOC` et `FREE` pour gérer l'allocation et la libération dynamique du segment `ES` en mémoire[cite: 325].

---

## 🛠 Architecture Technique

Le simulateur repose sur des structures de données optimisées :
* [cite_start]**HashMap :** Insère un couple clé/valeur en gérant les collisions avec sondage linéaire[cite: 84]. [cite_start]Une case supprimée est remplacée par `TOMBSTONE` pour permettre la continuité du sondage[cite: 94].
* [cite_start]**Parser :** Lit un fichier avec deux sections: `DATA` pour les variables et `CODE` pour les instructions[cite: 118].
* [cite_start]**Memory Handler :** Gère une liste de segments libres et une table de hachage pour les segments alloués[cite: 99].

---

## 💻 Compilation et Exécution

### Compilation
Le projet inclut un **Makefile**. Pour compiler l'intégralité du simulateur, utilisez la commande suivante dans votre terminal :
```bash
make
