# 2020-js-vanilla-testing-003

<p align="center">
    <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/logo.png" >	
</p>

## Temario

* [Testeando String.prototype](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#testeando-stringprototype)
* [Arquitectura del proyecto](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#arquitectura-del-proyecto)
* [Diseñando nuestros Tests](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#dise%C3%B1ando-nuestros-tests)
    * [toString]()
    * [toFixed]()
* [Lanzando la Suite de Test](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#lanzando-la-suite-de-test)
    * [toString]()
    * [toFixed]()
* [Conclusiones](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#conclusiones)
* [Referencias](https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003#referencias)

### Testeando String.prototype
```
Como se ha visto en la teoría, cualquier Number de JavaScript tiene unos métodos por defecto 
que se pueden utilizar para hacer operaciones con ellos mismas. 

En la práctica de hoy vamos a proporcionar una solución con el testing de los métodos más
usados.
```

#### Jest - Framework Testing
```    
Basándonos en la practica '2020-js-vanilla-testing-003' vamos a crear una nueva carpeta llamada '003-testing'.
En ella instalaremos 'Jest' con el comando que nos proporciona 'npm'.

Crea una carpeta llamada '003-testing':
    $ mdkir 003-testing
    
Accede a ella :
    $ cd 003-testing

Instala 'Jest' con el siguiente comando:
    $ npm install --save-dev jest
 
Valida que la terminal te ha mostrado un mensaje terminado como este:
      npm WARN 003-testing No description
      npm WARN 003-testing No repository field.
      npm WARN 003-testing No README data
      npm WARN 003-testing No license field.
     
      + jest@25.2.3
      added 474 packages from 282 contributors and audited 1095501 packages in 31.784s
      found 0 vulnerabilities

Para saber que todo se ha instalado correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estas dos elementos:
    $ node_modules/  package-lock.json
    
Para poder ejecutar 'Jest' se necesita crear un fichero y añadir la dependencia.
    $ touch package.json

En la terminal, abrimos nuestro editor y copiamos el siguiente código:

'
{
  "scripts": {
    "test": "jest"
  }
}
'
Guardamos y cerramos el editor.

Para saber que todo se ha seguido correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estos tres elementos:
    $node_modules/  package.json  package-lock.json
```


### Arquitectura del proyecto

```
Lo primero que vamos hacer es diseñar nuestra suite de Test (paquetería) para tener el alcance 'end-to-end' 
de lo que queremos desarrollar.

En la propia carpeta '003-testing' ejecutamos el siguiente comando:
    $ touch suite.test.js

Dicho fichero va a permitir a 'Jest' ejecutar la bateria de Test que vamos a crear.
Actualmente el fichero está vacío. Simplemente nos interesa tener una buena arquitectura de proyecto.

Vamos a definir 5 tests que deben de hacer referencia a 5 funciones de String.prototypes.

Al estar en una etapa temprana, vamos hacer las cosas de la manera más fácil posible.

Vamos a definir 5 ficheros primeramente.

Ficheros 

* test03-toString.js
* test03-toFixed.js

Lanzamos el siguiente comando por la terminal de git-bash.
  $ touch test03-toString.js test03-toFixed.js


Para saber que todo se ha hecho correctamente, dentro de nuestra carpeta ejecutamos el comando:
    $ ls

Debes visualizar estas elementos:

node_modules/
package.json
package-lock.json
suite.test.js
test03-toFixed.js
test03-toString.js
```

### Diseñando nuestros Tests

```
Llegados a este punto lo que vamos hacer es diseñar nuestra bateria de test.
Con ella, lo que vamos a conseguir es tener un diseño primerizo que nos va a permitir tener
una primera visión.

Por supuesto, no vamos a implementar nada todavía, simplemente vamos a diseñar.

Nos basamos en el patrón AAA que vimos anteriormente y procedemos método a método:
```

#### toString
```
En la terminal, abrimos nuestro editor y copiamos el siguiente código en suite.test.js:

' 
    const toString = require('./test03-toString.js');                                            //L-1

    test('toString(789) to equals "789" )', ()=>{                                                //L-3
    // Arrange
    var expected = "789";                                                                        //L-5

    // Act
    var result = toString(789);                                                                  //L-8
    
    // Assert
    expect(result).toBe(expected);                                                               //L-11
    });                                                                                          //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'toString' necesita un parámetro de entrada.

Un primero parámetro donde va el número. 

El resultado es la separación la conversión del entero en una string.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de toString.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

#### toFixed

```
En la terminal, abrimos nuestro editor y copiamos el siguiente código (abajo) en suite.test.js:

' 
    const toFixed = require('./test03-toFixed.js');                                            //L-1

    test('toFixed(123456.52,5)  to equals "123456.52000" )', ()=>{                             //L-3
    // Arrang
    var toBe =  "123456.52000";                                                                //L-5

    // Act
    var result = toFixed(123456.52,5);                                                         //L-8
    
    // Assert
    expect(result).toBe(toBe);                                                                 //L-11
    });                                                                                        //L-12

'

Fíjese que estamos diseñando un test sin tener la implementación todavía.
Estamos dando por hecho que nuestra función 'toFixed' necesita dos parámetro de entrada.

Un primero parámetro donde va el número decimal. 
Un segundo parámetro con el índice a obtener de los decimales.

El resultado es la obtención de una string obteniendo el redondeo limitando sus decimales.

A continuación describimos cada una de las líneas:

L-1  - Permite a 'Jest' acceder a la función de nuestro algoritmo de toFixed.
L-3  - Define la cabecera de una función de Testing para el framework de 'Jest'. 
L-5  - Inicializamos variables.
L-8  - Llamámos al método de nuestro Test.
L-11 - Comparamos nuestro resultado esperado con el resultado del método que hemos desarrollado.
L-12 - Cierre de la función.

Cerramos el editor y volvemos a la terminal.
```

### Lanzando la Suite de Test
```
Ahora simplemente vamos a lanzar Jest por la terminal para ver que nuestro tests fallan.
Es necesario realizar este primer paso antes de dar implementación a nuestros tests.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:


        > @ test C:\Users\vbolinches\Documents\003-testing
        > jest

        FAIL ./suite.test.js
          ● Test suite failed to run

            Cannot find module './test03-split.js' from 'suite.test.js'

            > 1 | const split = require('./test03-toString.js');                                                 
                |                      ^
              2 |
              3 |     test('toString(789) to equals "789" )',  ()=>{          
              4 |     // Arrange

              at Resolver.resolveModule (node_modules/jest-resolve/build/index.js:296:11)
              at Object.<anonymous> (suite.test.js:1:22)


Es muy importante saber qué nos quiere decir el interprete de JS con este fallo...
Recordar que simplemente hemos diseñado y no hemos hecho implementación de nuestros algoritmos.

El error recalca que hay algún fallo en el fichero './test03-toString.js'. 
Exactamente indica que no resuleve un método exportado..
Obvio, no tenemos implementación.
```

### toString 
```
Ahora vamos a desarrollar nuestro algoritmo toString:

En la propia carpeta '003-testing' ejecutamos el siguiente comando:
    $ touch test03-toString.js

En este fichero vamos añadir una pequeña función que devuelvala conversión de un número 
en una string

Abrimos nuestro editor y copiamos el siguiente código:

' 
    function toString(param) {                                                       //L-1
        return param.toString();                                                     //L-2
    }                                                                                //L-3
   
    module.exports = toString;                                                       //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'split' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:

        FAIL ./suite.test.js
          √ toString(789) to equals "789") (4ms)
          × toFixed(123456.52,5)  to equals "123456.52000") (3ms)
                     ...
          
Hemos pasado el test en Verde!
Simplemente se queja de que el siguiente test no tiene implementación.

```

### toFixed 
```
Ahora vamos a desarrollar nuestro algoritmo charAt:

En la propia carpeta '003-testing' ejecutamos el siguiente comando:
    $ touch test03-toFixed.js

En este fichero vamos añadir una pequeña función que devuelve un string 
redondeado/limitando sus decimales.

Abrimos nuestro editor y copiamos el siguiente código:

'
    function toFixed(param, indice) {                                               //L-1
        return param.toFixed(indice);                                               //L-2
    }                                                                               //L-3
   
    module.exports = toFixed;                                                       //L-5
'

A continuación describimos cada una de las líneas:

L-1  - Define la cabecera de nuestro algoritmo, junto con el parametro de entrada.
L-2  - Línea que indica la devolución del resultado de nuestro método.
L-3  - Cierre de nuestro algoritmo.
L-5  - Almacena la función 'toFixed' en una variable que luego 'Jest' recupera con 
       la línea 1 del fichero suite.test.js 
       
Cerramos el editor y volvemos a la terminal.

Ejecutamos el siguiente comando :
    $ npm run test
    
Debemos de obtener la siguiente salida:
     
        FAIL ./suite.test.js
          √ toString(789) to equals "789") (4ms)
          √ toFixed(123456.52,5)  to equals 123456.52000) (3ms)
            ...
                        
Lo hemos hecho bien por segunda vez!
```


### Conclusiones
```
Hemos empezado hacer TDD sin miedo.
Poco a poco hemos cambiado la forma de pensar a la hora de desarrollar pequeñas funciones.
Hemos guiado el diseño de nuestros algoritmos a través de los test.
Hacemos efectiva la rueda del Testing. Primero fallar, luego acertar y en un furuto, refactorizar.

Revisa las referencias.
```


### Referencias
  * [Number.prototype](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Number/prototype)
  * [Desarrollo guiado por pruebas](https://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas)
  * [Test Driven Development by JavaScript](https://softwarecrafters.io/javascript/tdd-test-driven-development)
  
  
  
  
  
<div>
    <p align="center">
        <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/pixel.png" >	
    </p>
  </div>
  
  <footer>
     <div>
        <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-002"><< Atrás</a>
         <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-003/blob/master/README.md#referencias">
        <img src="https://github.com/GeeksHubsAcademy/2020-geekshubs-media/blob/master/image/pixel.png" align="center"                  height="10" width="714"/>
         </a>
         <a href="https://github.com/GeeksHubsAcademy/2020-js-vanilla-testing-004">Siguiente >></a>   
    </div>

