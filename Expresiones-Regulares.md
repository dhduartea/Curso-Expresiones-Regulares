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

Con todas estas opciones podemos hacer búsquedas gigantescas, desde binarios [0-1], hexadeximales [#][a-fA-F0-9]{6}

## Otros Recursos
- [Cheat sheet](https://www.cheatography.com/davechild/cheat-sheets/regular-expressions/pdf/).

- [Probar Expresiones 1](https://regexr.com/).

- [Probar Expresiones 2](https://rubular.com/).
