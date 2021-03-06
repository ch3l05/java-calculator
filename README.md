# Java 8: Basics of the language
> Fundamentos del lenguaje

El codigo fuente en `Java` se escribe en archivos cuya extensión es .java a partir de los cuales luego del proceso de compilación se crean archivos .class, y estos archivos junto con las librerias son las que hacen nuestro programa que sera ejecuado por la [JVM](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual_Java). Vamos a discutir algunos conceptos a traves de este pequeño demo hecho en `Java`.

## tabla de contenido

- [Estructura basica de un programa en Java](#estructura-basica-de-un-programa-en-java)
  - [Package](#package)
  - [Imports](#import)
  - [Clases (overview)](#class)
    - [Campos de una clase](#fields)
    - [Metodos](#methods)
  - [Metodo main](#main)
- [Nociones basicas de programación](#basics)
  - [Estructuras de datos](#estructuras-de-datos)
    - [variables y tipos de datos](#variables)
      - [Entero](#entero)
      - [Punto Flotante](#punto-flotante)
      - [Caracter](#caracter)
      - [Booleano](#booleano)
      - [String](#string)
    - [Arreglos](#array)

## Estructura basica de un programa en Java

### package

Lo primero que vemos en archivo *.java es la declaración del [package](https://es.wikipedia.org/wiki/Paquete_Java) al que pertenece esta [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html). un paquete nos permite agrupar clases, interfaces y otros elementos que comparten caracteristicas comunes que hacen que queramos agruparlos de una manera conveniente.

Ejemplo de la declaración del paquete al que pertence la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html).

```java
package io.rhynl.java.basics;
```

Por convención en `Java` los nombre del paquete se define de manera inversa al dominio de la organización o grupo, en el ejemplo que se muestra arriba, utilizo el dominio `rhynl.io` invertido y a partir de este se crean los subdominios pertinentes `java` para indicar que es un codigo en `Java` y el subdominio `basics` que esta dentro del paquete `java`.

### import

En `Java` se trabaja con el paradigma de la [Programación Orientado a Objetos](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos) ([`OOP`](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos) por sus siglas en ingles) donde una de sus premisas es maximizar la reusabilidad de l codigo, de allí que podamos crear paquetes de clases comunes y por supuesto la idea de que podamos importar dichas clases desde otra ubicación para poder utilizarlas. Existes muchos paquetes con diferentes clases que nos provee el lenguaje como la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) [`System`](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html) el cual posee un campo statico [`out`](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#out) del tipo [`PrintStream`](https://docs.oracle.com/javase/8/docs/api/java/io/PrintStream.html) el cual posee metodos como [`println`](https://docs.oracle.com/javase/8/docs/api/java/io/PrintStream.html#println()) y [`format`](https://docs.oracle.com/javase/8/docs/api/java/io/PrintStream.html#format(java.lang.String,%20java.lang.Object...)) conocidos que hemos utilizado antes.

Ya iremos profundizando conceptos como [`OOP`](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos) y los diferentes paquetes y clases qe nos provee `Java`. Lo que debemos notar ahora es que la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) [`System`](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html) así como otras clases utiles y de uso común, las cuales pertenecen al paquete [`java.lang`](https://docs.oracle.com/javase/8/docs/api/java/lang/package-summary.html) son importadas o cargadas automaticamente por nosotros a la hora de compilar y/o ejecutar nuestros porgramas, de allí que no haya necesidad de importarlas pero hay muchos otros paquetes y clases que nos ofrece el lenguaje así como aquellas de terceros o que desarrollemos nosotros que no se cargan automaticamente es por ello que debemos indicar explicitamente la importación de las mismas.

Esto se logra con el uso de la palabra reservada [`import`](https://docs.oracle.com/javase/tutorial/java/package/usepkgs.html) seguido del nombre completamente calificado (esto no es mas que el nombre con el dominio invertido donde se indica el paquete y el nombre del miembro del paquete que deseamos utilizar).

Ejemplo de importación de una [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html).

```java
import java.util.Scanner;
```

En el ejemplo anterior, se indica que necesitamos hacer uso de la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) perteneciente al paquete [`java.util`](https://docs.oracle.com/javase/8/docs/api/java/util/package-summary.html), esta [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) nos permitirá crear un objeto con el cual podamos capturar lo que teclea el usuario como veremos mas adelante.

### class

Lo siguiente que notamos es la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html), cuando trabajamos con paquetes es un requerimiento que el nombre de la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) sea igual al nombre que le dimos al archivo .java, así pues, podemos ver que la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) se llama `Main` y el nombre del archivo es `Main.java`, si qieremos mas adelante cambiar el nombre de nuestra [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html), pro ejemplo a `Calculadora` debemos de igual manera renombrar el archivo correspondiente a `Calculadora.java`.

Ejemplo de la definición de la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html)

```java
public class Main {
  //...
}
```

Una [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) se define haciendo uso de la palabra reservada [`class`](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) seguido del nombre que se le dara, por convención, al nombrar las clases usamos el estilo [pascal](https://msdn.microsoft.com/en-us/library/x2dbyw72(v=vs.71).aspx) en enl cual la primera letra de la palabra se escribe en mayusculas y las siguientes en minuscalas y en el caso de que el nombre de la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) es compuesto de dos o mas palabras, la inicial de cada palabra tambien debe estar en mayuscula (ej: VehiculoAcuatico). El codigo corespondiente a la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) esta encerrado entre llaves `{}`. En ejemplo se aprecia que la definición de la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) tiene un [modificador de acceso](https://docs.oracle.com/javase/tutorial/java/javaOO/accesscontrol.html), la palabra clave `public`, esto lo veremos con mas detalles en proximas oportunidades, sin embargo lo que el modificador hacer es indicar quien puede utilizar la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html), puede ser `public` lo que implica que puede es visible desde cualquier otra [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) sin importar la ubicación de la misma en el programa o ausencia de modificar (que en si mismo es un modificador) lo que implica que [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) solo es visible desde el paquete que la contiene, es decir, que solo otras clases dentro del mismo paquete a la que la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) pertenece puede verle.

Una [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) puede tener campos (variables que pertenencen a la clase o a los objetos creados a partir de la clase) y metodos (rutinas que se ejecutan al ser llamados en algun momento durante la ejecución del programa y que generalmente su razón de ser es modificar o acceder a los campos de la clase u objeto).

### fields

Como indicamos anteriormente una [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) esta compuesta por metodos y por fields (campos). Los campos no son mas que variables definidas dentro de la clase y que son accesibles desde los metodos de dicha clase.

Ejemplo de campo:

```java
static Scanner teclado = new Scanner(System.in);
```

En el ejemplo anterior, tenemos un campo perteneciente a la [clase](https://docs.oracle.com/javase/tutorial/java/concepts/class.html) `Main` al que llamamos `teclado` el cual es de tipo [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) o dicho de otra manera, `teclado` es una instancia de [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html), como mencionamos antes, [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html)  nos permite recuperar los datos ingresados por el usuario a traves del teclado. Para ello debemos pasar como parametro al [costructor](https://docs.oracle.com/javase/tutorial/java/javaOO/constructors.html) de la clase [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) la fuente de los datos que van a ser leidos, en este caso será de [`System.in`](https://docs.oracle.com/javase/8/docs/api/java/lang/System.html#in).

### Methods

Informacion sobre los metodos de una clase
### main

Un programa consta en la mayoria de los casos de muchas clases, no es el caso de este repositorio (aún), pero es de lo mas comun que ese sea el caso, es por ello que necesitamos de una manera de indicarle a la [maquina virtual de Java](https://es.wikipedia.org/wiki/M%C3%A1quina_virtual_Java) el punto de partida para la ejecución del programa, esto se logra gracias al metodo [`main`](https://docs.oracle.com/javase/tutorial/getStarted/application/#MAIN) (no confundir con la clase Main).

```java
public static void main(String[] args) {
  //el programa empieza a ejecutarse aquí.
}
```

la declaración del metodo es tal cual como se muestra arriba, donde la palabra reservada `public` hace referencia a que es visible desde cualquier parte del programa, como ya mencionamos antes. La palabra `static` hace referencia a que este es un metodo que pertenece directamente a la clase y que se comparte para todos los objetos creados a partir de la clase, esto lo veremos con más detalle posteriormente. La palabra reservada `void` indica el tipo de dato que devuelve el metodo, en el caso de [`main`](https://docs.oracle.com/javase/tutorial/getStarted/application/#MAIN), como no devueve nada y es a eso a lo que hace referencia `void`, ausencia de valor de retorno.

## Basics

### Estructuras de datos

Existen diferentes [estructuras de datos](https://es.wikipedia.org/wiki/Estructura_de_datos) que veremos a lo largo de las semanas, pero por ahora vamos a comentar dos: [variables](#variables) y [arreglos](#array).
#### variables

Como vimos antes, las [variables](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html) en `Java` estan asociadas a las clases, como campos de estas. Y las mismas pueden ser de diferentes tipos, los hay de tipos personalizados como el caso de [`teclado`](#fields) que es del tipo [`Scanner`](https://docs.oracle.com/javase/8/docs/api/java/util/Scanner.html) pero los hay [variables](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html) de otros tipo, de hecho mas comunes, conocidos como tipo primitivos o propios del lenguaje. Existen cuatro categorias para agrupar los posibles tipos primitivos que una variable puede tomar. Estos son:

- [Entero](#entero)
- [Punto Flotante](#punto-flotante)
- [Caracter](#caracter)
- [Booleano](#booleano)

Por  convención las variables se nombran siguiendo el estilo [camel case](https://msdn.microsoft.com/en-us/library/x2dbyw72(v=vs.71).aspx), esto es, que los nombre comienzan con letra minuscula y las letras sucesivas en minuscula de igual manera, en el caso de ser un nombre compuesto, por dos o mas palabras, la primera letra de la segunda y demas letras estara en mayuscula. Ej: diasDeLaSemana.

##### Entero

Para los numeros [enteros](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html) (aquellos que no poseen parte decimal), existen cuatro tipos de datos primitivos. Estos son: `byte`, `short`, `int` y `long` la diferencia entre ellos radica basicamente en el rango maximo de valores que puede contener una variable de dicho tipo, como se ilustra en la tabla abajo:

![Tipos de datos enteros](https://rhynl.io/java/basics/images/tipos_de_enteros-min.png)

En la tabla podemos apreciar para tipo, cuantos [`bytes`](https://es.wikipedia.org/wiki/Byte) ocupa de la memoria del sistema una variable de cada tipo, el rango que puede contener y el valor por defecto para cada tipo.

```java
byte diasDeLaSemana = 7;
short edad = 33;
int numeroDeSegundosEnUnAnio = 31536000;
long edadAproximadaDelPlanetaTierra = 4543000000000L;
```

En el codigo anterior, se pueden apreciar algunos ejemplos de definición de variables. Com vemos, primero se indica el tipo de dato luego el nombre de la variable seguido del operador de asignación (simbolo de igualdad) y el valor que se asigna a la variable. Esto es una [sentencia (statement)](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/expressions.html) y como toda sentencia termina con punto y como `;`.

##### Punto Flotante

Para los numeros reales (que poseen parte decimal) se usa la notación de [punto flotante](https://es.wikipedia.org/wiki/Coma_flotante) y para este tipo de numeros existen dos tipos de datos primitivos en el lenguaje: `float` y `double`.

![Tipo de dato punto flotante](https://rhynl.io/java/basics/images/tipos_de_flotantes-min.png)

```java
float pi = 3.14159265359f;
double piPi = 9.869604401; // pi*pi
```

Al igual que ocurre para los tipos de datos enteros, la mayor diferencia entre los tipos `float` y `double` es la presición del valor que pueden contener.

##### Caracter

El tipo de dato [`char`](https://docs.oracle.com/javase/tutorial/java/data/characters.html) es la representación en memoria de un [caracter unicode](https://en.wikipedia.org/wiki/List_of_Unicode_characters) el cual se coloca entre comillas simples (`'`), si esta presente en el teclado de la computadora, basta con teclear ese caracter pero si no es ese el caso se puede indicar con el [codigo unicode](https://en.wikipedia.org/wiki/List_of_Unicode_characters).

![Tipo de dato caracter y booleano](https://rhynl.io/java/basics/images/caracter_booleano-min.png)

```java
char inicialDelNombre = 'R';
char letraA = '\u0041';
```

##### Booleano

El tipo de dato boolean puede tener dos valores posibles, `true` que indica ***verdadero*** y el valor `false` que indica ***falso***. las variables de este tipo de dato primitivo son utiles para almacenar el resultado de una comparación logica como veremos mas adelante.

```java
boolean es2017AnioBisiesto = false;
boolean esMartes = true;
```

##### String

Existe un tipo que no es primitivo pero cuyo uso es sumamente comun, de hecho lo hemos estado utilizando sin siquiera pensar en ello. La [cadena de caracteres](https://docs.oracle.com/javase/tutorial/java/data/strings.html) ([`String`](https://docs.oracle.com/javase/8/docs/api/java/lang/String.html)) es una clase que nos resuelve la manipulación de caracteres individuales para formar textos, de allí el nombre, cadena de caracteres, ya que no son mas que una suceción de caractres uno seguido de otro.

```java
System.out.println("Hello World!!");
```

En el ejemplo podemos apreciar como el metodo `println` recibe como parametro la cadena de caracteres `"Hello World!!"`, es de destacar que las cadenas de caracteres a diferencia de un caracter, se encierra entre comillas dobles (`"`). Para declarar una variable de tipo `String` se hace como hemos visto hasta ahora para los tipos pimitivos, aun cuando debemos recordar que `String` no es un tipo primitivo.

```java
String nombre = "John Doe";
```

Realmente lo que se esta creando es un objeto de tipo `String` o le que es lo mismo la variable `nombre` es una instancia de `String` y por ello tiene algunos atributos y metodos asociados, uno de los atributos mas comunes de los `String` es el `length` (longitud) que representa la logindut de la cadena de caracteres.

```java
String nombre = "John Doe";
int longitudDelNombre = nombre.length;
System.out.print(longitudDelNombre); // imprime 8.
```

Entre sus metodos vamos a mencionar dos por ahora, estos son `split` y `charAt`. `split` lo que hace es cortar la cadena, de acuerdo a un caracter dado y devolvernos un [arreglo](#array) (el cual veremos pronto) que contiene cada una de las partes en las que fue dividida la cadena.

```java
String cadenaDeLetras = "a,b,c,d,e";
String[] arregloDeLetras = cadenaDeLetras.split(","); // arregloDeLetras es igual a ["a","b","c","d","e"]
```

En el ejemplo que vemos arriba, tenemos una cadena contentiva de una serie de letras separadas por coma. y luego le estamos diciendo que deseamos separar esa cadena de caracteres usando como caracter de ruptura la coma `,`.

En cuanto al metodo `charAt` es un metodo que nos permite acceder al caracter ubicado en una posición especifica de la cadena. Digamos que deseamos almacenar en memoria la primera letra del nombre de una persona, lo hariamos de la siguiente manera.

```java
String nombre = "John Doe";
char incialDelNombre = nombre.charAt(0);
System.out.print(inicialDelNombre); // imprime J.
```

#### Array

Un arreglo tambien llamado vector, no es mas una serie de elementos del mismo tipo, con un orden especifico y que son accedidos a traves de un indice de base cero. Retomemos un ejemplo de esto, el arreglo (`array`) de `String` que creamos anteriormente a partir de la variable `cadenaDeLetras`.

```java
String[] arregloDeLetras = cadenaDeLetras.split(","); // arregloDeLetras es igual a ["a","b","c","d","e"]
```

Como vemos en este ejemplo la variable `arregloDeLetras` es un vector en este caso de variables de tipo `String`, veamos otros ejemplos.

```java
int[] arregloDeNumeros = {1,2,3,4,5};
char[] arregloDeCaracteres = new char[5];
arregloDeCaracteres[0] = 'A';
int primerElemento = arregloDeNumeros[0];
```

De los ejemplos anteriores podemos desprender algunas ideas sobre los arreglos, en primer lugar que existen diferentes maneras de declararlos y asignanles valores. Lo primero que debemos hacer es indicar el tipo de dato que los elementos que contendra el arreglo, estos puede ser cualquiera de los tipos primitivos o incluso tipos compuestos como lo es el caso de `String`, luego del tipo usamos los corchetes (`[]`) de apertura y cierre, seguido del nombre que le demos a la variable. En cuanto a la asignación podemos hacerlo indicando directamente los elementos que contendra el arreglo como es el caso de `arregloDeNumeros` y en cuyo caso debe hacerse indicando entre llaves (`{}`) y separados por coma (`,`) los distintos valores que contendra el arreglo. O como en el caso de `arregloDeCaracteres` definimos solo la longitud que tendra el arreglo, en cuyo caso se usa la palabra reservada `new` la cual indica que vamos a crear una variable de un tipo personalizado, en caso del ejemplo arraglo de char, seguido del tipo de dato y los corchetes, el cual debe ser igual al tipo que indicamos en la declaración de la variable y dentro de los corchetes indicamos la longitud del arreglo, es decir la cantidad de elementos maxima que puede albergar el vector.
