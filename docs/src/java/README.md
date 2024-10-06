# POO avec Java

## La Classe

Elle est constituée de : 
* Données ce qu'on appelle des attributs 
* Procédures et/ou des fonctions ce qu'on appelle des méthodes

Une classe est un modèle de définition pour des objets 
* Ayant même structure (même ensemble d'attributs)
* Ayant même comportement (même méthodes)
* Ayant une sémantique commune

En java une classe a les caractéristiques suivantes :
* Un nom de fichier « NomDeClasse.java »
* Une classe commence toujours par une majuscule

![java](../assets/images/classejava.png)

exemple de classe voiture, avec des attributs et des méthodes
:::details  Classe Voiture
```java
public class Voiture {
    int puissance;
    boolean estDemarree = false;
    float vitesse;
    public void demarre() {
          estDemarree = true;
    }
  
    public int deQuelPuissance {
        return puissance;
    }

    public void accelere(float uneVitesse) {
        uneVitesse = vitesse;
    }
}
```
:::

Les `attributs` sont des variables qui sont stockées dans une classe.
* Variables « globales » de la classe : Accessibles dans toutes les méthodes de la classe
* Variable simple n’est visible uniquement qu’à l’intérieur du bloc d’une méthode.

Les `méthodes` sont des fonctions qui sont stockées dans une classe.


### La classe statique

Une classe est dite statique si elle possède des méthodes statiques. Les méthodes statiques sont des méthodes qui peuvent être appelées sans créer d’instance d’une classe.

Exemple :

```java
public class Statique {
    public static void exempleStatic() {
        System.out.println("Static");
    }
    public static void main(String[] args) {    
       Statique.exempleStatic(); // la methode statique est appelée sans créer d’instance de la classe
    }
```

## L’Objet 

L'objet est une instance d'une classe. A une définition de classe on peut instancier une infinité d'objets.

### Instanciation

* Les objets sont des représentations dynamiques, du modèle défini pour eux au travers de la classe
* La création d’un objet à partir d’une classe est appelée une instanciation
* Une classe permet d'instancier (créer) plusieurs objets
* Chaque objet est instance d'une classe et une seule 

![instanciation](../assets/images/instanciation.png)

### Constructeur

On a utilisé le constructeur par défaut sans paramètre :

```java
    public static void main(String[] args) {
        Voiture audi = new Voiture(); // Instanciation
        voiture.demarre();
        voiture.deQuelPuissance();
        voiture.accelere(10);
    }
```

* On ne sait pas comment se construit la « Voiture »
* Les valeurs des attributs au départ sont indéfinies et identique pour chaque objet (puissance, etc.) 

#### Rôle du constructeur en Java 
* Effectuer certaines initialisations nécessaires pour le nouvel objet créé
* Toute classe Java possède au moins un constructeur
* Si une classe ne définit pas explicitement de constructeur, un constructeur par défaut sans arguments et qui n’effectue aucune initialisation particulière est invoquée

```java
public class Voiture {
    int puissance;
    boolean estDemarree = false;
    float vitesse;
    public Voiture(Integer puissance) { //Constructeur 1
        this.puissance = puissance;
    }
    public Voiture(Integer puissance, Boolean estDemarree, Float vitesse) { //Constructeur 2
        this.puissance = puissance;
        this.estDemarree = estDemarree;
        this.vitesse = vitesse;
    }
    ...

    public static void main(String[] args) {
        Voiture voiture = new Voiture(10, true, 10.0f);
        Voiture voiture2 = new Voiture(10);
    }
}
```

### Methode principale

La méthode principale est la méthode qui est appelée lorsque l’on appelle la classe. C'est le point d'entrée de la classe.

* La methode principale est équivalente à la fonction main du C/C++
* Elle permet de récupérer des arguments transmis au programme au moment de son lancement

Exemple : 
```java
public class Main {
    public static void main(String[] args) {
        System.out.println(args[0]); // args[0] est le premier argument passé à la méthode main
        Voiture voiture = new Voiture();
        voiture.demarre();
        voiture.deQuelPuissance();
        voiture.accelere(10);
    }
}
```

### Affichage console

### La modélisation

La modélisation est la représentation d’un concept ou d’une idée sous forme de diagrammes. Elle permet de décrire les relations entre les éléments d’un système et de leur représentation graphique. 

L'`UML` est un langage de modélisation qui permet de décrire les concepts et les relations entre ces concepts. [Visual Paradigm](https://www.visual-paradigm.com/) est un outil de modélisation qui permet de créer des diagrammes UML.

![paradigm](../assets/images/uml.png)

## Héritage 

L'héritage est la notion de dériver des caractéristiques d'un objet d'un autre objet. 

```java
public class A {
    private int a;
    public int getA() {
        return a;
    }
}

public class B extends A {
    private int b;
    public int getB() {
        return b;
    }
}
```

Dans l'exemple ci-dessus, l'objet B hérite de l'objet A. Il possède donc les mêmes caractéristiques que l'objet A.

Pour accéder aux méthodes d'un objet hérité, on peut utiliser le mot-clé `super` :
```java
public class A {
    private int a;
    public int getA() {
        return a;
    }
}

public class B extends A {
    private int b;
    public int getB() {
        return b;
    }
    public int getC() {
        return super.getA() + b;
    }
}

public static void main(String[] args) {
    B b = new B();
    b.getA(); // erreur
    b.getB(); // ok
    b.getC(); // ok
}
```

le mot clef `override` permet de définir une méthode qui remplace une méthode héritée. 

```java
public class A {
    private int a;
    public int getA() {
        return a;
    }
}

public class B extends A {
    private int b;
    public int getB() {
        return b;
    }
    public int getC() {
        return super.getA() + b;
    }
}
public class C extends B {
    @Override
    public int getC() {
        return super.getC() + 1;
    }
}
``` 
## Abstraction

L'abstraction est la notion de définir une classe abstraite qui ne contient pas de méthode. 
```java
abstract class A {
    abstract int getA();
}
```

On peut utiliser une classe abstraite comme classe de base pour définir une classe qui hérite de la classe abstraite.
```java
class B extends A {
    @Override
    public int getA() {
        return 1;
    }
}
```

## Interface

L'interface est une collection de méthodes, un contrat. Elle permet de définir les méthodes qui doivent être implémentées par un objet. Ces méthodes sont definis de manière abstraite et ne contiennent pas de code dans l'interface. Elles seront implémentées par les classes qui implémentent l'interface.

```java
public interface A {
    int getA();
}

public class B implements A {
    private int a;
    public int getA() {
        return a;
    }
}
```

Pour utiliser une interface, on peut créer un objet qui implémente l'interface.
```java
A a = new B();
a.getA(); // ok
```
## 🧪 Modélisation d'une voiture
## 🧪 Modélisation d'un parc de voitures
## 🧪 Modélisation d'un Zoo
## 🧪 Modélisation d'une école
## 🧪 Modélisation d'un fastfood
## 🧪 Projet d'application de Quiz





