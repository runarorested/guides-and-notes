# ![jQuery](https://logodownload.org/wp-content/uploads/2017/10/jquery-logo-6.png)
jQuery es una biblioteca de funciones Javascript/ECMAscript, que permite operar de manera más sencilla e independiente del navegador o del grado de soporte o compatibilidad que este ofrece.

jQuery se encargará de abstraer o emular la funcionalidad necesaria si el navegador no la ofrece.



## Introducción y conceptos básicos

### Navegador web
> Programa que permite visualizar información hipertextual y multimedia, e interactuar con ella, proveniente de otros ordenadores, a través de redes IP como Internet, mediante protocolos y estándares como HTTP, HTML, CSS y Javascript.

### Redes IP

> Redes basadas en el protocolo de Internet. Son redes que emplean un sistema de direccionamiento virtual no vinculado al hardware (Dirección IP), para referirse a los ordenadores y/o dispositivos que la componen. 
>
> Actualmente existen dos versiones coexistiendo a la vez: 
>
> * IPv4, evolución de versiones anteriores, y basada en direcciones de 32 bits (4 bytes, expresados como 4 números decimales de 8 bits separados por puntos [.]),
>   Ej:
>
>   > 1.1.1.1
>   > 192.168.3.120
>
> * IPv6, basada en direcciones de 128 bits (16 bytes, expresados como 8 números hexadecimales de 16 bits, separados por dos puntos [:]). Una secuencia de varios ceros se puede abreviar con doble dos puntos [::].
>   Ej:
>
>   > 2606:4700:4700::1111, equivalente a 2606:4700:4700:0:0:0:0:1111, 
>   >
>   > ::ffff:c0a8:378, equivalente a 0:0:0:0:0:ffff:c0a8:0378

### HyperText Transfer Protocol (HTTP)

> **Protocolo de Transferencia de Hipertexto**, que permite consultar e interactuar con páginas web creadas en lenguaje HTML y variantes, y sus recursos multimedia asociados.

### HyperText Markup Language (HTML)

> El **Lenguaje de Marcas para Hipertexto** es un lenguaje de marcas basado en SGML que permite (según el entendimiento moderno) describir, estructurar y maquetar un documento de texto y sus recursos multimedia asociados, dándoles formato mediante CSS, y dotándolo de interactividad en el lado del cliente más allá de simple hipertexto mediante scriptlets en Javascript.
>
> Ej:
>
> ```html
> <h1 id="cabecera">Título</h1>
> <p class="introduccion">Un párrafo de texto.</p>
> <p>Otro párrafo con un <a href="http://URL">enlace de hipertexto</a>.</p>
> ```

### Cascading Style Sheets (CSS)

> Las **Hojas de Estilo en Cascada** es un sistema de notación de propiedades (mayormente gráficas) asociadas a fragmentos de texto HTML, especificadas mediante reglas de aplicación. Estas reglas de aplicación se basan en:
>
> * etiquetas HTML (`<a>`, `<p>`)
> * identificadores únicos (**#id**), 
> * etiquetas de clase (**.cabecera**)
> * combinaciones mediante reglas de selección o **selectores** (**.introduccion + p**)
>
> Estas se aplican en orden secuencial, y mediante un sistema de prioridades. De menos a más prioridad:
>
> CSS externa enlazada &rarr; CSS en cabecera (`<style>`) &rarr; etiqueta style (`style="..."`)

### Javascript/ECMAscript

> Javascript es un **lenguaje de programación** **interpretado**, de **tipado dinámico** **débil**, **sin arrays**, y con abstracciones basadas en **objetos** y **prototipos**. Eso significa que:
>
> * *Interpretado*, es un lenguaje cuyas instrucciones son ejecutadas por un intérprete, runtime o máquina virtual.
>
> * *tipado dinámico*, indica que las variables se declaran sin tipo, y asumen el tipo de los valores que se le asignan.
>   Ej:
>
>   ```javascript
>   var variable;
>   console.log(typeof variable); # "undefined"
>     
>   variable = true;
>   console.log(typeof variable); # "boolean"
>     
>   variable = 3;
>   console.log(typeof variable); # "number"
>   variable = 3.3;
>   console.log(typeof variable); # "number"
>   variable = "0.0";
>   console.log(typeof variable); # "string"
>     
>   variable = {};
>   console.log(typeof variable); # "object"
>   variable = null;
>   console.log(typeof variable); # "object"
>     
>   variable = function(x) { return x.toString(); };
>   console.log(typeof variable); # "string"
>   variable = (x) => x.toString();
>   console.log(typeof variable); # "string"
>     
>   variable = [1, 2, 3]; # No hay arrays como tipos de datos, solo objetos con propiedades de índices numéricos.
>   console.log(typeof variable); # "object"
>     
>   ```
>
> * *tipado debil*, indica que los tipos de las variables pueden cambiar dinámicamente según lo necesite el código, sin intervención del programador. Esto puede causar innumerables conversiones de tipos automáticas que ralenticen la ejecución del código, y causen errores al tener los operadores diferente funcionalidad según se ejecuten sobre un tipo o otro. 
>   Ej:
>
>   ```javascript
>   var correcto    =  2  +  3 ; # int:5       = int:2 + int:3 ; SUMA
>     
>   var incorrecto1 = "2" + "3"; # string:"23" = string:"2" + string:"3" ; CONCATENACIÓN
>     
>   var incorrecto2 =  2  + "3"; # string:"23" = int:2 + string:"3" ; INOPERABLE. CONVERSION TRANSPARENTE A STRING
>   var incorrecto2 =  (2).toString()  + "3"; # string:"23" = string:"2" + string:"3" ; CONCATENACIÓN
>   ```
>
> * *objetos*, son básicamente arrays de claves heterogeneas (múltiples tipos de variables). Si una de sus propiedades es de tipo valor (boolean, number, string), es una propiedad. Si es una función, es un método. La invocación de una función o método se realiza con los paréntesis para contener los parámetros, si los hay. Si hay una función definida, y se desea llamarla como si fuese un método (tiene acceso al `.this` de un objeto), se puede emplear la función `func.call(obj, param1, param2, ...)`.
>   Ej:
>
>   ```javascript
>   var aHero = { "name": "Peter", "surname":"Parker", "alias": "Spider-Man", "adjetive":"amazing",};
>     
>   var capitalize = function() { return this.replace(/\w\S*/g, (w) => (w.replace(/^\w/, (c) => c.toUpperCase())));
>   var fullName = function() { return this.name + ' ' + this.surname + ', ' + ('the ' + this.adjetive + ' ' + this.alias).capitalize; }
>     
>   console.log(fullName.call(aHero));
>   ```
>
>   Existen varios objetos pre-generados por el lenguaje, con algunos métodos: 
>
>   * El **Object** base, que contiene métodos para gestionar la consulta de propiedades, prototipos y getters y setters automáticos.
>   * El **Array**, que en este caso es un objeto que permite asignar propiedades numéricas, y contiene el método/propiedad `.length` para consultar su longitud/número de elementos, emulando la presencia de arrays nativos.
>
> * *prototipos*, es un sistema de abstracción de datos basado en el modelo de objetos, pero en el que no existe el concepto de *clase* como tipo de dato. Lo que existe es una propiedad mágica llamada *prototipo* o `.__proto__`, que contiene/enlaza con otro objeto. Cuando se llama/consulta una propiedad o método y este no existe en el objeto consultado, se mira si tiene un prototipo, si esta existe en el prototipo, y se ejecuta. Si no es así, esta consulta es recursiva, hasta que un objeto es un objeto raíz o padre, sin prototipos. A veces se describe como *overlay chaining*.

### Document Object Model (DOM)

> El *modelo de objetos del documento* es una estructura de datos de tipo grafo, en forma de árbol, que refleja la estructura del documento HTML. Esta estructura puede ser consultada, navegada y modificada mediante el lenguaje Javascript empleando una serie de objetos y métodos presentado al entorno de ejecución. 
>
> Ej: El entorno Javascript del navegador tiene un objeto `window` que funciona como ámbito de ejecución. En este objeto se puede consultar el documento cargado como otro objeto, `document`, y a través de este, navegar una estructura árbol de nodos que representan los textos y las etiquetas HTML del documento. 
> Los objetos en sí no son objetos puros, sino interfaces que interactúan con el nodo equivalente nativo del navegador.



## Funcionamiento

**jQuery Core** es una biblioteca centrada en la consulta y manipulación del DOM a través de un objeto  principal, `jquery`, basado en un objeto de tipo función. Esto permite invocarla como una función en vez de emplear un método (`jquery()` en vez de `jquery.select()`). Esta, a su vez, tiene una serie de alias creados dentro del objeto de alcance global (`window` en el caso de un navegador), lo cual la convierte en algo similar a una extensión del lenguaje. Esos alias son `window.jquery()` y `window.$()`. 

jQuery también posee extensiones y un sistema de plug-ins, capaces de extender sus características o generar plantillas prediseñadas con funcionalidad incluida. Algunas de estas extensiones son oficiales, como las de creación de interfaces de usuario, **jQuery UI**, y la extensión para el tratamiento de gestos y opciones específicas para dispositivos móviles, **jQuery Mobile**. 

El proyecto además mantiene un framework de pruebas unitarias en Javascript, **QUnit**, valido para todos los entornos (incluidos servidores, con NodeJS), y la función de parseado de selectores del DOM como proyecto independiente, **Sizzle**.

Los plug-ins permiten crear layouts dinámicos, galerías de fotos, presentaciones de imágenes, animaciones, transiciones,  validación de formularios en cliente, búsqueda en vivo, autocompletado de sugerencias,  y mucho más.

### Modo de funcionamiento

El modo de funcionamiento es sencillo. Si se invoca la función sobre un objeto del DOM, este es encapsulado, dotándole de métodos que ofrecen funcionalidades independientemente del navegador y del grado de soporte/modernidad de este.  Dependiendo del argumento que se le pase a dicha función, esta actuará como si fuesen métodos radicalmente diferentes.

* Si es un objeto del DOM, extenderá este objeto según sea necesario para ofrecer funcionalidades adicionales o suplir funcionalidades que navegadores modernos ofrecen de forma estandar, mediante métodos independientes del navegador subyacente.
* Si es una función, la asocia a una función lanzada al finalizar la carga (evento `load`, método `$.ready()`).
* Si es una cadena de texto, esta trata de interpretarse como un selector CSS (con alguna extensión sobre estos), y se devuelve unal ista de nodos

Por ejemplo, `$(document).ready(func)` extenderá el objeto `document` y le dotará de un método `.ready()`, encargado de ejecutar la función que se le pase, cuando el documento HTML haya terminado de cargarse y su contenido haya sido interpretado y reflejado en el DOM del navegador. Este ofrece siempre la misma funcionalidad, de forma independiente a:

* si es un navegador moderno que simplemente crea un `listener` al evento `load`, 
* si es uno más antiguo que emplea otros eventos o métodos, o estos tienen nombres diferentes,
* o incluso consulta el estado de alguna variable de forma periódica hasta que esta indica que ha terminado de cargar (*polling* en lugar de *callbacks*).

Ej:

```javascript
# Todo este código es equivalente.

# Notación completa
window.jquery( document ).ready( function() {
	console.log('¡Documento cargado y listo para manipular!')
} );

# Notación abreviada JS: 
#    window.jquery => $
$( document ).ready( function() {
	console.log('¡Documento cargado y listo para manipular!')
} );

# Notacion abreviada jQuery: 
#    Si el argumento es una función, se asume que es una abreviatura de un callback para $(document).ready
$( function() {
	console.log('¡Documento cargado y listo para manipular!')
} );


```







[How to know the type of an object in JavaScript? (tutorialsteacher.com)](https://www.tutorialsteacher.com/articles/how-to-get-type-of-object-in-javascript)

[Node - Web APIs | MDN (mozilla.org)](https://developer.mozilla.org/en-US/docs/Web/API/Node)
