# Curso de Expresiones Regulares
Las expresiones regulares son patrones de carácteres que te permite ir seleccionando o descartando datos en un archivo de texto, por ejemplo, un csv, o en una línea o un input, según coincidan o nó con este patrón.

Debes ser muy selectivo y específico en ellas para encontrar lo que verdadermente necesitas.

## Aplicaciones de las expresiones regulares
Permiten filtrar texto, buscar patrones, validar formularios, etc. de forma sencilla y eficiente,filtrando con mucha velocidad enormes cantidades de texto.
Entre las aplicaciones de las expresiones regulares tenemos:

- Buscar informacion en los archivos log de un servidor, debido a que estos archivos generalmente son enormes y es muy probable que los editores de texto no los puedan manejar de forma simple.

- En archivos de texto plano con mas de un millón de líneas, para este caso son muy útiles las expresiones regulares puesto que quizas quieras traer solamente las lineas que inician con un log de un usuario que inice con la letra “a” y las expresiones regulares te lo facilitarían mucho.

- Validar patrones, por ejemplo, en un formulatio definir el formato de un correo electrónico y evaluar el texto que escribe el usuario con ese formato para saber si es un correo válido o no.

- Entre otros. 

## Expresiones generales
### El Carácter (***.***)

Antes de ahondar en cómo funciona el (**.**), primero algunas definiciones

- Archivo de texto: Serie de cadenas de carácteres o sucesión de líneas.

- Cadena de carácteres: Un carácter seguido de otro carácter, seguido de otro carácter.

- Carácter: Representación gráfica en bits de algún código, en mayor de los casos ASCII. Es la unidad mínima que se puede abstraer de una cadena de carácteres.

#### Funciones del .

El punto, nos permite seleccionar todos los carácteres en general(excepto salto de línea), espacios, letras, números, cada carácter se selecciona, y con ello se pueden dar diferentes condiciones, como lo puede ser encuentre un carácter con un espacio despues entonces buscaríamos [***.*** ], o queremos cualquier carácter que termine con io, entonces sería [***.io*** ], o tal vés que en el empieze con ciertos números contenga números [***78.***].
Otros ejemplos:
- Si se quiere una cadena de texto que contenga n elementos, si tomáramos n como 10 sería algo así [**..........**], es importante recordar que también encontrará espacios

## Clases predefinidas
Dentro del mundo de las Expresiones regulares(llamémoslas ahora REGEX), existen varias clases ya construidas que nos harán la búsqueda de datos más fácil, algunas de estas son:

|    REGEX    |         Qué hace        |                                                                                 Descripción                                                                                 |   
|:-----------:|:-----------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| .           | Character               | Cualquier carácter, selecciona cada uno de los carácteres                                                                                                                   |   
| \d          | Digit                   | Digits: (d minúscula) Encuentra todos los dígitos (número) de 0 a 9, es equivalente a poner [0-9].                                                                          |   
| \w          | Word                    | All word characters, Encuentra todos los carácteres que son parte de una palabra, tanto letras (minúsculas o mayúsculas) como números, es equivalente a poner [a-zA-Z0-9_]. |   
| \s          | Space                   | WhiteSpaces, Encuentra todos los espacios (los saltos de línea y tabuladores también son espacios).                                                                         |   
| [0-9]       | Specific Digit          | Encuentra todos los dígitos de 0 a 9, además, podemos varias de rango, no necesariamente necesitamos que sea del 0 al 9, también podemos manejar valores como [1-7], [6-9], entre todas sus posibles combinaciones                                                                                                                                       |   
| [0-9a-zA-Z] | Specific Word Character | Encontrará todos los carácteres que estén del 0-9 o que sean letras mayúsculas o minúsculas (\w)                                                                            |   
| [a-zA-Z]    |                         | nos encontrará solamente las letras, tanto mayúsculas como minúsculas del rango que querrámos                                                                                                     |   
| \           | Diagonal invertida      | Escapa los carácteres, permite que un carácter especial se muestre como el punto, **\\.**, coma       **\\.**, barra diagonal **\\\\**, entre otros.                                                                                                 |

Con todas estas opciones podemos hacer búsquedas gigantescas, desde binarios [0-1], hexadeximales [#][a-fA-F0-9]{6}, buscar un número de teléfono por cierto patrón ([\d]{2}[\.\-]?){5}

## Filtros Comunes
A la hora de buscar ciertos patrones hay unos más comunes y constantes que siempre sobresalen, y estos los repasaremos aquí, empezando por...

### URL's
Podemos decir que esta es la solución.

    https?:\/\/[\w\-\.]+\.\w{2,6}\/?\S*

Pero es importante saber de donde se obtiene esta expresión y lo haremos de la forma más simple, divide y vencerás, empezaramos a explicar pedazo por pedazo, partiendo de:
- ***https?:***  : el cual nace de que toda url parte de un protocolo HTTP, este puede ser seguro o no, por lo que la (***s***) queda como una posibilidad y los dos puntos(:) siguientes.

-  ***\\/\\/[\w\\-\\.]+\\.***: para este primero iniciamos con las dos barras invertidad que siempre van después del protocolo, luego de esto encerrado entre corchetes cuadrados (***\w***) llamamos cualquier letra o número, (***\\-\\.***) tenemos en cuenta que también pueden ser usados guiones o puntos, agregamos el (***+***) fuera del corchete para dejar claro que pueden aparecer más de una vez y por último, (***\\.***) agregamos al final el punto como delimitador.

- ***\w{2,6}\\/?\S\****: en este último caso, primero se dice que después del punto, (***\w{2,6}***) puede contener un conjunto de entre 2 y 6 letras que serían su dominio principal como  ejemplo: ***.com***, ***.edu***, ***.boeing***, entre otros, luego de esto,(***\\/?***) puede o no tener una barra diagonal, y se selecciona (***\S\****) todo lo que no sea un espacio si existe.

### Teléfonos
En el caso de números esta variación es muy amplia dependiendo del país, así que por ahora, solo trabajaremos con el caso colombiano. (Esperando ampliarlo a un futuro)


#### Números Colombianos

    ^([\+0]\d{2,2})?(\d{3,3}[\-\. ]?){2,2}\d{4,4}([#pe]\d{3,10})?$  

A primera vista esto puede parecer incomprensible, pero como en el paso anterior, lo separaremos por partes para hacerlo más fácil de comprender, empezaremos por los que está al principio y final.

- ***\^ ... \$*** : el acento circunflejo(***^***) o gorrito junto con el signo de dolar \(***\$***), se usan para indicar que se haga una única búsqueda por línea, por lo tanto, si el criterio no se cumple en la línea en general, no se selecciona.

- ***([\+0]\d{2,2})?*** : en este caso, se filtra si se usa o no, el indicativo del país, que está formado por el signo más o por un cero y después está seguido por dos dígitos.

- ***(\d{3,3}[\\-\\. ]?){2,2}*** : partiendo desde lo más chicho,***\d{3,3}*** este nos indica que debe haber una repetición de 3 dígitos, luego puede seguir un guión, punto o un espacio y toda esta cadena se debe repetir dos veces.

- ***\d{4,4}*** : Al igual que el paso anterior, se deben repetir 4 dígitos para terminar el número base.

- ***([#pe]\d{3,10})?*** : este último indicativo nos define si se usa o no extenciones, generalmente estas comienzan con (***#pe***), luego seguirá una serie de 3 a 10 dígitos. 

### Email 
Y de nuevo, otra expresión difícil de comprender a la primera.

    [\w\._]{5,30}\+?[\w]{0,10}@[\w\.\-]{3,}\.\w{2,6}$
Pero poco a poco, se entenderá cada parte, empezando por:

- ***[\w\\._]{5,30}\\+?*** : Empezamos con lso primeros corchetes, que nos indican que se van a manejar letras o números, donde puede contener un punto o una barra al piso y tendrá un largo de 5 a 30 carácteres, luego de esto puede que tenga un signo de suma.

- ***[\w]{0,10}@*** :se prosigue con un conjunto de letras o números de 0 a 10 carácteres, seguido de un arroba.

- ***[\w\\.\\-]{3,}*** : este actuaría como el nombre de la compañía (gmail, hotmail, etc...), que sería un conjunto de mínimo 3 carácteres, compuesto por letras, números, que pueden estar acompañados puntos o guiones.

- ***\\.\w{2,6}$*** : por último, el dominio que contiene el punto y un conjunto de 2 a 6 carácteres.

### Nombres

Para este caso de nombres, solo sería un filtro como ejemplo si se nos da un nombre completo y teniendo en cuenta algunos casos latinoamericanos.

    ^[A-Ú][a-ú]+(\s[A-Ú]?[a-ú]+\.?){1,4}$

- ***[A-Ú][a-ú]+*** : se incluyen letras mayúsculas o minúsculas, de la ***A*** a la ***Z***, incluyendo acentos y para el caso de las minúsculas debe haber una o más letras(+).

- ***(\s[A-Ú]?[a-ú]+\\.?){1,4}$*** : Diviéndolo por partes y entendiendo que lo que está adentro se reconocerá de 1 a 4 veces.
    - ***\s[A-Ú]?*** : reconociendo un espacio antes de la siguiente línea, y siendo posible que se use o no mayúscula al inicio.
    - ***[a-ú]+\\.?*** : para este caso se reconoce al menos una minúscula y puede que al finalizar haya un punto.



## Otros Recursos
- [Cheat sheet](https://www.cheatography.com/davechild/cheat-sheets/regular-expressions/pdf/).

- [REGEX Python](https://platzi.com/blog/expresiones-regulares-python/).

- [Practicar Jugando](https://regexone.com/).

- [Probar Expresiones 1](https://regexr.com/).

- [Probar Expresiones 2](https://rubular.com/).

- [Generar Data](https://generatedata.com)