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


###  Methode statique

 Les méthodes statiques sont des méthodes qui peuvent être appelées sans créer d’instance d’une classe.

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
        audi.demarre();
        audi.deQuelPuissance();
        audi.accelere(10);
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

### Transtypage 
Le transtypage, ou casting, est une technique en Java qui permet de convertir une variable d'un type de données à un autre. Cela peut être nécessaire lorsque vous travaillez avec des types de données différents et que vous devez les manipuler ensemble.

Le transtypage d'objets complexes est souvent utilisé dans le contexte de l'héritage et des interfaces. En Java, vous pouvez convertir un objet d'une classe parente en un objet d'une classe enfant (transtypage descendant) ou vice versa (transtypage ascendant).

```java

class Animal {
    public void faireDuBruit() {
        System.out.println("L'animal fait du bruit");
    }
}

class Chien extends Animal {
    public void aboyer() {
        System.out.println("Le chien aboie");
    }
}

public class TranstypageObjetExample {
    public static void main(String[] args) {
        // Transtypage ascendant (implicite)
        Animal animal = new Chien();
        animal.faireDuBruit(); // Appelle la méthode de la classe parente

        // Transtypage descendant (explicite)
        if (animal instanceof Chien) {
            Chien chien = (Chien) animal;
            chien.aboyer(); // Appelle la méthode de la classe enfant
        }
    }
}
```
Dans cet exemple, nous avons une classe Animal et une classe Chien qui hérite de Animal. Le transtypage ascendant est implicite et permet de traiter un Chien comme un Animal. Le transtypage descendant est explicite et nécessite une vérification avec instanceof pour s'assurer que l'objet peut être converti en type Chien avant d'appeler des méthodes spécifiques à la classe Chien.

### Affichage console

### La modélisation

La modélisation est la représentation d’un concept ou d’une idée sous forme de diagrammes. Elle permet de décrire les relations entre les éléments d’un système et de leur représentation graphique. 

L'`UML` est un langage de modélisation qui permet de décrire les concepts et les relations entre ces concepts. [Visual Paradigm](https://www.visual-paradigm.com/) est un outil de modélisation qui permet de créer des diagrammes UML.

![paradigm](../assets/images/uml.png)

## 🧪 Modélisation d'une voiture

Modelisez une voiture en Java.
Une voiture possède : 
* Puissance, 
* Est-elle demarrée, 
* Vitesse
* Un reservoir de carburant
* une immatriculation
* 4 phares avant et arrière
* des freins

Une voiture doit pouvoir : 
* Demarrer, 
* Accelerer, 
* Ralentir
* Freiner
* Allumer ses phares
* éteindre ses phares 

Simulation: 
Je souhaite creer 4 voitures de différentes puissances et simuler leur démarrage, accélération, ralentissement, freinage, allumage et éteindre des phares

::: details Solution

Main.java
```java
public class Main {
    public static void main(String[] args) {
        Voiture[] voitures = {
            new Voiture(100, "AB123CD", 50),
            new Voiture(200, "EF456GH", 60),
            new Voiture(300, "IJ789KL", 70),
            new Voiture(400, "MN101OP", 80)
        };
        for(Voiture voiture : voitures) {
            voiture.demarrer();
            voiture.accelerer();
            voiture.freiner();
            voiture.ralentir();
            voiture.allumerPhares();
            voiture.eteindrePhares();
        }
    }
}
```

Voiture.java
```java
public class Voiture {
    Integer puissance;
    Boolean estDemarree;
    Integer vitesse;
    String immatriculation;
    Integer reservoirEnLitres;
    Boolean[] phares = new Boolean[4];
    Boolean[] freinsAvantArriere = new Boolean[2];

    Voiture(Integer puissance, String immatriculation, Integer reservoirEnLitres){
        this.puissance = puissance;
        estDemarree = false;
        vitesse = 0;
        phares[0] = false;
        phares[1] = false;
        phares[2] = false;
        phares[3] = false;
        freinsAvantArriere[0] = false;
        freinsAvantArriere[1] = false;
        this.immatriculation = immatriculation;
        this.reservoirEnLitres = reservoirEnLitres;

    }

    public void demarrer() {
        if(estDemarree) {
            printVoiture("La voiture est déjà démarrée");
            return;
        }
        estDemarree = true;
        printVoiture("La voiture démarre");
    }

    public void accelerer() {

        if(!estDemarree) {
            printVoiture("La voiture n'est pas démarrée");
            return;
        }

        if(vitesse < 200) {
            vitesse += 10;
            printVoiture("La voiture accélère. Elle est a " + vitesse + " km/h");
            return;
        }
        printVoiture("La voiture est déjà à sa vitesse maximale");

    }

    public void ralentir() {
        if(!estDemarree) {
            printVoiture("La voiture n'est pas démarrée");
            return;
        }
        if(vitesse > 0) {
            vitesse -= 10;
            printVoiture("La voiture ralentit. Elle est a " + vitesse + " km/h");
            return;
        }
        printVoiture("La voiture est déjà à l'arrêt");

    }

    public void freiner() {
        if(!estDemarree) {
            printVoiture("La voiture n'est pas démarrée");
            return;
        }
        freinsAvantArriere[0] = true;
        freinsAvantArriere[1] = true;
        if(vitesse > 0) {
            printVoiture("La voiture ralenti grâce aux freins");
            vitesse -= 10;
        }else {
            printVoiture("La voiture ne ralenti pas car elle est déjà à l'arrêt");
        }
        freinsAvantArriere[0] = false;
        freinsAvantArriere[1] = false;
    }

    public void allumerPhares() {
        if(phares[0] && phares[1] && phares[2] && phares[3]) {
            printVoiture("Les phares sont déjà allumés");
            return;
        }
        phares[0] = true;
        phares[1] = true;
        phares[2] = true;
        phares[3] = true;

        printVoiture("Les phares sont allumés");
    }
    public void eteindrePhares() {
        if(!phares[0] && !phares[1] && !phares[2] && !phares[3]) {
            printVoiture("Les phares sont déjà éteints");
            return;
        }
        phares[0] = false;
        phares[1] = false;
        phares[2] = false;
        phares[3] = false;
        printVoiture("Les phares sont éteints");
    }

    public void printVoiture(String message){
        System.out.println("Voiture " + immatriculation + " : " + message);
    }

}
```

:::

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

## 🧪 Modélisation d'un parc de voitures

Je souhaite gérer un `parc de vehicules`

Ces `vehicules` peuvent être :
* des 2 roues, 
* des voitures 
* ou des camions

Un vehicule possède : 
* Une immatriculation, 
* un modèle, 
* un prix argus, 
* un kilométrage,
* une date de mise en circulation
* une cylindré, 
* un carburant , 
* un etat ( neuf, quasi neuf, usagé), 
* une liste des défauts, 
* liste d'options

Une voiture possède : 
* un nombre de portes, 
* une nombre de places, 
* une taille de coffres

Un vehicule doit pouvoir: 
* se garer, 
* demarrer, 
* rouler

La vitesse max d'une voiture une `180km/h`

Une voiture implemente : 
* accelerer, 
* ralentir, 
* afficher la vitesse

Dans la simulation: 
Le parc de vehicules s'appelle AutoPlus et possède 1 deux roues, deux voitures de votre choix et deux camions

::: details Solution

Main.java
```java
import java.util.Date;

public class Vehicule {

    enum Etat {
        NEUF,
        QUASI_NEUF,
        USAGE,
    }

    String immatriculation;
    String modele;
    Integer PrixArgus;
    Integer Kilometrage;
    Date dateMiseEnCirculation;
    Integer cylindree;
    String carburant;
    Etat etat;
    String[] listeDefauts;
    String[] listeOptions;
    Boolean estGare;

    public Vehicule(String immatriculation, String modele, Integer prixArgus, Integer kilometrage, Date dateMiseEnCirculation, Integer cylindree, String carburant, Etat etat, String[] listeDefauts, String[] listeOptions) {
        this.immatriculation = immatriculation;
        this.modele = modele;
        PrixArgus = prixArgus;
        Kilometrage = kilometrage;
        this.dateMiseEnCirculation = dateMiseEnCirculation;
        this.cylindree = cylindree;
        this.carburant = carburant;
        this.etat = etat;
        this.listeDefauts = listeDefauts;
        this.listeOptions = listeOptions;
        this.estGare = false;
    }

    public void seGarer() {
        System.out.println("Je me gare");
        this.estGare = true;
    }

    public void demarrer() {
        System.out.println("Je démarre");
        this.estGare = false;
    }
    public void rouler(Integer vitesse) {
        System.out.println("Je roule à " + vitesse + " km/h");
    }
}
```

Voiture.java
```java
import java.util.Date;

public class Voiture extends Vehicule  implements GestionDeVitesseImpl{

    Integer nombreDePortes;
    Integer nombreDePlaces;
    Integer tailleDuCoffre;
    final Integer vitesseMax = 180;

    public Voiture(String immatriculation, String modele, Integer prixArgus, Integer kilometrage, Date dateMiseEnCirculation, Integer cylindree, String carburant, Etat etat, String[] listeDefauts, String[] listeOptions, Integer nombreDePortes, Integer nombreDePlaces, Integer tailleDuCoffre) {
        super(immatriculation, modele, prixArgus, kilometrage, dateMiseEnCirculation, cylindree, carburant, etat, listeDefauts, listeOptions);
        this.nombreDePortes = nombreDePortes;
        this.nombreDePlaces = nombreDePlaces;
        this.tailleDuCoffre = tailleDuCoffre;
    }

    @Override
    public void rouler(Integer vitesse) {
        if (vitesse <= vitesseMax) {
            afficherVitesse();
        } else {
            afficherVitesse();
        }
    }


    @Override
    public void accelerer(Integer ajoutVitesse) {
        if(vitesse + ajoutVitesse <= vitesseMax) {
            vitesse += ajoutVitesse;
            afficherVitesse();
        } else {
            vitesse = vitesseMax;
            afficherVitesse();
        }

    }

    @Override
    public void ralentir(Integer ajoutVitesse) {
        if(vitesse - ajoutVitesse >= 0) {
            vitesse -= ajoutVitesse;
            afficherVitesse();
        } else {
            vitesse = 0;
            afficherVitesse();
        }

    }

    @Override
    public void afficherVitesse() {
        System.out.println("Je roule à " + vitesse + " km/h");

    }


}
```

DeuxRoues.java
```java
import java.util.Date;

public class DeuxRoues extends Vehicule{
    public DeuxRoues(String immatriculation, String modele, Integer prixArgus, Integer kilometrage, Date dateMiseEnCirculation, Integer cylindree, String carburant, Etat etat, String[] listeDefauts, String[] listeOptions) {
        super(immatriculation, modele, prixArgus, kilometrage, dateMiseEnCirculation, cylindree, carburant, etat, listeDefauts, listeOptions);
    }
}
```

Camion.java
``` java
import java.util.Date;

public class Camion extends Vehicule{

    public Camion(String immatriculation, String modele, Integer prixArgus, Integer kilometrage, Date dateMiseEnCirculation, Integer cylindree, String carburant, Etat etat, String[] listeDefauts, String[] listeOptions) {
        super(immatriculation, modele, prixArgus, kilometrage, dateMiseEnCirculation, cylindree, carburant, etat, listeDefauts, listeOptions);
    }
}
```

Main.java
```java
import java.util.Date;

public class Main {
    public static void main(String[] args) {

        DeuxRoues moto = new DeuxRoues("1234", "Yamaha", 1000, 1000, new Date(), 100, "Essence", Vehicule.Etat.NEUF, new String[]{"Pneu crevé"}, new String[]{"ABS"});
        Voiture voiture1= new Voiture("1234", "Peugeot", 1000, 1000, new Date(), 100, "Essence", Vehicule.Etat.NEUF, new String[]{"Pneu crevé"}, new String[]{"ABS"}, 5, 5, 500);
        Voiture voiture2= new Voiture("1234", "Peugeot", 1000, 1000, new Date(), 100, "Essence", Vehicule.Etat.NEUF, new String[]{"Pneu crevé"}, new String[]{"ABS"}, 5, 5, 500);
        Camion camion1 = new Camion("1234", "Peugeot", 1000, 1000, new Date(), 100, "Essence", Vehicule.Etat.NEUF, new String[]{"Pneu crevé"}, new String[]{"ABS"});
        Camion camion2 = new Camion("1234", "Peugeot", 1000, 1000, new Date(), 100, "Essence", Vehicule.Etat.NEUF, new String[]{"Pneu crevé"}, new String[]{"ABS"});

        ParcDeVehicule autoPlus = new ParcDeVehicule("AutoPlus", new Vehicule[]{moto, voiture1, voiture2, camion1, camion2});

        System.out.println(autoPlus.toString());
        
        autoPlus.vehicules[0].rouler(230);
        autoPlus.vehicules[1].rouler(200);
    }
}
```

ParcDeVehicule.java 
``` java
import java.util.Arrays;

public class ParcDeVehicule {
    String name;
    Vehicule[] vehicules;

    public ParcDeVehicule(String name, Vehicule[] vehicules) {
        this.name = name;
        this.vehicules = vehicules;
    }

    @Override
    public String toString() {
        return "ParcDeVehicule{" +
                "name='" + name + '\'' +
                ", vehicules=" + Arrays.toString(vehicules) +
                '}';
    }


}
```
GestionDeVitesseImpl.java
```java
public interface GestionDeVitesseImpl {

    public void accelerer(Integer ajoutVitesse);
    public void ralentir(Integer ajoutVitesse);
    public void afficherVitesse();
}
```



:::

## 🧪 Modélisation d'un Zoo

Je souhaite modéliser le comportement des animaux d'un `Zoo`
Un `animal` est caractérisé par : 
* Un nom, 
* Une taille,
* Un age, 
* Une durée de vie,
* Un crie Un poids, 
* Espece protégé, 
* Espece éteinte

Un animal doit pouvoir : 
* Vieillir jusqu'à son age.
* Crier

J'ai 4 grandes familles d'animaux dans mon Zoo : Les reptiles, Les oiseaux,
Les poissons, Les Mammifères

Les Mamifères on la particularité :  
* d'avoir un genre (male/femelle), 
* un type de motricité (marcher/nager/)

Les mamifères implémente :
* Allaiter si c'est une femelle 3 fois par jours
* Prodiguer des Soins parentaux 1 fois par jours

Simulation : 
* Vous simulez 100 années qui s'écoulent soit 100 fois 365 Jours et simulez la vie d'un mamifère (Crier , Vieillir, Allaiter, Prodiguer des soins)

::: details Solution

Main.java
```java
public class Main {
    public static void main(String[] args) {
        Integer YEARS = 100;
        Integer DAYS_COUNTER= 365;
        Zoo zoo = new Zoo();
        ArrayList<Animal> animals = zoo.getAnimals();

        while(YEARS > 0){
            while (DAYS_COUNTER > 0){
                System.out.println("Days left for Year : "+YEARS +" => "+ DAYS_COUNTER);
                for (Animal animal : animals) {
                    animal.scream();
                   if(animal instanceof Mammal){
                       ((Mammal) animal).breastFeed();
                       ((Mammal) animal).childCare();
                       ((Mammal) animal).breastFeed();
                       ((Mammal) animal).breastFeed();
                   }
                }
                DAYS_COUNTER--;
            }
            for (Animal animal : animals) {
                animal.gettingOlder(1);
            }
            YEARS--;
            DAYS_COUNTER=365;
        }
        zoo.getAnimalInfo();
    }
}
```

Zoo.java
```java
public class Zoo {

    ArrayList<Animal> animals = new ArrayList<Animal>();

    public Zoo(){
        animals.add(new Reptile("Crocodile", 5, 100, "Roar", 100, true, false));
        animals.add(new Bird("Penguin", 1, 150, "Squawk", 5, true, false));
        animals.add(new Fish("Goldfish", 1, 300, "Blub", 1, false, false));
        animals.add(new Mammal(Mammal.MOTRICITY.QUADRUPEDAL, Mammal.GENDER.FEMALE,"Lion", 4, 10, "Roar", 200, true, false));
    }

    public ArrayList<Animal> getAnimals() {
        return animals;
    }
    public void getAnimalInfo() {
        for (Animal animal : animals) {
            System.out.println("Name: " + animal.name);
            System.out.println("Age: " + animal.age);
            System.out.println("Size: " + animal.size);
            System.out.println("Duration: " + animal.duration);
            System.out.println("Scream: " + animal.scream);
            System.out.println("Weight: " + animal.weight);
            System.out.println("Protected by law: " + animal.protectedByLaw);
            System.out.println("Extinct: " + animal.extinct);
            System.out.println();
        }
    }
}
```

Animal.java
```java
public class Animal {
    String name;
    Integer age;
    Integer size;
    Integer duration;
    String scream;
    Integer weight;
    Boolean protectedByLaw;
    Boolean extinct;

    public Animal(String name, int size, int duration, String scream, Integer weight, Boolean protectedByLaw, Boolean extinct) {
        this.name = name;
        this.age = 0;
        this.size = size;
        this.duration = duration;
        this.scream = scream;
        this.weight = weight;
        this.protectedByLaw = protectedByLaw;
        this.extinct = extinct;
    }

    public void scream() {
        System.out.println(this.scream);
    }

    public void gettingOlder(Integer years) {
        if(age<=duration) this.age+=years;
        else { System.out.println("I'm dead"); age=-1; };
    }



}
```

Bird.java
```java
public class Bird extends Animal {
    public Bird(String name, int size, int duration, String scream, Integer weight, Boolean protectedByLaw, Boolean extinct) {
        super(name, size, duration, scream, weight, protectedByLaw, extinct);
    }
}
```

Fish.java
```java
public class Fish extends Animal {
    public Fish(String name, int size, int duration, String scream, Integer weight, Boolean protectedByLaw, Boolean extinct) {
        super(name, size, duration, scream, weight, protectedByLaw, extinct);
    }
}

```

Reptile.java
```java
public class Reptile extends Animal {
    public Reptile(String name, int size, int duration, String scream, Integer weight, Boolean protectedByLaw, Boolean extinct) {
        super(name, size, duration, scream, weight, protectedByLaw, extinct);
    }
}
```
Mammal.java
```java
public class Mammal extends Animal implements breastFeedImpl, childCaringImpl {
    enum GENDER{
        MALE,
        FEMALE
    }
    enum MOTRICITY{
        BIPEDAL,
        QUADRUPEDAL,
        SWIMMING,
        FLYING
    }
    GENDER gender;
    MOTRICITY motricity;

    public Mammal(MOTRICITY motricity,GENDER gender,String name, int size, int duration, String scream, Integer weight, Boolean protectedByLaw, Boolean extinct) {
        super(name, size, duration, scream, weight, protectedByLaw, extinct);
        this.gender=gender;
        this.motricity=motricity;
    }

    @Override
    public void breastFeed() {
        if(gender.name() == GENDER.FEMALE.name())  System.out.println("I'm breast feeding");
        else System.out.println("I'm not a Female");
    }

    @Override
    public void childCare() {
        System.out.println("I'm taking care of my child");
    }
}

```

breastFeedImpl.java
```java
public interface breastFeedImpl {
    public void breastFeed();
}
```

ChildCaringImpl.java
```java
public interface childCaringImpl {
    public void childCare();
}
```

:::

## 🧪 Modélisation d'une école

Une ecole est un ensemble de classes

Une classe possède : 
- un tableau, un retroprojecteur capable d'afficher un slide et de s'éteindre, On peut egalement 
  passer au slides suivant/precedent 
- un nombre de tables
- un nombre de chaises

Une salle de cours peut : sonner la recreation, lancer la projection

Les salles peuvent etre : des classes, une salle de pause ou de reunion

L'école possède des climatisations reversibles mobile cable de chauffer/rafraichir la salle à une temperature de 21°
Elles sont actuellement uniquement en salle de pause et de reunion


Simulation :
 l'école `MySchool` possède 5 classes de cours 

 Main.java
```java


```
:::


## 🧪 Modélisation d'un fastfood

Je souhaite modéliser un Fastfood . Un Fastfood posède : 
* des Tables
* des Chaises
* Une cuisine . Dans cette cuisine il y a : desverres, des fourchette, des couteau, des assiette, une gazinière, un micro-onde

Chaque Fastfood est capable de : 
* cuire des aliments (Différents selon les types de fastfood)


Un fastfood peut etre :
* Une Pizerria
* Un kebab
* Un Barre à Salade 
* Une Sandwicherie
* Un spécialiste du Burger


Une pizerria possède Un four
* un meuble a ingrédients
* Une liste de pizza à la carte


Une pizerria peut occasionnellement implementer une salle de fête :
* gerer une sonorisation 
* illuminer la salle 
* décorer la salle

Main.java
```java


```
:::

## 🧪 Projet d'application de Quiz

1. Modéliser une application qui permet de faire un quiz a l'aide de l'UML. 

Voici comment s'utilise l'application de quiz shell : 
```shell
./quiz.sh
1. Quelle est la couleur du cheval blanc d\'Henri IV ?
a) Rouge
b) Jaune
c) Blanc
--> votre réponse est : a
Vous avez répondu correctement
2. Quelle est la couleur du cheval bleu d'Henri VI ?
```

2. Faite valider votre modélisation avec le professeur.
3. Réaliez votre application de quiz



