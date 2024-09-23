# 02 - Premiers programmes

## Récapitulatif

``` mermaid
%%{init: {'theme':'neutral'}}%%
mindmap
  root((Langage C))
    Compilateur
        langage compilé != langage interprété
            Python, PHP
        4 étapes
            1 - Pré-processeur
                Suppression des commentaires
                Récupération du contenu des bibliothèques
            2 - Compilateur
                Traduction en assembleur
            3 - Assemblage
                Traduction en binaire
            4 - Editeur de liens
                Récupération des bibliothèques pré-compilées
                Ajout des routines pour l'exécution
    Variables
        Types
            Entiers
                char 1 octet
                short 2 octets
                int 4 octets
                long 4 octets
                long long 8 octets
            Réels
                ["float 
                (précision à 6 chiffres)"]
                double
        Identificateur
    Fonctions
        Principale main
            Point d'entrée du programme
        Bibliothèques 
            #include
            stdio.h
                ["printf()"]
                ["scanf()"]
            math.h
                ["sqrt()"]
    Opérateurs
        Arithmétiques
        Relationnels
        Logiques
        Affectation composée
        Incrémentaux
        Taille
        Adresse
    Logique
        if...else if...else
```

## Exercice 1

Créer un programme `exo1.c` qui demande à l'utilisateur son année de naissance et lui donne son âge.

```
> exo1.exe
Annee de naissance : 1984
Vous avez 38 ans !
```

> On sera plus précis dans l'exercice 3

??? success "Correction"

    ```c
    #include <stdio.h>

    int main() {
        int annee;

        printf("Annee de naissance : ");
        scanf("%d", &annee);
        //          🡑 on oublie pas le &, sinon gare à l'erreur de segmentation !
        //                                                               🡑 C'est ce qui arrive quand 
        //                                                                 on écrit dans une zone 
        //                                                                 mémoire qui ne nous est pas 
        //                                                                 allouée ⛔

        printf("Vous avez %d ans !", 2024 - annee);

        return 0;
    }
    ```

## Exercice 2

Créer un programme `exo2.c` qui demande à l'utilisateur son année, puis son mois, puis son jour de naissance et lui souhaite un joyeux anniversaire **si** c'est aujourd'hui.

> Réfléchir sur le papier

> La date du jour doit être définie dans des constantes.

```
// Si nous sommes le 13/09 😄

> exo2.exe
Annee de naissance : 1984
Mois de naissance : 9
Jour de naissance : 13
Joyeux anniversaire !

> exo2.exe
Annee de naissance : 1984
Mois de naissance : 9
Jour de naissance : 7
Joyeux non-anniversaire !
```

??? success "Correction"

    ```c
    #include <stdio.h>

    int main() {
        int year, month, day;
        const int today_year  = 2023, 
                  today_month = 9, 
                  today_day   = 26;

        printf("Annee de naissance : ");
        scanf("%d", &year);
        printf("Mois de naissance : ");
        scanf("%d", &month);
        printf("Jour de naissance : ");
        scanf("%d", &day);

        if (day == today_day && month == today_month) {
            printf("Joyeux anniversaire !");
        }
        else {
            printf("Joyeux non-anniversaire !");
        }

        return 0;
    }
    ```

## Exercice 3

Créer un programme exo3.c qui demande à l'utilisateur son année, puis son mois, puis son jour de naissance et lui donne son âge plus précisément qu'à l'exercice 1.

```
> ./exo3.exe
Année de naissance : 1984
Mois de naissance : 12
Jour de naissance : 25
Vous avez 37 ans !

> ./exo3.exe
Année de naissance : 1984
Mois de naissance : 9
Jour de naissance : 7
Vous avez 38 ans !
```

??? success "Correction"
    
    Solution détaillée :

    ```c
    #include <stdio.h>

    int main() {
        int year, month, day;
        const int TODAY_YEAR = 2024, 
                TODAY_MONTH = 9, 
                TODAY_DAY = 17;

        printf("Annee de naissance : ");
        scanf("%d", &year);
        printf("Mois de naissance : ");
        scanf("%d", &month);
        printf("Jour de naissance : ");
        scanf("%d", &day);

        // L'anniversaire de l'utilisateur est déjà passé : 
        // (Mois avant le mois actuel)
        if (month < TODAY_MONTH) {
            printf("Vous avez %d ans !", TODAY_YEAR - year);
        }

        // (Ce mois-ci mais avant aujourd'hui ou aujourd'hui)
        else if (month == TODAY_MONTH && day <= TODAY_DAY) {
            printf("Vous avez %d ans !", TODAY_YEAR - year);
        }

        // L'anniversaire n'est pas encore passé :
        else {
            printf("Vous avez %d ans !", TODAY_YEAR - year - 1);
        }

        return 0;
    }
    ```

    Solution condensée :

    ```c
    #include <stdio.h>

    int main() {
        int year, month, day;
        const int TODAY_YEAR = 2024, 
                TODAY_MONTH = 9, 
                TODAY_DAY = 17;

        printf("Annee de naissance : ");
        scanf("%d", &year);
        printf("Mois de naissance : ");
        scanf("%d", &month);
        printf("Jour de naissance : ");
        scanf("%d", &day);
        
        if (month < TODAY_MONTH || (month == TODAY_MONTH && day <= TODAY_DAY)) {
            printf("Vous avez %d ans !", TODAY_YEAR - year);
        }
        else {
            printf("Vous avez %d ans !", TODAY_YEAR - year - 1);
        }

        return 0;
    }
    ```

## Exercice 4

Créer un programme exo4.c qui demande un entier à l'utilisateur puis lui affiche la conversion en hexadécimal et en octal.

```
> ./exo4.exe
Nombre à convertir : 42
Hexadécimal : 2A
Octal : 52
```

??? success "Correction"

    ![Please... wait...](../images/meme/waiting-kid.gif)

## Exercice 5

Créer un programme exo5.c qui convertit des composantes RGB de décimal en hexadécimal.

```
> ./exo5.exe
Couleur en décimal : 255 204 0
Couleur en hexa    : #FFCC00
```

??? danger "Aller plus loin"
    
    Programmer l'inverse.
    
    ```
    > ./exo5.exe
    Couleur en hexa    : #FFCC00
    Couleur en décimal : 255 204 0
    ```

??? success "Correction"

    ![Please... wait...](../images/meme/waiting-zootopia.gif)

## Exercice 6

Créer un programme exo6.c qui demande deux entiers à l’utilisateur puis donne le résultat de leur division.

```
> ./exo6.exe
Entier 1 : 12
Entier 2 : 5
Resultat : 12 / 5 = 2.40000
```

??? success "Correction"

    ![Please... wait...](../images/meme/waiting-kid.gif)

## Exercice 7

Créer un programme exo7.c qui demande un entier strictement positif à l'utilisateur et ne s’arrête pas **tant qu**’il n’a pas une réponse qui convient.

```
> ./exo7.exe
Entrer un nombre strictement positif : -420
Ce nombre n'est pas strictement positif.
Entrer un nombre strictement positif : 0
Ce nombre n'est pas strictement positif.
Entrer un nombre strictement positif : 23
OK ! Merci...
```

??? danger "Aller plus loin"
    
    Compter le nombre de tentatives :
    
    ```
    > ./exo7.exe
    Entrer un nombre strictement positif : 23
    Chapeau ! Du premier coup !
    
    > ./exo7.exe
    Entrer un nombre strictement positif : -420
    Ce nombre n'est pas strictement positif.
    Entrer un nombre strictement positif : 0
    Ce nombre n'est pas strictement positif.
    Entrer un nombre strictement positif : 23
    Ah quand même... 3 fois pour y arriver :(
    ```

??? success "Correction"

    ![Please... wait...](../images/meme/waiting-bean.gif)