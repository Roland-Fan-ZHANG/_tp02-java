# [TP-02 Java](https://monge.univ-mlv.fr/ens/IR/IR1/2023-2024/Java/td02.php)

# Exercice 1 - Assignation, égalité, référence

## 1.1 - On considère le code suivant :

```java
var s = "toto";
System.out.println(s.length());
```

### Quel est le type de `s` ? Comment le compilateur fait-il pour savoir qu'il existe une méthode `length()` sur `s` ?

## 1.2 - Qu'affiche le code suivant ? Expliquer.

```java
var s1 = "toto";
var s2 = s1;
var s3 = new String(s1);

System.out.println(s1 == s2);
System.out.println(s1 == s3);
```

## 1.3 - Quelle est la méthode à utiliser si l'on veut tester si le contenu des chaînes de caractères est le même ?

```java
var s4 = "toto";
var s5 = new String(s4);

System.out.println(/* comparer contenue de s4 et s5 */);
```

## 1.4 - Qu'affiche le code suivant ? Expliquer.

```java
var s6 = "toto";
var s7 = "toto";

System.out.println(s6 == s7);
```

## 1.5 - Expliquer pourquoi il est important que `java.lang.String` ne soit pas mutable.



## 1.6 - Qu'affiche le code suivant ?

```java
var s8 = "hello";
s8.toUpperCase();
System.out.println(s8);
```

### Expliquer.

# Exercice 2 - Afficher les arguments de la ligne de commande

### Écrire une classe Morse qui permet, lors de son exécution, d'afficher les chaînes de caractères prises en argument séparées par des `"Stop."`.

```console
$ java Morse ceci est drole
ceci Stop. est Stop. drole Stop.
```

## 2.1 - Utiliser dans un premier temps l'opérateur + qui permet la concaténation de chaînes de caractères.



## 2.2 - A quoi sert l'objet `java.lang.StringBuilder` ?

### Pourquoi sa méthode `append(String)` renvoie-t-elle un objet de type `StringBuilder` ?


## 2.3 - Réécrire la classe Morse en utilisant un `StringBuilder`.

### Quel est l'avantage par rapport à la solution précédente ?


## 2.4 - Recopier le code suivant dans une classe de `Test` :

```java
public static void main(String[] args) {
    var first = args[0];
    var second = args[1];
    var last = args[2];
    System.out.println(first + ' ' + second + ' ' + last);
}
```

### Pourquoi peut-on utiliser ' ' à la place de " " ?

### Compiler le code puis utiliser la commande `javap` pour afficher *le bytecode Java* (qui n'est pas un assembleur) généré.

```console
javap -c Test
```

### Que pouvez-vous en déduire ?


## 2.5 - Compiler le code de la question 1, puis utiliser la commande `javap` pour afficher *le bytecode Java* généré.

### Que pouvez-vous en déduire ?

### Dans quel cas doit-on utiliser `StringBuilder.append()` plutôt que le `+` ?

### Et pourquoi est-ce que le chargé de TD va me faire les gros yeux si j'écris un `+` dans un appel à la méthode `append`?


# Exercice 3 - Reconnaissance de motifs

Le but de cet exercice est la manipulation d'expressions régulières en java. En Java, nous utiliserons pour cela les classes du paquetage `java.util.regex`. Relisez la fin du cours 2 sur le sujet. Si vous avez besoin de vous rafraichir la mémoire sur les expressions régulières, vous pouvez lire la page [Wikipédia](https://fr.wikipedia.org/wiki/Expression_r%C3%A9guli%C3%A8re).


## 3.1 - A quoi servent la classe `java.util.regex.Pattern` et sa méthode `compile` ?

### A quoi sert la classe `java.util.regex.Matcher` ?

## 3.2 - Reprenez la petite calculatrice `Calc` de l'exercice 1. On veut que si l'utilisateur saisisse autre chose qu'un nombre, le programme lui demande de saisir une autre valeur. Pour cela on remplacera l'appel `scanner.nextInt` par `scanner.nextLine` qui renvoie la chaîne de caractères saisie par l'utilisateur. N'oubliez pas de remplacer `scanner.hasNextInt()` par `scanner.hasNextLine()`.

### Attention, n'oubliez pas que l'utilisateur doit pouvoir saisir un nombre négatif.


## 3.3 - En partant du code ci-dessous, on veut écrire un programme qui va lire un fichier HTML dont le chemin est pris sur la ligne de commande et qui va afficher la liste des URLs de tous les liens contenus dans le fichier.

```java
public class LinkExtractor {
    public static void main(String[] args) throws IOException {
        var path = Path.of(args[0]);
        var lines = Files.readAllLines(path, StandardCharsets.ISO_8859_1);
        // reads all lines of the file opened in Latin-1
        for(var line : lines){
        // TODO
        }
    }
} 
```



On rappelle qu'en HTML l'URL d'un lien est donné par le tag href de la balise `<a>`.

Vous pouvez tester votre programme sur le fichier [forax.html](https://monge.univ-mlv.fr/ens/IR/IR1/2023-2024/Java/td02/forax.html). Vous devez faire un clic droit et "Enregistrer sous".

<!-- 

Vous devriez obtenir l'affichage suivant: <a href="http://www-igm.univ-mlv.fr/~forax/ens/java-avance/cours/pdf"

===>http://www-igm.univ-mlv.fr/~forax/ens/java-avance/cours/pdf

<a href="http://www-igm.univ-mlv.fr/ens/"

===>http://www-igm.univ-mlv.fr/ens/

<a href="http://www-igm.univ-mlv.fr/~forax/ens/ig/cours/pdf"

===>http://www-igm.univ-mlv.fr/~forax/ens/ig/cours/pdf

-->

## 3.4 - Modifiez le programme pour ne conserver que les liens contenant le mot `java` ou `Java`.


## 3.5 - Si vous vous embêtez pendant le week-end, modifiez votre programme pour gérer des liens contenant plusieurs balises comme par exemple, `<a style="bigboss" class="hypercool" href="www.mic.drop.eu">`

