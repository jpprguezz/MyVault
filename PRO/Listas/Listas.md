Las listas en Python permiten almacenar datos/objetos con un orden definido y además, con la posibilidad de hacer duplicados de esos datos. Estas son mutables, que como hemos visto, son aquellos datos en Python que se pueden modificar siempre que uno quiera, ya sea eliminando, añadiendo o cambiando los datos.

### Crear listas

Al igual que el string, una lista puede estar compuesta por cero o más elementos. Lo que la diferencia entre un string y una lista es que esta último necesita se crea con corchetes, y los datos dentro de ella se separan con comas. Esto sería algunos tipos de strings:

```python
empty_list = []
pokemons = ['Pikachu', 'Charmander', 'Squirtle', 'Bulbasaur']
natural_nums = [0, 1, 2, 3, 4]
```

Debemos recordar que al elegir un nombre para nuestra lista, NUNCA debemos llamarla "list". Al hacer esto, podríamos destruir la función list, haciéndola inservible para el resto de código.

### Conversión

También se nos ofrece la posibilidad de convertir datos directamente a listas, todo esto con la función `list()` pongamos el siguiente ejemplo:

```python
>>> list('Pikachu')
['P', 'i', 'k', 'a', 'c', 'h', 'u']
```

Como podemos ver, el string ha pasado a ser una lista de 7 elementos, siendo cada uno una letra del string, donde cada uno representa un elemento de la lista. Hay que tener en cuenta que esto se puede hacer con todo aquel dato que sea iterable.

Otra forma de mirar esto es con la función `range`, pongamos el siguiente ejemplo:

```python
>>> list(range(5))
[0, 1, 2, 3, 4]
```

Como podemos ver se muestran los números del range (menos 1), y cada numero es un elemento de la lista.

### Lista vacía 

Existe una forma de usar la función `list()` . Esta se puede usar sin pasarle ningún argumento. Esto hace que la función entienda que queremos crear una lista a partir de nada, por lo que la creará vacía directamente. Veamoslo:

```python
>>> list()
[]
```

Aunque esto funcione de forma correcta, al fin y al cabo es más "pitónico" el crear una variable y pasarle directamente a esa variable los corchetes vacíos.

### Operaciones con listas: Obtener un elemento

Al igual que en los strings, para acceder a los elementos en las listas, usamos los indices para saber el lugar que ocupa cada elemento en la lista. Veamos un ejemplo:

```python
>>> pokemons = ['Pikachu', 'Fearow', 'Pidgey']
 
>>> pokemons[0]
'Pikachu'
>>> pokemons[1]
'Fearow'
>>> pokemons[2]
'Pidgey'
>>> pokemons[-1] # Indice negativo
'Pidgey'
```

Incluso si probamos a acceder a un indice de la lista el cual no existe, Python nos dará un error, concretamente, uno que indica que estamos intentando acceder a un indice fuera del rango de la lista:

```python
>>> pokemons[-10]

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range
```

### Troceado de listas

Igualmente, el troceado de cadenas funciona exactamente igual. Veamos ejemplos:

```python
>>> pokemons = ['Pikachu', 'Fearow', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard']

>>> pokemons[2:4]
['Pidgey', 'Poliwrath']
>>> pokemons[1:6]
['Fearow', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard']
>>> pokemons[0:2]
['Pikachu', 'Fearow']
>>> pokemon[::-1] # Lo mismo que invertir la lista
['Charizard', 'Charmander', 'Poliwrath', 'Pidgey', 'Fearow', 'Pikachu']
```

A diferencia de intentar obtener los elementos de una lista, podemos escribir el rango de indices que queramos, ya que Python automáticamente restringe este rango:

```python
>>> pokemons[2:100]
['Pidgey', 'Poliwrath', 'Charmander', 'Charizard']
>>> pokemons[-100:3]
['Pikachu', 'Fearow', 'Pidgey']
```

### Invertir listas

El invertir una lista es un mecanismo importante a la hora de tratar con estas, ya que nos pueden ayudar en ciertas ocasiones. Veamos las diferentes maneras de invertir una lista:

- Troceado de lista con step en negativo
```python
>>> pokemons[::-1]
['Charizard', 'Charmander', 'Poliwrath', 'Pidgey', 'Fearow', 'Pikachu']
```

- Usando reversed
```python
>>> list(reversed(pokemons))
['Charizard', 'Charmander', 'Poliwrath', 'Pidgey', 'Fearow', 'Pikachu']
```

- Modificando la lista original
```python
>>> pokemons.reverse()
>>> pokemons
['Charizard', 'Charmander', 'Poliwrath', 'Pidgey', 'Fearow', 'Pikachu']
```

### Añadir al final de la lista

Como hemos dicho anteriormente, las listas son mutables. Esto implica que podemos añadir/modificar/eliminar datos. En este caso veremos como añadir datos a una lista ya creada, lo cual se haría con `append()`. Veamos ejemplos:

```python
>>> pokemons
['Pikachu', 'Fearow', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard']
>>> pokemons.append('Torchic')
>>> pokemons
['Pikachu', 'Fearow', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard', 'Torchic']
```

### Creando desde vacío

Una de las formas más comunes de trabajar con las listas es creándolas desde cero e ir añadiendo elementos progresivamente. Por ejemplo, creemos una lista con los números pares del 0 al 20:

```python
nums = []
for i in range(20):
	if i % 2 == 0:
		nums.append(i)

>>> nums
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

### Añadir en cualquier posición de una lista

Hemos visto el como añadir elementos al final de una lista, pero también podemos añadirlos en la posición que queramos. Para ello existe la función `insert()`. Para usarla debemos requerir de el indice en donde queramos introducir el dato y el dato en sí. Probemoslo:

```python
>>> pokemons = ['Pikachu', 'Fearow', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard', 'Torchic']
>>> pokemons.insert(2, 'Moltres')
>>> pokemons
['Pikachu', 'Fearow', 'Moltres', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard', 'Torchic']
```

Al igual que en el troceado de listas anteriormente, si insertamos un dato en una lista y nos intentamos pasar del indice de limite, Python añadirá ese elemento al final de la lista.

```python
>>> pokemons.insert(10000, 'Mankey')
>>> pokemons
['Pikachu', 'Fearow', 'Moltres', 'Pidgey', 'Poliwrath', 'Charmander', 'Charizard', 'Torchic', 'Mankey']
```

Aunque se pueda, siempre será mejor utilizar `append()` en el caso de que queramos añadir elementos al final de una lista, ya que siempre aportará legibilidad.

### Repetición de elementos

Al igual que lo hacen las cadenas de texto, con las listas podemos repetir los elementos simplemente usando el símbolo de multiplicación junto al numero de veces que queramos multiplicar esa lista:

```python
pokemons * 3
['Pikachu', 
 'Fearow', 
 'Moltres', 
 'Pidgey', 
 'Poliwrath', 
 'Charmander', 
 'Charizard', 
 'Torchic', 
 'Mankey', 
 'Pikachu', 
 'Fearow', 
 'Moltres', 
 'Pidgey', 
 'Poliwrath', 
 'Charmander', 
 'Charizard', 
 'Torchic', 
 'Mankey', 
 'Pikachu', 
 'Fearow', 
 'Moltres', 
 'Pidgey', 
 'Poliwrath', 
 'Charmander', 
 'Charizard', 
 'Torchic', 
 'Mankey']

```

### Combinación de listas

Python también nos ofrece una forma de combinar listas, para ello tenemos los dos siguientes métodos:

- Conservando la lista original usando el `+` o `+=` 

```python
>>> minecraft_objects = ['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> minecraft_objects + minecraft_blocks
['Pickaxe', 'Shovel', 'Sword', 'Axe', 'Stone', 'Sand', 'Cobblestone']
```

- Modificando la lista original usando la función `extend()`: 

```python
>>> minecraft_objects
['Pickaxe', 'Shovel', 'Sword', 'Axe', 'Stone', 'Sand', 'Cobblestone']
```

Este ultima caso funciona al cien por cien con las listas, esto implica que usar otros casos a lo mejor no es lo ideal:

```python
>>> minecraft_objects
['Pickaxe', 'Shovel', 'Sword', 'Axe', 'Stone', 'Sand', 'Cobblestone', 'O', 'b', 's', 'i', 'd', 'i', 'a', 'n']
```
Esto se debe a que `extend()` itera sobre cada elemento en la lista y al tener la palabra 'Obsidian' como elemento, itera sobre cada carácter de la misma, haciendo cada palabra un nuevo elemento.

Podríamos incluso plantear el uso de `append()` para unir la otra lista, pero el resultado no sería el esperado, ya que la cadena unida se introduciría como una subcadena:

```python
>>> minecraft_objects = ['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> minecraft_objects.append(minecraft_blocks)
>>> minecraft_objects
['Pickaxe', 'Shovel', 'Sword', 'Axe', ['Stone', 'Sand', 'Cobblestone']]
```

### Modificar una lista

Ahora veremos la manera que tenemos en Python de poder modificar cualquier dato que haya en una lista. Para ello requerimos el usar los indices:

```python
>>> minecraft_blocks[0]
'Stone'
>>> minecraft_blocks[0] = 'Netherrack'
>>> minecraft_blocks
['Netherrack', 'Sand', 'Cobblestone']
```

Y si intentamos acceder a un indice inexistente, pasará esto: 

```python
>>> minecraft_blocks[600] = 'End Stone'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range
```

### Modificar con troceado

Al igual que podemos modificar un elemento, podemos modificar más, y como sería lógico se hace troceando los elementos de la lista que queramos cambiar:

```python
>>> minecraft_blocks[1:4] 
['Sand', 'Cobblestone']
>>> minecraft_blocks[1:4] = ['Wood', 'Wool'] 
>>> minecraft_blocks
['Netherrack', 'Wood', 'Wool']
```

### Borrar elementos

Como hemos mencionado en varia ocasiones a lo largo del tema, podemos borrar cualquier elemento disponible en una lista. Esto se puede hacer de hasta cuatro maneras:

- Por indice, usando `del`

```python
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> del minecraft_blocks[1]
>>> minecraft_blocks
['Stone', 'Cobblestone']
```

- Por valor, usando la función `remove()`. Hay que tener en cuenta que si existen más algún elemento repetido, solo se eliminará la primera ocurrencia

```python
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> minecraft_blocks.remove('Stone')
>>> minecraft_blocks
['Sand', 'Cobblestone']
```

- Por extracción con indice, usando la función `pop()` . Esta lo que hace es extraer el elemento que deseemos, pero no solo lo extraerá, sino que también podemos guardar ese elemento extraído en una variable. Cabe destacar que si no le pasamos ningún indice a la función, eliminará el último carácter. Veamos algún ejemplo:

```python
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> minecraft_blocks.pop()
'Cobblestone'

>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> eliminated_block = minecraft_blocks.pop(1)
>>> eliminated_block
'Sand'
>>> minecraft_blocks
['Stone', 'Cobblestone']
```

- Por rango, mediante troceado de listas

```python
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> minecraft_blocks[0:1] = []
>>> minecraft_blocks
['Sand', 'Cobblestone']
```

### Borrado completo de la lista

Podemos también hacer borrados completos de listas. Para ello hay dos maneras:

- Usando la función `clear()` 
```python
>>> minecraft_objects
['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> minecraft_objects.clear()
>>> minecraft_objects
[]
```

- Reiniciando la lista a vacío con `[]` 
```python
>>> minecraft_objects = ['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> minecraft_objects = []
>>> minecraft_objects
[]
```

Las única diferencia se puede ver cuando en las id's que quedan antes y después de hacer los cambios. Al hacer el limpiado con `clear()`, la id sigue siendo la misma que antes de hacer la limpieza. Sin embargo al usar el método de reinicio, este hace que la id cambie, pasando a estar la lista en una nueva zona de memoria:

```python
>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> id(minecraft_blocks)
135206838386560
>>> minecraft_blocks.clear()
>>> id(minecraft_blocks)
135206838386560

>>> minecraft_blocks = ['Stone', 'Sand', 'Cobblestone']
>>> id(minecraft_blocks)
135206838249600
>>> minecraft_blocks = []
>>> id(minecraft_blocks)
135206846696256
```

En términos de eficiencia, hay que saber que `clear()` siempre será más rápido que reiniciar la lista.


### Encontrar un elementos

Si quisiéramos encontrar el índice concreto de algún elemento en la lista, usaríamos al igual que en los strings, la función `index()`:

```python
>>> minecraft_objects = ['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> minecraft_objects.index('Axe')
3
```

Aunque si intentamos buscar un elemento que no se encuentra en la lista, el intento de búsqueda nos devolverá un error.

```python
>>> minecraft_objects.index('Hammer')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'Hammer' is not in list
```

Y en el caso de que busquemos algún elemento que existe más de una vez en la lista, el comando nos devolverá el primer elemento que encuentre con ese nombre.

### Pertenencia de un elemento

En el caso de que quisiéramos comprobar si un elemento se encuentra en una lista, lo haríamos al igual que en los strings, usando el `in`:
```python
>>> 'Shovel' in minecraft_objects
True

>>> 'Hammer' in minecraft_objects
False
```

### Longitud de una lista

Para poder conocer cual es la longitud de una lista, podemos usar al igual que con un string, la función `len()`. Aunque como es lógico, sirve para conocer cuantos elementos posee la lista:

```python
>>> minecraft_objects = ['Pickaxe', 'Shovel', 'Sword', 'Axe']
>>> len(minecraft_objects)
4
```

### Número de ocurrencias

Podemos también contar la cantidad de veces que aparece un elemento en una lista. Para ello usamos `count()` y entre las comillas colocamos el elemento que deseemos contar, probemos:

```python
>>> pokemons_in_my_team
['Pikachu', 'Bulbasar', 'Squirtle', 'Squirtle', 'Pidgey', 'Nidoran']
>>> pokemons_in_my_team.count('Squirtle')
2
```

### Dividir una cadena de texto en lista

Una de las acciones más importantes en lo que respecta a listas, es el poder dividir cadenas de textos usando el separador de nuestra preferencia con la función `split()`. A esta función con simplemente pasarle el separador que queramos usar en forma de string, nos convertirá  nuestro string en una lista. Veamos ejemplos:

```python
>>> minecraft_end_poem
'And the game was over and the player woke up from the dream.'
>>> minecraft_end_poem.split()
['And', 'the', 'game', 'was', 'over', 'and', 'the', 'player', 'woke', 'up', 'from', 'the', 'dream.']

>>> queen_songs
'Seven Seas of Rhye / Sheer Heart Attack / Heaven for Everyone'
>>> queen_songs.split('/')
['Seven Seas of Rhye ', ' Sheer Heart Attack ', ' Heaven for Everyone']
```

Como hemos visto en el string 'minecraft_end_poem', al no pasarle ningún argumento a la función `split()`, esta divide de forma predeterminada el texto por los espacios.

### Particionado de cadenas de texto

Existe una forma un poco más elaborada para poder separar una cadena de texto, y esa es la función `partition()` . Esta lo que hace es coger algún argumento del string y usarlo como separador para dividir la cadena en tres partes: la parte de la izquierda, el separador, y la parte de la derecha. Esta como podemos debajo, devuelve una tupla:

```python
>>> text = '3 + 4'

>>> text.partition('+')
('3 ', '+', ' 4')
```

### Unir una lista en cadena de texto

Teniendo una lista, podemos usarla para convertirla a string, uniendo todos sus elementos con un separador de nuestra preferencia. Esto se hace usando la función `join()`. Esta se construye de esta manera:

![[Pasted image 20241121115055.png]]


Veamos ahora unos ejemplos:

```python
>>> minecraft_end_poem
['And', 'the', 'game', 'was', 'over', 'and', 'the', 'player', 'woke', 'up', 'from', 'the', 'dream.']
>>> ' '.join(minecraft_end_poem)
'And the game was over and the player woke up from the dream.'

>>> pokemons_in_my_team
 ['Pikachu', 'Bulbasar', 'Squirtle', 'Squirtle', 'Pidgey', 'Nidoran']
>>> '-'.join(pokemons_in_my_team)
'Pikachu-Bulbasar-Squirtle-Squirtle-Pidgey-Nidoran'
```

Como podemos ver, esta función es la opuesta a la anteriormente vista, `split()` 

### Ordenar una lista

Para ordenar una lista, tenemos tres opciones distintas en Python:

- Conservando la lista original usando la función `sorted()`:
```python
>>> pokemons_in_my_team 
['Pikachu', 'Bulbasar', 'Squirtle', 'Squirtle', 'Pidgey', 'Nidoran']
>>> sorted(pokemons_in_my_team)
['Bulbasar', 'Nidoran', 'Pidgey', 'Pikachu', 'Squirtle', 'Squirtle']
```

- Modificando la lista con la función `sort()`
```python
>>> pokemons_in_my_team 
['Pikachu', 'Bulbasar', 'Squirtle', 'Squirtle', 'Pidgey', 'Nidoran']
>>> pokemons_in_my_team.sort()
>>> pokemons_in_my_team
['Bulbasar', 'Nidoran', 'Pidgey', 'Pikachu', 'Squirtle', 'Squirtle']
```

Podemos también incluso añadir a la ecuación un parámetro booleano `reverse` con el fin de ordenar la lista al reves:

```python
>>> pokemons_in_my_team 
['Pikachu', 'Bulbasar', 'Squirtle', 'Squirtle', 'Pidgey', 'Nidoran']
>>> sorted(pokemons_in_my_team, reverse=True)
['Squirtle', 'Squirtle', 'Pikachu', 'Pidgey', 'Nidoran', 'Bulbasar']
```


### Iterar sobre una cadena de texto

Al igual que vimos en su momento con los strings, podemos iterar las listas elemento por elemento con la sentencia `for`:

```python
>>> pokemons_in_my_team
['Bulbasar', 'Nidoran', 'Pidgey', 'Pikachu', 'Squirtle', 'Squirtle']

>>> for pokemon in pokemons_in_my_team:
...     print(pokemon)
...
Bulbasar
Nidoran
Pidgey
Pikachu
Squirtle
Squirtle
```

Habrán veces que queramos iterar sobre una lista y queramos saber el índice de cada elemento iterado, para ello usaríamos en el texto que vayamos a iterar con for, la función `enumerate`:

```python
>>> pokemons_in_my_team
['Bulbasar', 'Nidoran', 'Pidgey', 'Pikachu', 'Squirtle', 'Squirtle']

>>> for i, pokemon in enumerate(pokemons_in_my_team):
...     print(i, pokemon)
...
0 Bulbasar
1 Nidoran
2 Pidgey
3 Pikachu
4 Squirtle
5 Squirtle
```


### Iterar sobre múltiples listas

En Python es posible iterar sobre varias listas de forma paralela usando la función `zip()`. Esta hace que la listas se vayan juntando elemento a elemento. Como comparación podríamos usar una cremallera, la cual tiene dos lados los cuales se van juntado a medida que pasa la el zip

![[Captura de pantalla 2024-11-21 122423.png]]

Después de haber visto esta explicación pongamos algún ejemplo:

```python
>>> gen1_pokemons
['Squirtle', 'Bulbasaur', 'Charmander']
>>> gen2_pokemons
['Cindaquil', 'Totodile', 'Chikorita']

>>> for gen1_pokemon, gen2_pokemon in zip(gen1_pokemons, gen2_pokemons):
...     print(gen1_pokemon, gen2_pokemon)
...
Squirtle Cindaquil
Bulbasaur Totodile
Charmander Chikorita
```

Debido a que `zip()` simplemente produce un iterador, si quisiéramos obtener una lista explícita con la combinación de listas, deberíamos construirla así:

```python
>>> gen1_pokemons
['Squirtle', 'Bulbasaur', 'Charmander']
>>> gen2_pokemons
['Cindaquil', 'Totodile', 'Chikorita']
>>> list(zip(gen1_pokemons, gen2_pokemons))
[('Squirtle', 'Cindaquil'), ('Bulbasaur', 'Totodile'), ('Charmander', 'Chikorita')]
```
