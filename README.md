# Labo 01 - scanf et printf

## Objectifs pédagogiques
-  Récupérer des valeurs saisies par l'utilisateur avec `scanf`.
-  Afficher des valeurs avec `printf` et maîtriser le formatage (nombre de décimales, alignement).
-  Utiliser l'instruction `if` / `else`.
-  Faire quelques calculs simples sur des nombres à virgule (`double`).
-  Editer, corriger et déboguer un programme.

## Cahier des charges
-  Il n'est pas autorisé de travailler en groupe, c'est un laboratoire individuel.
-  Le programme demande à l'utilisateur d'entrer **3 nombres à virgule** : `a`, `b` et `c`.
-  Le programme affiche ensuite :
   1. les 3 nombres saisis ;
   2. le plus grand des 3 nombres ;
   3. le plus petit des 3 nombres ;
   4. l'écart maximum entre les nombres (la différence entre le plus grand et le plus petit) ;
   5. la moyenne des 3 nombres ;
   6. pour chacun des 3 nombres, s'il est **positif**, **négatif** ou **nul**.
-  Tous les nombres sont affichés avec **2 chiffres après la virgule**.
-  Tous les nombres doivent être **alignés à droite**, les uns sous les autres (voir les exemples plus bas).
-  Le programme ne contrôle pas si autre chose que des nombres sont entrés par l'utilisateur (pas besoin de tester la valeur de retour de `scanf`).
-  Seules les fonctions `scanf` et `printf` ainsi que l'instruction `if` / `else` sont nécessaires. Les boucles ne sont **pas** autorisées.
-  Le programme retourne `0`.

## Aides

### Afficher du texte et des valeurs avec `printf`
Une chaîne de caractères est représentée entre guillemets doubles.
```C
"Une chaîne de caractères"
```

Pour afficher une chaîne de caractères, on utilise `printf`. Cette fonction prend en entrée un **format** et, éventuellement, des variables.

```C
    int age = 20;
    double taille = 1.756;
    printf("J'ai %d ans et je mesure %.2f m\n", age, taille);
```

```console
J'ai 20 ans et je mesure 1.76 m
```

Après le signe `%`, on retrouve le type de format que l'on souhaite :

| Format | Type      | Exemple                         |
|--------|-----------|---------------------------------|
| `%d`   | `int`     | `printf("%d", 12);`             |
| `%f`   | `double`  | `printf("%f", 3.5);` → `3.500000` |
| `%.2f` | `double`  | `printf("%.2f", 3.5);` → `3.50`   |

`\n` permet de passer à la ligne suivante.

Vous pouvez regarder sur la carte jaune pour trouver d'autres manières de formater une chaîne de caractères.

### Aligner des nombres avec `printf`
On peut indiquer une **largeur minimale** entre le `%` et le type. Si le nombre est plus court, `printf` ajoute des espaces **à gauche**, ce qui aligne les nombres à droite.

```C
    printf("[%8.2f]\n", 3.5);
    printf("[%8.2f]\n", -123.456);
    printf("[%8.2f]\n", 10.0);
```

```console
[    3.50]
[ -123.46]
[   10.00]
```

Ici `%8.2f` signifie : au moins 8 caractères au total (signe, point et décimales compris), dont 2 chiffres après la virgule.

> Pour que les nombres soient bien alignés, il faut aussi que les textes placés **avant** les nombres aient tous la même longueur.

### Lire une valeur avec `scanf`
`scanf` permet de lire une valeur tapée au clavier par l'utilisateur et de la stocker dans une variable.

```C
    double taille;

    printf("Entrer votre taille : ");
    scanf("%lf", &taille);

    printf("Vous mesurez %.2f m\n", taille);
```

Attention à deux points importants :
-  Pour lire un `double` avec `scanf`, il faut utiliser `%lf` (et pas `%f`).
-  Il faut mettre un `&` devant le nom de la variable. Sans le `&`, le programme compile peut-être, mais plante à l'exécution.

L'utilisateur doit utiliser le **point** comme séparateur décimal : `3.5` et pas `3,5`.

### Déboguer pas à pas
Le débogueur permet d'exécuter le programme **une ligne à la fois** et d'observer la valeur des variables.

1. Poser un **point d'arrêt** : cliquer dans la marge à gauche du numéro de ligne (un point rouge apparaît), par exemple sur le premier `printf`.
2. Appuyer sur **`F5`** : le programme est compilé puis démarre. Il s'arrête sur le point d'arrêt.
3. Avancer avec les touches suivantes :

| Touche      | Action                                                         |
|-------------|----------------------------------------------------------------|
| `F10`       | Exécuter la ligne courante et passer à la suivante (pas à pas) |
| `F11`       | Entrer dans la fonction appelée sur la ligne courante          |
| `F5`        | Continuer jusqu'au prochain point d'arrêt (ou la fin)          |
| `Shift+F5`  | Arrêter le débogage                                            |

Pendant l'arrêt, la valeur des variables est visible dans le panneau **Variables** à gauche, ou en passant la souris sur une variable dans le code.

Lorsque le programme exécute un `scanf`, il attend la saisie : cliquer dans le **terminal** en bas, taper le nombre puis `Entrée`.


## Tâches à effectuer
- Exécuter VS Code
- Comme pour le laboratoire `#1` (voir document info-resume.pdf)
  - Cloner le répertoire du laboratoire sur votre ordinateur
  - Ouvrir le code dans un `container`
- Avant d'écrire le code, réfléchissez sur papier à la manière de trouver le plus grand et le plus petit des 3 nombres **uniquement avec des `if`**.
- Lancer votre programme en debug avec `F5`, avancer **pas à pas** (`F10`) après chaque `scanf` et vérifier dans le panneau **Variables** que `a`, `b` et `c` contiennent bien les valeurs saisies. Continuer ensuite l'exécution avec `F5`.

## Affichage du programme
Voici trois exemples d'exécution du programme. Vous pouvez modifier les textes, mais les nombres doivent rester alignés.

```console
$ ./app
Entrer le nombre a : 3.5
Entrer le nombre b : -12.25
Entrer le nombre c : 7

Nombre a     :       3.50
Nombre b     :     -12.25
Nombre c     :       7.00

Plus grand   :       7.00
Plus petit   :     -12.25
Ecart max    :      19.25
Moyenne      :      -0.58

Le nombre a est positif
Le nombre b est negatif
Le nombre c est positif
```

```console
$ ./app
Entrer le nombre a : 0
Entrer le nombre b : 1234.5
Entrer le nombre c : -8.75

Nombre a     :       0.00
Nombre b     :    1234.50
Nombre c     :      -8.75

Plus grand   :    1234.50
Plus petit   :      -8.75
Ecart max    :    1243.25
Moyenne      :     408.58

Le nombre a est nul
Le nombre b est positif
Le nombre c est negatif
```

```console
$ ./app
Entrer le nombre a : -4
Entrer le nombre b : -1.5
Entrer le nombre c : -20

Nombre a     :      -4.00
Nombre b     :      -1.50
Nombre c     :     -20.00

Plus grand   :      -1.50
Plus petit   :     -20.00
Ecart max    :      18.50
Moyenne      :      -8.50

Le nombre a est negatif
Le nombre b est negatif
Le nombre c est negatif
```
