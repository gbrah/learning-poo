#  Fondamentaux JAVA

## Historique 
**1995 : Java 1.0**
- **SDK** : Introduction du Java Development Kit (JDK) 1.0.
- **Écosystème** : Lancement de Java par Sun Microsystems, conçu pour être portable, sécurisé et multithread.

**1997 : Java 1.1**
- **API** : Introduction de l'API JDBC pour l'accès aux bases de données et de l'API RMI pour la communication entre objets distants.

**1998 : Java 2 (JDK 1.2)**
- **SDK** : Renommé en Java 2 Platform, Standard Edition (J2SE).
- **API** : Introduction des Collections Framework.
- **Écosystème** : Expansion de Java avec les éditions Enterprise (J2EE) et Micro (J2ME).

**2004 : Java 5 (JDK 1.5)**
- **SDK** : Introduction des Generics, des Enums, et des annotations.
- **API** : Ajout de l'API java.util.concurrent pour la programmation concurrente.

**2006 : Java 6 (JDK 1.6)**
- **Écosystème** : Java devient open source sous la licence GPL.

**2011 : Java 7 (JDK 1.7)**
- **SDK** : Introduction du Project Coin avec des améliorations syntaxiques.
- **API** : Ajout de l'API NIO.2 pour une meilleure gestion des fichiers.

**2014 : Java 8 (JDK 1.8)**
- **SDK** : Introduction des expressions lambda et des Streams.
- **API** : Ajout de l'API java.time pour la gestion des dates et heures.
- **Écosystème** : Java 8 devient une version très populaire grâce à ses améliorations majeures.

**2017 : Java 9 (JDK 9)**
- **SDK** : Introduction du système de modules (Project Jigsaw).

**2018 : Java 11 (JDK 11)**
- **SDK** : Java devient un logiciel LTS (Long-Term Support).
- **API** : Ajout de l'API HTTP Client.
- **Écosystème** : Adoption de Java 11 comme version LTS par de nombreuses entreprises.

**2021 : Java 17 (JDK 17)**
- **SDK** : Version LTS avec de nombreuses améliorations de performance.
- **API** : Ajout de l'API Foreign Function & Memory (en preview).
- **Écosystème** : Adoption massive de Java 17 comme version LTS.

**2023 : Java 21 (JDK 21)**
- **SDK** : Version LTS avec de nombreuses améliorations de performance.
- **API** : Ajout de l'API Pattern Matching pour les switch.
- **Écosystème** : Adoption massive de Java 21 comme version LTS.
- **Projet Loom** : Introduction des fibres légères (lightweight threads) pour une meilleure gestion de la concurrence.

**2024 : Java 23 (JDK 23)**
- **SDK** : Améliorations continues de la performance et de la sécurité.
- **API** : Introduction de nouvelles fonctionnalités pour le traitement des données et l'IA.
- **Écosystème** : Adoption croissante dans les domaines de l'IA et du machine learning, avec un soutien accru pour les frameworks modernes.

## Installation

1. Installer [JDK](https://jdk.java.net/archive/)
2. Ajouter le dossier BIN du JDK à la variable PATH `%JAVA_HOME%/bin`.

![path1](../assets/images/path1.jpg)
![path2](../assets/images/path2.jpg)


3. Compiler avec la commande `javac filename.java`.
4. Exécutez votre programme avec la commande `java nomdufichier`.


## Compilation

![compilation](../assets/images/compilation.png)

```java
C:\Users\user1>javac helloworld.java
C:\Users\user1>dir
helloworld.class
helloworld.java
C:\Users\user1>java helloworld
Hello, World!
```

## JVM

La machine virtuelle Java (JVM) est l'environnement d'exécution du langage de programmation Java. Elle est responsable de l'exécution du bytecode Java. La JVM est une machine virtuelle mise en œuvre dans le langage Java lui-même. Elle permet l'exécution de programmes Java sur un large éventail de plates-formes sans qu'il soit nécessaire de disposer d'un compilateur natif ou d'une machine virtuelle distincte. 

![jvm](../assets/images/jvm.png)


## JavaSE

Java SE est un ensemble d'outils de développement de logiciels et de bibliothèques utilisés pour développer des applications pour la plate-forme Java. Il comprend le kit de développement Java (JDK), l'environnement d'exécution Java (JRE) et les API de l'édition standard Java (SE).

![java](../assets/images/package.png)

## Documentation

La documentation Java vous permet de trouver des informations sur le langage de programmation Java, l'API Java SE et l'environnement Java SE. Vous pouvez explorer les classes, les méthodes et d'autres éléments des API, ainsi que le JDK et le JRE.

- [Java Documentation](https://devdocs.io/openjdk~21/)

## Les types primitifs

LE types primitifs sont les types de base des langages de programmation. Ils sont utilisés pour représenter des valeurs simples telles que des entiers, des flottants, des chaînes de caractères, des booléens, etc.    

En java, les types primitifs sont les suivants : 
- `int` : représente un entier
- `double` : représente un nombre à virgule flottante
- `boolean` : représente un booléen
- `char` : représente un caractère
- `byte` : représente un octet
- `short` : représente un court
- `long` : représente un long
- `float` : représente un flottant  

Chacun des types simples possède un alter-ego objet disposant de méthodes de conversion identifiable grâce à sa majuscule 
Ex : le type primitif « float » a pour équivalent objet « Float ».

```java
float f = 1.0f;
Float f2 = f;
f2.intValue(); // 1
```

Une variable en java est par convention déclarée avec une minuscule.
```java
int exempleOfInt = 10;
```

## Initialisation et constantes

Pour déclarer une variable, il faut d'abord la déclarer. 
```java
int a = 10;
```

Une variable peut être initialisée à une valeur par défaut. 
```java
int a = 10;
int b = a;
```

Une variable peut être initialisée à une valeur constante. 
```java
final int a = 10;
final int b = a;
```


## Structures de contrôles

Les structures de contrôles permettent de contrôler l'exécution d'un programme. 
```java
if (a > b) {
    System.out.println("a est plus grand que b");
} else {
    System.out.println("a est plus petit que b");
}
```

Les structures de contrôles peuvent être imbriquées. 
```java
if (a > b) {
    System.out.println("a est plus grand que b");
} else if (a < b) {
    System.out.println("a est plus petit que b");
} else {
    System.out.println("a est égal à b");
}
```
## Itérations

Les itérations permettent de parcourir un ensemble d'éléments. 
```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

Il est possible d'utiliser une variable d'itération dans une itération. 
```java
for (int i = 0; i < 10; i++) {
    for (int j = 0; j < 10; j++) {
        System.out.println(i + " " + j);
    }
}
```
## Tableaux

Les tableaux permettent de stocker un ensemble d'éléments. 
Une tableau a une taille fixe.
```java
int[] a = new int[10];
```

On peut initialiser un tableau à partir d'une liste d'éléments.
```java
int[] a = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
```

## 📚 Lectures complémentaires

- [Slides de cours de Mickael BARON](https://speakerdeck.com/mickaelbaron/programmation-orientee-objet-application-au-langage-java)


