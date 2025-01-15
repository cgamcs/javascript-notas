# Agregar nuevos valores a un array

Este tema tiene que ver con una pregunta tecnica para conseguir trabajo "¿en qué valores una variable declarada en const se puede modificar sus valores? seria en objetos y en arreglos a menos que este congelado o sellado el objeto.

Podemos agregar un valor cambiando otro, ejemplo:

``` javascript
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio'];

meses[0] = 'Nuevo mes';
```

Eso cambiaria **Enero** por "Nuevo mes" ya que esta en la posicion 0, si queremos agregar un nuevo valor al arreglo debemos hacerlo al final de la lista:

``` javascript
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio'];

meses[7] = 'Nuevo mes';
```

Eso haria que el arreglo cambia a `['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio'. 'Nuevo mes']`

**NOTA**

En otros lenguajes si agregar el valor en un indice que no existe te agrega los indices faltantes en blanco, javascript no, lo que hace es solo dejar pasar los indices y agregar el valor en el indice que escribiste.

### Agregar con Array Methods

Si agregamos un elemento al arreglo con un indice eso dependera de que conozcamos la longitud del arreglo, para hacer de una forma mas dinamica utilizamos arreay methos en especifico uno conocido como `.push()` su sintaxis para agrerar un elemento seria la siguiente: `meses.push('Julio')`
