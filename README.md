# Taller 9 - Maps, Sets, Archivos de texto y binarios

En este taller se trabajará la carga y escritura de archivos de texto y binarios. Se trabajará sobre el proyecto de la aplicación de música que se ha venido desarrollando en los talleres anteriores.

## Indice

1. [Preguntas teóricas](#preguntas-teóricas)
2. [Enunciado](#enunciado)
   1. [Cargar y guardar el estado del programa](#cargar-y-guardar-el-estado-del-programa)
   2. [Generación de reportes](#generación-de-reportes)
3. [Calificación](#calificación)
4. [¿Qué sigue?](#qué-sigue)

## Preguntas teóricas

Marque la respuesta correcta a las siguientes preguntas. Estas preguntas no afectan la calificación del taller, pero le ayudarán a reforzar los conceptos vistos en clase:

1. La forma de instanciar correctamente un HashMap (siguiendo, además, las buenas prácticas de código) cuya llave es un `String` y el valor es un `Integer` es:
   - `Map<String, Integer> map = new HashMap<>();`
   - `HashMap<String, Integer> map = new HashMap<>();`
   - `HashMap<String, Integer> map = new Map<>();`
   - `Map<String, Integer> map = new Map<>();`

Las preguntas 2 a 5 hacen referencia al siguiente código:

```java

Map<String, Integer> map = new HashMap<>();

map.put("a", 1);
map.put("b", 2);
map.put("c", 3);
map.put("c", 5);

```

2. ¿Cuál es la forma correcta de obtener el valor asociado a la llave `"b"`?
   - `map.get("b")`
   - `map.get(2)`
   - `map.get(1)`
   - `map.get("2")`
3. ¿Cuál es la forma correcta de verificar si la llave `"b"` está en el `Map`?
   - `map.containsKey("b")`
   - `map.contains("b")`
   - `map.containsValue("b")`
   - `map.contains("2")`
4. ¿Cuál es la forma correcta de eliminar la llave `"b"` del `Map`?
   - `map.remove("b")`
   - `map.remove(2)`
   - `map.remove(1)`
   - `map.remove("2")`
5. Si decidiera imprimir las llaves y valores de `map` con un `for-each`, ¿cuál sería la forma correcta de hacerlo?
   - ```java 
      for (String key : map.keySet()) { 
              System.out.println(key + " " + map.get(key));
          }
     ```
   - ```java
     for (String key : map) { 
        System.out.println(key + " " + map.get(key)); 
     }
     ```
   - ```java
     for (String key : map.values()) { 
        System.out.println(key + " " + map.get(key)); 
     }
     ```
   - ```java
     for (String key : map.entrySet()) { 
        System.out.println(key + " " + map.get(key)); 
     }
     ```
6. ¿Cuál es el resultado de imprimir `map` en el código anterior?
   - `a 1, b 2, c 3`
   - `a 1, b 2, c 3, c 5`
   - `a 1, b 2`
   - `a 1, c 3, c 5`
7. ¿Cuál es la diferencia entre una lista (List) y un conjunto (Set)?
   - Un conjunto no permite elementos duplicados y tiene elementos ordenados, mientras que una lista permite elementos duplicados y no tiene elementos ordenados.
   - Un conjunto permite elementos duplicados y tiene elementos ordenados, mientras que una lista no permite elementos duplicados y no tiene elementos ordenados.
   - Un conjunto no permite elementos duplicados y no tiene elementos ordenados, mientras que una lista permite elementos duplicados y tiene elementos ordenados.
   - Un conjunto permite elementos duplicados y no tiene elementos ordenados, mientras que una lista no permite elementos duplicados y tiene elementos ordenados.
8. ¿Cuál es la forma correcta (siguiendo llas buenas prácticas de programación) de instanciar un HashSet de `String`?
   - `Set<String> set = new HashSet<>();`
   - `HashSet<String> set = new HashSet<>();`
   - `HashSet<String> set = new Set<>();`
   - `Set<String> set = new Set<>();`
     Las preguntas 9 a 12 hacen referencia al siguiente código:

```java

Set<String> set = new HashSet<>();

set.add("a");
set.add("b");
set.add("c");
set.add("c");

```

9. ¿Cuál es la forma correcta de verificar si el elemento `"b"` está en el conjunto?
   - `set.contains("b")`
   - `set.contains(2)`
   - `set.contains(1)`
   - `set.contains("2")`
10. ¿Cuál es la forma correcta de eliminar el elemento `"b"` del conjunto?
   - `set.remove("b")`
   - `set.remove(2)`
   - `set.remove(1)`
   - `set.remove("2")`
11. Si decidiera imprimir los elementos de `set` con un `for-each`, ¿cuál sería la forma correcta de hacerlo?
   - ```java
      for (String element : set) { 
          System.out.println(element); 
      }
      ```
   - ```java
      for (String element : set.values()) { 
          System.out.println(element); 
      }
      ```
   - ```java
      for (String element : set.keySet()) { 
          System.out.println(element); 
      }
      ```
   - ```java
      for (String element : set.entrySet()) { 
          System.out.println(element); 
      }
      ```
12. ¿Cuál es el resultado de imprimir `set` en el código anterior?
   - `a, b, c`
   - `a, b, c, c`
   - `a, b`
   - `a, c, c`
13. ¿Cómo se pueden obtener los valores únicos de una lista usando un `Set`?
   - Agregando todos los elementos de la lista al `Set`.
   - Usando el método clear de la lista.
   - Iterando sobre el `Set` y agregando los elementos a la lista.
   - Usando el método `unique` de la lista.
14. "Un archivo `CSV` es un tipo de archivo binario". Esta afirmación es:
   - Falsa
   - Verdadera
15. ¿Qué es la serialización en Java?
   - Es el proceso de convertir un objeto en un formato que se puede almacenar en un archivo o enviar a través de la red.
   - Es el proceso de convertir un archivo en un objeto.
   - Es el proceso de convertir un objeto en un archivo.
   - Es el proceso de convertir un objeto en un formato que se puede almacenar en un archivo que puede leer un ser humano fácilmente.

El siguiente código fue generado a través de un prompt en un LLM (Large Language Model). Al copiarlo en su proyecto, todo parece bien. Las preguntas 16 a 18 hacen referencia a este código:

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        Employee e = new Employee();
        e.name = "John Doe";
        e.address = "123 avenue";
        e.SSN = 11122333;
        e.number = 101;

        try (FileOutputStream fileOut = new FileOutputStream("employee.ser");
             ObjectOutputStream out = new ObjectOutputStream(fileOut)) {
            out.writeObject(e);
            System.out.println("Serialized data is saved in employee.ser");
        } catch (IOException i) {
            i.printStackTrace();
        }
        
    }
}

class Employee {
    public String name;
    public String address;
    public int SSN;
    public int number;
}
```

16. ¿Qué hace el código del método `main`?
   - Serializa un objeto de la clase `Employee` y lo guarda en un archivo llamado `employee.ser`.
   - Deserializa un objeto de la clase `Employee` y lo guarda en un archivo llamado `employee.ser`.
17. Al ejecutar el código anterior, usted nota que un mensaje de error es impreso en la consola. ¿Cuál es la causa más probable de este error?
   - El archivo `employee.ser` no existe.
   - La clase `Employee` no implementa la interfaz `Serializable`.
   - No se ha capturado la excepción `ClassNotFoundException`.
   - La clase `Employee` no tiene un método `readObject`.
18. Suponga que soluciona el error que estaba obteniendo y se pudo generar el archivo binario: Si luego se modificara la clase `Employee` para agregar un nuevo atributo `email` y, además, se implementara un método dentro de la clase `Main` para deserializar el objeto, ¿cuál de las siguientes afirmaciones sería correcta si se quisiera deserializar el archivo binario creado al inicio?
   - No se puede deserializar el archivo binario porque la clase `Employee` ha cambiado.
   - Se puede deserializar el archivo binario sin problemas.
   - Se puede deserializar el archivo binario, pero se perderá el valor del atributo `email`.
   - Se puede deserializar el archivo binario, pero se lanzará una excepción.

Suponga que tiene un archivo de texto llamado `data.txt` con el siguiente contenido:

```
1|2|3|4|5
6|7|8|9|10
11|12|13|14|15
```

ChatGPT le sugiere el siguiente código para leer el archivo:

```java
import java.io.*;

public class Main {
    public static void main(String[] args) {
        try {
            File file = new File("data.txt");
            List<String> lines = Files.readAllLines(file.toPath(), StandardCharsets.UTF_8);
            for (String line : lines) {
                String[] values = line.split("|");
                for (String value : values) {
                    System.out.print(value + " ");
                }
                System.out.println();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
```
La pregunta 19 y 20 hacen referencia a este código.34

19. ¿Cuál es el resultado de ejecutar el código anterior?
   - `1 2 3 4 5 6 7 8 9 10 11 12 13 14 15`
   - `1 6 11 2 7 12 3 8 13 4 9 14 5 10 15`
   - `1 2 3 4 5`
   - `1 2 3 4 5 6 7 8 9 10`
20. ¿Qué hace el método `split` en el código anterior?
   - Divide una cadena en subcadenas basadas en un delimitador.
   - Divide una cadena en subcadenas basadas en un índice.
   - Divide una cadena en subcadenas basadas en un carácter.
   - Divide una cadena en subcadenas basadas en un número.

[Volver al índice](#indice)

## Enunciado

**Este taller toma como base el proyecto de la aplicación de música que se ha venido desarrollando en los talleres anteriores.**

El programa debe permitir ahora cargar y guardar la información de los artistas, canciones, listas de reproducción y clientes en archivos de texto y binarios. Para esto, se deben crear los métodos necesarios en las clases de servicios y controladores.
Además, se deben capturar las excepciones que puedan surgir al cargar o guardar los archivos.
    - Recuerde que al momento de cargar los archivos, se deben cumplir las validaciones presentes en la entrega anterior.

Para lograr esto, se recomienda crear una nueva vista que permita al usuario seleccionar la opción de cargar o guardar los archivos de texto o binarios.


### Cargar y guardar el estado del programa

El programa debe permitir cargar la información desde uno o varios archivos de texto con una estructura definida por el grupo. 
Además, por practicidad a la hora de probar, el programa debe permitir exportar la información a archivos de texto con la misma estructura.

Adicionalmente, se debe permitir crear un archivo binario que contenga la información serializada de los artistas, canciones, listas de reproducción y clientes.
El programa debe permitir cargar la información desde el archivo binario creado previamente.

### Generación de reportes

Su proyecto debe permitir generar reportes con información relevante de los artistas, canciones, listas de reproducción y clientes.

El proyecto debe ser modificado para agregar un nuevo módulo que permita la generación de reportes. **Los reportes deben ser guardados en archivos de texto y deben ser mostrados en pantalla**. Los reportes son los siguientes:


1. Se debe mostrar la popularidad de cada artista (Si un artista no existe dentro de las listas de reproducción, o no es seguido, no debe mostrarse en el reporte). La popularidad de un artista se calcula de la siguiente manera:

    - Si un artista aparece en una lista de reproducción, se le suma 1 a su popularidad por cada canción que tenga en la lista de reproducción.
    - Por cada follow que tenga un cliente de un artista, se le suma 2 a la popularidad del artista.

   El reporte debe ser guardado en un archivo de texto llamado `reporte_popularidad.txt`. En este archivo deben aparecer los artistas con una popularidad mayor a 0. El formato del archivo debe ser el siguiente:

    ```
    Reporte de popularidad
    
    <Nombre del artista 1>: <Popularidad>
    <Nombre del artista 2>: <Popularidad>
    ...
    <Nombre del artista n>: <Popularidad>
    
    ```
2. Para cada cliente, se debe mostrar la cantidad de canciones que tiene en sus listas de reproducción, la cantidad de artistas que sigue y el nombre del artista que más escucha (Este artista será el que más se repita en las listas de reproducción). El reporte debe ser guardado en un archivo de texto llamado `reporte_clientes.txt`. El formato del archivo debe ser el siguiente:

    ```
    Reporte de clientes
    
    <Nombre del cliente 1>
    - Canciones en listas de reproducción: <Cantidad de canciones>
    - Artistas seguidos: <Cantidad de artistas>
    - Artista que más escucha: <Nombre del artista>
   
    <Nombre del cliente 2>
    - Canciones en listas de reproducción: <Cantidad de canciones>
    - Artistas seguidos: <Cantidad de artistas>
    - Artista que más escucha: <Nombre del artista>
   
    ...
   
    <Nombre del cliente n>
    - Canciones en listas de reproducción: <Cantidad de canciones>
    - Artistas seguidos: <Cantidad de artistas>
    - Artista que más escucha: <Nombre del artista>
   
    ```
3. Se debe mostrar, para un cliente en particular, el top 3 artistas preferidos (en orden): los 3 artistas que más se repiten en las listas de reproducción del cliente. El reporte debe ser guardado en un archivo de texto llamado `reporte_top3_<nombre_cliente>.txt`, donde `<nombre_cliente>` es el nombre del cliente para el cual se está generando el reporte. El formato del archivo debe ser el siguiente:

    ```
    Top 3 artistas preferidos de <Nombre del cliente>
    
    1. <Nombre del artista 1>
    2. <Nombre del artista 2>
    3. <Nombre del artista 3>
    
    ```
[Volver al índice](#indice)

## Calificación

El programa debe compilar y ejecutar sin errores. Se debe cumplir con los siguientes requerimientos:


1. El programa debe cargar los archivos csv.(1.0)
2. El programa debe exportar los archivos csv.(1.0)
3. El programa debe permitir guardar los archivos serializados.(0.5)
4. El programa debe permitir cargar los archivos serializados.(0.5)
5. El programa debe generar los reportes solicitados, guardarlos en archivos de texto y mostrarlos en pantalla.(2.0)

**Este taller hace parte de su proyecto. Los posteriores talleres no se calificarán hasta que se haya completado este.
Si todo está correcto, sumará 2.0 a su proyecto final.
Este taller debe ser entregado durante la semana 14**

## ¿Qué sigue?

En el proyecto aún no se puede conocer información útil con respecto a las canciones, artistas, listas de reproducción y clientes. En el siguiente taller se trabajará en la creación de reportes que permitan conocer información relevante de la aplicación de música.

## Recursos en línea

- [Set in Java](https://www.geeksforgeeks.org/set-in-java/) [Artículo]
- [Map in Java](https://www.geeksforgeeks.org/map-interface-java-examples/) [Artículo]
- [Java IO - Curso](https://www.youtube.com/watch?v=v8ToJLBBfq8&list=PLTd5ehIj0goOxCwlYFWTKCYH1KeUx1qB1) [Video]
- [What is a CSV file?](https://data.europa.eu/apps/data-visualisation-guide/csv-files/) [Artículo]
- [Qué es CSV](https://www.youtube.com/watch?v=SaHIUR9jIPY) [Video]
- [Introduction to Java Serialization](https://www.baeldung.com/java-serialization) [Artículo]
- [Different ways of reading a text file in Java](https://www.geeksforgeeks.org/different-ways-reading-text-file-java/) [Artículo]