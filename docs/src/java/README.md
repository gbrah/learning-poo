# POO avec Java

## La Classe : attributs et méthodes




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

### Instanciation

### Constructeur

### Méthode principale 

### Affichage console

### La modélisation

La modélisation est la représentation d’un concept ou d’une idée sous forme de diagrammes. Elle permet de décrire les relations entre les éléments d’un système et de leur représentation graphique. 

L'`UML` est un langage de modélisation qui permet de décrire les concepts et les relations entre ces concepts. [Visual Paradigm](https://www.visual-paradigm.com/) est un outil de modélisation qui permet de créer des diagrammes UML.

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





