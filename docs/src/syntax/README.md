#  Plus loin avec JAVA

## Collections 

Une collection est un ensemble d'éléments de taille variable. 
On peut créer une collection à partir d'une liste d'éléments.
```java
List<Integer> a = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```
Une collection peut être modifiée.
```java
a.add(11);
```

Pour intancier une collection, on peut utiliser la méthode `new` :
```java
List<Integer> a = new ArrayList<>();
```

Le type de la collection est déterminé par le type des éléments de la collection. 
```java
List<Integer> a = new ArrayList<>();
a.add(1);
a.add(2);
a.add(3);
```
On peut également définir le type de la collection à partir d'un type générique.
```java
List<Integer> a = new ArrayList<Integer>();
```

Un itérateur permet de parcourir une collection.
```java
Itérateur<Integer> it = a.iterator();
while (it.hasNext()) {
    System.out.println(it.next());
}
```

## Énumérations

l'énumération permet de définir un ensemble d'éléments. 
```java
enum Color {
    RED, GREEN, BLUE
}
```
Pour utiliser une énumération, on peut utiliser la méthode `valueOf` :
```java
Color color = Color.valueOf("RED");
```

On peut déclarer un constructeur pour une énumération.

```java
enum Color {
    RED(255, 0, 0), GREEN(0, 255, 0), BLUE(0, 0, 255);
    
    private final int red;
    private final int green;
    private final int blue;
    
    Color(int red, int green, int blue) {
        this.red = red;
        this.green = green;
        this.blue = blue;
    }
}
```
    
## Logs et debugging

Pour afficher un message dans la console, on peut utiliser la méthode `System.out.println` :
```java
System.out.println("Hello, World!");
```

On peut debuger un programme en pas à pas à l'aide d'un debugger tel que GDB. Pour utiliser GDB, il faut d'abord installer GDB sur votre ordinateur. Puis, vous pouvez lancer GDB en utilisant la commande `gdb` suivie du nom du fichier exécutable. 

```bash
gdb helloworld
```

Une fois que GDB est lancé, vous pouvez exécuter votre programme en utilisant la commande `run`. 

```bash
run
```

Vous pouvez ensuite utiliser les commandes `break`, `continue`, `next`, `step`, `print` pour déboguer votre programme. 

```bash
break main
continue
next 
step 
print a 
``` 

## Packaging et visibilité

La visibilité d'un membre détermine si un membre peut être accédé par un autre objet. 

```java
public class A {
    private int a;
    private int getA() {
        return a;
    }
}

public static void main(String[] args) {
    A a = new A();
    a.getA(); // erreur
}
```

La visibilité d'un membre est définie par les mots-clés `public`, `protected` et `private`. 
- `public` : membre accessible depuis n'importe quel objet
- `protected` : membre accessible uniquement depuis l'objet qui hérite de la classe
- `private` : membre accessible uniquement depuis l'objet qui l'a défini    

## Exception

Les exceptions permettent de gérer les erreurs dans un programme. 
```java
try {
    // code qui peut générer une erreur
} catch (Exception e) {
    // code qui gère l'erreur
}
``` 

Les exceptions sont définies par les classes `Exception` et `Throwable`. 
- `Exception` : une exception qui peut être générée par un programme
- `Throwable` : une exception qui peut être générée par un programme ou une autre exception    

#### Levée de l'exception

Les exceptions peuvent être définies par l'utilisateur. 
```java
public class A {
    public void getA() throws Exception {
        throw new Exception();
    }
}
public static void main(String[] args) {
    A a = new A();
    a.getA(); // erreur
}
```

#### Propagation de l'exception

Les exceptions peuvent être propagées à l'extérieur du programme. 
```java
public class A {
    public void getA() throws Exception {
        throw new Exception();
    }
}
public static void main(String[] args) {
    A a = new A();
    try {
        a.getA();
    } catch (Exception e) {
        System.out.println("Erreur");
    }
}
```

#### Création d'une exception personnalisée

On peut créer une exception personnalisée en définissant une classe qui hérite de `Exception`. 
```java
public class A extends Exception {
    public A() {
        super();
    }
}
``` 
On peut ensuite utiliser cette exception dans le code.
```java
public class A {
    public void getA() throws A {
        throw new A();
    }
}
```

## Concurrence

L'asynchrone est la notion de définir des tâches qui ne sont pas bloquantes. 
Le multi-threading est la notion de définir des tâches qui peuvent être exécutées en parallèle.

Le Thread est un object java qui permet de définir des tâches qui ne sont pas bloquantes.

Un runnable est un objet qui contient une tâche. 
```java
public class A implements Runnable {
    public void run() {
        System.out.println("A");
    }
}
```

Soit un thread A et un thread B. Si A exécute une tâche et B exécute une autre tâche, alors les deux tâches ne sont pas exécutées en parallèle. 

```java
//Creation d'une classe qui étend thread et implémente Runnable
public class A extends Thread implements Runnable {
    public A() {
        super("A");
    }
    public void run() {
        System.out.println("A");
    }
}

//Creation d'une classe qui étend thread et implémente Runnable
public class B extends Thread implements Runnable {
    public B() {
        super("B");
    }
    public void run() {
        System.out.println("B");
    }
}

//Creation d'un thread A et d'un thread B
public static void main(String[] args) {
    A a = new A();
    B b = new B();
    a.start();
    b.start();
}
```


## Appel HTTP Rest

Pour appeler une API HTTP, on peut utiliser la bibliothèque `HttpURLConnection` de manière asynchrone a l'aide d'un thread.
```java


//Creation d'une classe qui étend thread et implémente Runnable pour réaliser une requête get HTTP
public class A extends Thread implements Runnable {
    public A() {
        super("A");
    }
    public void run() {
        try {
            URL url = new URL("https://jsonplaceholder.typicode.com/todos/1");
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
            connection.setRequestMethod("GET");
            connection.connect();
            InputStream inputStream = connection.getInputStream();
            BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(inputStream));
            StringBuilder stringBuilder = new StringBuilder();
            String line;
            while ((line = bufferedReader.readLine()) != null) {
                stringBuilder.append(line);
            }
            System.out.println(stringBuilder.toString());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
//Creation d'un thread A
public static void main(String[] args) {
    A a = new A();
    a.start();
}
``` 

## GUI avec JavaFX

`GUI` signifie `Graphical User Interface`. JavaFX est une bibliothèque Java qui permet de créer des interfaces graphiques. 
```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloWorld extends Application {
    public void start(Stage primaryStage) {
        primaryStage.setTitle("Hello World!");
        primaryStage.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
``` 

Pour ajouter des éléments à l'interface graphique, on peut utiliser la classe `Scene` :
```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.StackPane;
import javafx.stage.Stage;

public class HelloWorld extends Application {
    public void start(Stage primaryStage) {
        Button button = new Button("Click me!");
        button.setOnAction(e -> System.out.println("Button clicked!"));
        StackPane root = new StackPane();
        root.getChildren().add(button);
        Scene scene = new Scene(root, 300, 250);
        primaryStage.setTitle("Hello World!");
        primaryStage.setScene(scene);
        primaryStage.show();
    }
    public static void main(String[] args) {
        launch(args);
    }
}
``` 







