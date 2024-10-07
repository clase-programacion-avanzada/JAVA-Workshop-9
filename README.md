# Taller 9 - Maps, Sets, Archivos de texto y binarios

En este taller se trabajará la carga y escritura de archivos de texto y binarios. Se trabajará sobre el proyecto de la aplicación de música que se ha venido desarrollando en los talleres anteriores.

## Indice

1. [Preguntas teóricas](#preguntas-teóricas)
2. [Enunciado](#enunciado)
   1. [Estructura de los archivos de texto](#estructura-de-los-archivos-de-texto)
   2. [Archivos binarios](#archivos-binarios)
   3. [Cambios adicionales](#cambios-adicionales)
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

Para lograr esto, se recomienda crear una nueva vista que permita al usuario seleccionar la opción de cargar o guardar los archivos de texto o binarios.

### Estructura de los archivos de texto

Los archivos de texto se encuentran en la carpeta [resources](src/main/resources) del proyecto. Debe poner esos archivos en la misma carpeta de su proyecto. Estos archivos contienen la información de los artistas, canciones, listas de reproducción y clientes de la aplicación de música.

Los archivos CSV contienen la siguiente estructura:

- `artists.csv`: Contiene la información de los artistas. El archivo consta de una serie de líneas donde cada una representa un artista; cada uno de los atributos de un artista va a estar separado por el caracter _";"_. En el siguiente ejemplo, la información que inicia con _"#"_ indica que es un comentario, el archivo final no lo tendrá: </br>
    ```csv
        #id;name
        33f20939-c665-4e1d-aac1-e340c3d95656;Shakira
        62506fc4-639a-4160-8f26-6c478462621e;Wyclef Jean
    ```
- `songs.csv`: Contiene la información de las canciones. El archivo consta de una serie de líneas donde cada una representa una canción; cada uno de los atributos de una canción va a estar separado por el caracter _";"_. En el siguiente ejemplo, la información que inicia con _"#"_ indica que es un comentario, el archivo final no lo tendrá: </br>
    ```csv
        # id;name;{artist_id1,artist_id2...};genre;duration;album
        # Nota: Los artistas de la canción están separados por comas y encerrados entre llaves.
        # En este caso, la canción 'Hips Don't Lie' de Shakira y Wyclef Jean está en el archivo.
        
        92ab9e23-613e-4ae3-9378-0824e846836c;Hips Don't Lie;{33f20939-c665-4e1d-aac1-e340c3d95656,62506fc4-639a-4160-8f26-6c478462621e};Pop;223;Oral Fixation, Vol. 2
    ```
- `playlists.csv`: Contiene la información de las listas de reproducción. El archivo consta de una serie de líneas donde cada una representa una lista de reproducción; cada uno de los atributos de una lista de reproducción va a estar separado por el caracter _";"_. En el siguiente ejemplo, la información que inicia con _"#"_ indica que es un comentario, el archivo final no lo tendrá: </br>
    ```csv
        # id;name;{song_id1,song_id2...}
        # Nota: Las canciones de la lista de reproducción están separadas por comas y encerradas entre llaves.
        # En este caso, la playlist 'PlayList2' contiene la canción 'Hips Don't Lie'.
        
        4e9f14c7-70d5-4059-9fa6-fe59272bc375;PlayList2;{92ab9e23-613e-4ae3-9378-0824e846836c}
    ```
- `customers.csv`: Contiene la información de los clientes. El archivo consta de una serie de líneas donde cada una representa un cliente; cada uno de los atributos de un cliente va a estar separado por el caracter _";"_. En el siguiente ejemplo, la información que inicia con _"#"_ indica que es un comentario, el archivo final no lo tendrá: </br>
    ```csv
        # id;username;password;first_name;last_name;age;{artist_id1,artist_id2...};{playlist_id1,playlist_id2...}
        # Nota: Los artistas y las listas de reproducción del cliente están separados por comas y encerrados entre llaves.
        # En este caso, el cliente 'Juan' sigue a Shakira y tiene la lista de reproducción 'PlayList2'.
        
        # En este caso, el cliente 'Marcusfenix' tiene 34 años y tiene la playlist 'PlayList2'.
        # Además, sigue a Shakira.
               
         d4e6c3c7-54eb-4edc-94c7-416504663f82;Marcusfenix;G3ars_1234567;Marcus;Fenix;34;{33f20939-c665-4e1d-aac1-e340c3d95656};{4e9f14c7-70d5-4059-9fa6-fe59272bc375}
    ```
Los archivos de texto deben poder ser leídos y escritos por el programa. Al ser escritos, debe tener la misma estructura que los archivos de ejemplo (incluyendo los saltos de línea).

### Archivos binarios

Los archivos binarios se encuentran en la carpeta [resources](src/main/resources) del proyecto. Estos archivos contienen la información de los artistas, canciones, listas de reproducción y clientes de la aplicación de música.

Los archivos binarios contienen la información serializada de las clases. Estos archivos deben poder ser leídos y escritos por el programa.

### Cambios adicionales

Además de estos cambios, se debe modificar el modelo de clientes para que el atributo `followedArtists` sea un `Set` en lugar de una lista. Esto se debe a que un cliente no puede seguir a un mismo artista más de una vez.

[Volver al índice](#indice)

## Calificación

El programa debe compilar y ejecutar sin errores. Se debe cumplir con los siguientes requerimientos:

1. Las clases deben estar en los paquetes correctos (servicios, controladores, vistas, modelos y excepciones). (0.25)
2. La clase `Main` y las clases del paquete `views` son las únicas que pueden interactuar con el usuario.(0.25)
3. Los controladores deben llamar a los métodos de los servicios correspondientes.(0.25)
4. Los servicios deben llamar a los métodos de las clases del paquete `models` correspondientes.(0.25)
5. El programa debe cargar los archivos csv.(1.0)
6. El programa debe exportar los archivos csv.(1.0)
7. El programa debe permitir guardar los archivos serializados.(1.0)
8. El programa debe permitir cargar los archivos serializados.(1.0)

**Este taller hace parte de su proyecto. Los posteriores talleres no se calificarán hasta que se haya completado este.
Si todo está correcto, sumará 1.0 a su proyecto final.
Este taller debe ser entregado durante la semana 13**

## ¿Qué sigue?

En el proyecto aún no se puede conocer información útil con respecto a las canciones, artistas, listas de reproducción y clientes. En el siguiente taller se trabajará en la creación de reportes que permitan conocer información relevante de la aplicación de música.

## Recursos en línea

- [Set in Java](https://www.geeksforgeeks.org/set-in-java/) [Artículo]
- [Map in Java](https://www.geeksforgeeks.org/map-interface-java-examples/) [Artículo]
- [Java IO - Curso](https://www.youtube.com/watch?v=v8ToJLBBfq8&list=PLTd5ehIj0goOxCwlYFWTKCYH1KeUx1qB1) [Video]
- [What is a CSV file?](https://data.europa.eu/apps/data-visualisation-guide/csv-files/) [Artículo]
- [Qué es CSV](https://www.youtube.com/watch?v=SaHIUR9jIPY) [Video]
- [Introduction to Java Serialization](https://www.baeldung.com/java-serialization) [Artículo]