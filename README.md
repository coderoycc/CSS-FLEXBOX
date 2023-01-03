# CSS Flexbox 
Es un modelo de caja 

## ¿Qué se puede hacer con flexbox?
* Diseños flexibles con menos código.
* Alinear elementos de manera vertical u horizontal
* Re-ordenar contenido sin tocar HTML

## 10 reglas de oro para flexbox

### N° 1 Flexbox necesita un padre y por lo menos un hijo
* La etiqueta padre lleva como propiedad css `display: flex;`
   * Los hijos solo llevan sus propiedades css
   * La altura de los hijos depende de la etiqueta padre
   * La anchura de los hijos depende de la cantidad de su contenido
   * El posicionamiento inicial de los hijos depende del tipo de etiqueta que sean. (En linea o en bloque)

### N° 2 El Flex container tiene 2 ejes
* Flex container es conocido como el padre, los hijos como 'flex item'
* EJE PRICIPAL: `flex-direction: row;` Por defecto es horizontal
* EJE SECUNDARIO: `flex-direction: column;` Por defecto es vertical

### N° 3 Se puede modificar el eje principal con la propiedad flex-direction
* Si se aplica la propiedad `flex-direction` el eje secundario cambia
* ROW: Los elementos se alinean horizontalmente. El eje secundario pasa a ser COLUMN
* COLUMN: Los elementos se alinean verticalmente. El eje secundario pasa a ser ROW 
* Tambien se puede cambiar el orden de los elementos con `flex-direction: row-reverse;` o `flex-direction: column-reverse;`

### N° 4 Se puede permitir un salto de columns con flex-wrap
* Cuando se sobrepase el tamaño del contenedor padre se puede usar la propiedad flex-wrap en la etiqueta del padre.
* Por defecto los hijos se mantienen en una sola linea `flex-wrap:nowrap;`
* Existe la opcion de `flex-wrap:wrap-reverse;` que invierte el orden empezando desde abajo.

### N° 5 Alineamos elementos en el eje principal con justify-content
* La propiedad `justify-content` alinea a los hijos en el eje principal.
* Por defecto `justify-content: flex-start;`
* `justify-content: center;` centra los elementos en el eje principal
* `justify-content: space-between;` (pegado a los costados) distribuye los elementos desde el comienzo hasta el final con espacios iguales en el medio.
* `justify-content: space-around;` (Sin pegarse a los costados) distribuye los elementos con distribuciones iguales partiendo desde los alrededores. 
* `justify-content: flex-end;` distribuye a los elementos al final.

### N° 6 Alineamos elementos en el eje secundario con align-items
* Por defecto los hijos ocupan todo la alto|ancho que el padre les proporciona `align-items: stretch;`
* `align-items: flex-start;` alinea los hijos al inicio del eje secundario.
* `align-items: flex-end; ` alinea los hijos al final del eje secudario.
* `align-items: center;` centra a los hijos en el eje secundario.
* `align-items: baseline` elementos con texto (-)

### N° 7 Podemos alinear los elementos hijos de forma individual en el eje secundario con align-self
* Esta es la "primera" propiedad de aplica en el HIJO 
* Sobreescribe a la propiedad align-items del padre
* Se usa `align-self` para cambiar la propiedad del elemento hijo
* `align-self: flex-start;` alinea al elemento al inicio del eje secundario.
* `align-self: flex-end; ` alinea al elemento al final del eje secudario.
* `align-self: center;` centra al elemento en el eje secundario.
* `align-self: stretch;` hace que el elemento ocupe todo el espacio del eje sedundario definido por el padre.

### N° 8 Los hijos ignoran propiedades como float, clear, vertical-align
* Al aplicar flex a los hijos, ellos ignorarn las propiedades float: left, clear pues ya son parte del contexto flex.
* El padre si puede soportar las propiedades clear, float, vertical-align

### N° 9 Podemos modificar el tamaño de los hijos con flex-grow, flex-shrink, flex-basis
* Por defecto el tamaño de los hijos se define por el tamaño de su contenido.
* `flex-grow` Define el tamaño que crecerá el elemento (hijo) en relacion a sus hermanos cuando hay espacio en el contenedor (padre). Su valor por defecto es 0
   * Cuando se necesite agregar más espacio a un elemento (hijo) poner en su contenedor un número en relación a los demás. `flex-grow: 2` --> dos 'porciones'
* `flex-shrink` define el tamaño de reducción de un elemento (hijo) en relación a sus demás hermanos cuando falte espacio en el contenedor (padre). Por defecto es 1. 
   * Para cuando se necesite que un hijo no se reduzca cuando ya no haya espacio en el contenedor se pone `flex-shrink: 0;`
* `flex-basis` Define el tamaño inicial del elemento (hijo). Su valor por defecto es 'auto'. Es el tamaño base de un elemento
   * Un equivalente a `width` de los contenedores hijos
   * `flex-basis: 0; ` nos asegura que los contenedores tendran el mismo tañano al aplicar `flex-grow` cada porción sera de la misma manera. (no por el contenido del elemento hijo)

### N° 10 Podemos resumir todo con la propiedad flex
_flex: flex-grow flex-shrink flex-basis_
_flex: 0 1 100px_
* Para poder hacer más compacto las propiedades se puede usar `flex: 1 1 0px;` o `flex: 1 0px`
   * Lo que quiere decir que `flex-grow:1`, `flex-shrink:1` y `flex-basis: 0px;`
   * Es conveniente poner *0px* para evitar soporte en navegadores

### ADICIONAL ORDER Para ordernar los hijos
* El orden de cada hijo por defecto es *0*
* Cada hijo sigue un patron de orden de menor a mayor.
* `order: -1;` El hijo que tenga esta propiedad se posicionará al inicio de todos los elementos.
* `order: 1;` El hijo que tenga esta propiedad se posicionará después de todos los elementos hijo que tenga valores menores a *1*.