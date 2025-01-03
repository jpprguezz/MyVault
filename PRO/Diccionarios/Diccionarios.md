Al fin y al cabo, un diccionario en Python es lo mismo que sería un diccionario en la vida real: un objeto que guarda una palabra y su significado. En Python un diccionario indexa una clave (la palabra) y un valor (el significado de esa palabra).

![[clave_valor.png]]


Los diccionarios poseen las siguientes características:

- El orden del diccionario es el de inserción de claves.
- Son mutables.
- Las claves deben ser únicas. Normalmente se utilizan los strings como claves, aunque se puede utilizar también cualquier dato inmutable.
- Debido a como están implementados internamente, los diccionarios poseen la capacidad de ser accesibles rapidamente.

#### Creando diccionarios

Para poder crear un diccionario, hacemos lo siguiente:

```python
empty_dict = {}
```

Y para incluir contenido en el tenemos que seguir la estructura de clave-valor seguida por separadas entre ellas por ":" y separando entre comas cada adición al diccionario, así:

```python
pokemons = {
		'Pikachu' : 'Pokémon eléctrico de 1º generación',
		'Elekid' : 'Pokemon eléctrico de 2º generación'	
}
```

Debemos de tener en cuenta que a la hora de crear un nuevo diccionario, NUNCA debemos llamarlo dict, ya que como hemos visto en muchos casos, esto podría romper la función propia. Tampoco podemos usar nombre derivados (por ejemplo -dict).


#### Conversión 

Para convertir otros datos a un diccionario, poseemos de la función llamada "dict()":

```python
# lista a diccionario
>>> dict(['a1', 'b2'])
{'a': '1', 'b': '2'}

# tupla a diccionario
>>> dict(('a1', 'b2'))
{'a': '1', 'b': '2'}

# lista de listas a diccionario
>>> dict([['a', 1], ['b', 2]])
{'a': 1, 'b': 2}
```

Como vemos en los ejemplos, cualquier colección de elementos que puedas recorrer (ya sea una tupla o lista) donde hayan dos valores juntos, puede ser transformado a diccionario con la función "dict()"

#### Diccionarios vacíos

Al usar la función dict() sin pasarle nada, podemos crear un diccionario vacío. Esto es así ya que al no pasarle nada, lo que hace la función es intentar crear un diccionario de nada, lo que hace que nos quedemos con solo los corchetes. Aunque siempre es más recomendable usar simplemente los corchetes ("{}") al igual que se hace con las listas vacías:

```python
empty_dict1 = dict()
empty_dict = {}
```


#### Creación con dict()

Podemos usar la función para crear diccionarios, para así no tener que utilizar las llaves y las comas. Supongamos que tenemos estas claves y valores que queremos colocar en un diccionario: 

| Nombres  | Descripción              |
| -------- | ------------------------ |
| Thorfinn | Guerrero en busca de paz |
| Askeladd | Astuto líder mercenario  |
| Thorkell | Guerrero fuerte y audaz  |

Usando dict() podemos pasar las claves y valores como argumentos de la función:

```python
>>> vinland_saga_characters = dict(
... Thorfinn = 'Guerrero en busca de paz',
... Askeladd = 'Astuto líder mercenario',
... Thorkell = 'Guerrero fuerte y audaz'
... )

vinland_saga_characters
{'Thorfinn': 'Guerrero en busca de paz', 'Askeladd': 'Astuto líder mercenario', 'Thorkell': 'Guerrero fuerte y audaz'}
```

El mayor inconveniente que tiene esta aproximación, es que las claves que queramos asignar a los valores, deben ser validas. Pongamos el ejemplo de que quisiéramos crear una clave con espacios en ella: 

```python
>>> person = dict(
...     name='Guido van Rossum',
...     date of birth='31/01/1956'
  File "<stdin>", line 3
    date of birth='31/01/1956'
          ^
SyntaxError: invalid syntax
```

Incluso si quisiéramos, podríamos crear un diccionario especificando sus claves, y un único valor de relleno para todas estas claves:

```python
>>> dict.fromkeys('pikachu', 25)
{'p': 25, 'i': 25, 'k': 25, 'a': 25, 'c': 25, 'h': 25, 'u': 25}
```


#### Operaciones con diccionarios

Ahora comprobaremos algunas de las operaciones que podemos hacer con los diccionarios:

- **Obtener un elemento**

Para obtener el valor de cualquier elemento de un diccionario, basta con simplemente escribir el nombre del diccionario, así como la clave de dicho elemento entre corchetes.

```python
>>> vinland_saga_characters = dict(
... Thorfinn = 'Guerrero en busca de paz',
... Askeladd = 'Astuto líder mercenario',
... Thorkell = 'Guerrero fuerte y audaz'
... )

>>> vinland_saga_characters['Thorkell']
'Guerrero fuerte y audaz'
```

Y si intentáramos acceder a una clave que no existe, nos daría como resultado un error:

```python
>>> vinland_saga_characters['Leif']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'Leif'
```

- **Usar get()**

En Python existe una función bastante útil, que puede ayudar a evitar errores por acceso de claves inexistentes. Esta función es get() y funciona de la siguiente manera:

1. Si la clave que buscamos existes, nos devuelve su valor
2. Si no existe, nos devuelve None, a menos que le indiquemos otro valor. Pero en ninguno de los casos obtendremos un error.

```python
>>> vinland_saga_characters.get('Thorfinn')
'Guerrero en busca de paz'
>>> vinland_saga_characters.get('Leif')  # Aunque no se vea, devuelve None
>>> vinland_saga_characters.get('Leif', 'Gudrid')  # Como el primer elemento pasado, no esta en el diccionario, la función devuelve el segundo elemento (es decir el valor aportado por defecto)
'Gudrid'
```

- **Añadir o modificar un elemento**

Para añadir un elemento a un diccionario, simplemente hacemos referencia a la clave, y le asignamos su valor:

Si la clave ya estaba en el diccionario, se reemplaza el valor que estaba por el nuevo. En cambio, si la clave es nueva, se añade al diccionario con su valor. En el caso de los diccionarios, aquí no se obtiene un error, a diferencia de las listas.

Para probar esto, pongamos de ejemplo el diccionario que ya teníamos. A este le vamos a añadir el personaje de Leif:

```python
>>> vinland_saga_characters['Leif'] = 'Explorador formidable'
>>> vinland_saga_characters
{'Thorfinn': 'Guerrero en busca de paz', 'Askeladd': 'Astuto líder mercenario', 'Thorkell': 'Guerrero fuerte y audaz', 'Leif': 'Explorador formidable'}
```

Si quisiéramos modificar la descripción de Leif, simplemente haríamos el mismo proceso hecho para añadir un nuevo elemento, pero simplemente le pondríamos una nueva descripción:

```python
>>> vinland_saga_characters['Leif'] = 'Explorador formidable y audaz'
>>> vinland_saga_characters
{'Thorfinn': 'Guerrero en busca de paz', 'Askeladd': 'Astuto líder mercenario', 'Thorkell': 'Guerrero fuerte y audaz', 'Leif': 'Explorador formidable y audaz'}
```

- **Creando desde vacío**

Una de las formas más comunes para trabajar con diccionario, es el usar el patrón de creación partiendo de un diccionario vacío e ir añadiendo los elementos poco a poco. Pongamos el ejemplo en el queremos construir un diccionario con las claves como vocales, y los valores son sus posiciones:

```python
>>> VOWELS = 'aeiou'
>>> enum_vowels = {}
>>> for i, vowel in enumerate(VOWELS, start=1):
...     enum_vowels[vowel] = i
...
>>> enum_vowels
{'a': 1, 'e': 2, 'i': 3, 'o': 4, 'u': 5}
```

#### Pertenencia de una clave

Dentro de Python, existe una forma pitónica para poder comprobar la existencia de una clave dentro de un diccionario. Esto es posible gracias al operador in, ya visto en otros temas. Como sabemos, este operador devuelve un valor booleano (es decir True o False):

```python
>>> 'Thorfinn' in vinland_saga_characters
True
>>> 'Snake' in vinland_saga_characters
False
```

#### Longitud de un diccionario

Podemos comprobar la cantidad de elementos que hay en un diccionario (es decir, el conjunto de clave-valor), usando la función ya vista en otros temas, llamada len():

```python
>>> len(vinland_saga_characters)
4
```

#### Obtener todos los elementos

Python ofrece mecanismos para poder obtener todos los elementos de un diccionario. Veamos las diferentes opciones:

- **Obtener todas las claves de un diccionario usando la función keys()**

```python
>>> vinland_saga_characters.keys()
dict_keys(['Thorfinn', 'Askeladd', 'Thorkell', 'Leif'])
```

- **Obtener todos los valores de un diccionario usando la función values()**

```python
>>> vinland_saga_characters.values()
dict_values(['Guerrero en busca de paz', 'Astuto líder mercenario', 'Guerrero fuerte y audaz', 'Explorador formidable y audaz'])
```

- **Obtener todos los conjuntos de elementos (claves-valor) usando la función items()**

```python
>>> vinland_saga_characters.items()
dict_items([('Thorfinn', 'Guerrero en busca de paz'), ('Askeladd', 'Astuto líder mercenario'), ('Thorkell', 'Guerrero fuerte y audaz'), ('Leif', 'Explorador formidable y audaz')])
```

Hay que tener en cuenta que para el ultimo caso de obtención de elementos, los items se devuelven en forma de tuplas y cada tupla posee dos elementos, siendo el primer elemento la clave y el segundo el valor.

#### Iterar sobre claves

En base a la forma que hemos visto anteriormente para poder obtener los distintos elementos de un diccionario iterando sobre el mismo. Veamos los distintos ejemplos:

- **Iterar sobre claves**

```python
>>> for word in vinland_saga_characters.keys():
...     print(word)
...
Thorfinn
Askeladd
Thorkell
Leif
```

- **Iterar sobre valores**

```python
>>> for meaning in vinland_saga_characters.values():
...     print(word)
...
Guerrero en busca de paz
Astuto líder mercenario
Guerrero fuerte y audaz
Explorador formidable y audaz
```

- **Iterar sobre clave-valor**

```python
>>> for word, meaning in vinland_saga_characters.items():
...     print(f'{word} : {meaning}')
...
Thorfinn : Guerrero en busca de paz
Askeladd : Astuto líder mercenario
Thorkell : Guerrero fuerte y audaz
Leif : Explorador formidable y audaz
```