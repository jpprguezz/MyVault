Para hacer resolver cualquier problema, normalmente lo que se suele hacer es ir paso por paso para resolver los problemas. De hecho al intentar esto, nos daremos cuenta de que muchos de los ejercicios/problemas que se nos planten delante, siguen una esquemática que en muchos de los casos, se repite. A eso los podemos llamar algoritmos. Por ello en este archivo colocaré los algoritmos más comunes presentes en las listas de Python:


#### Para búsqueda

- **Búsqueda lineal:** Para comparar el índice de cada elemento de la lista, con el elemento objetivo.
```python
def busqueda_lineal(lista, objetivo):
    for i in range(len(lista)):
        if lista[i] == objetivo:
            return i
```

#### Para ordenamiento

- **Ordenamiento por selección:** Este algoritmo lo que hace es buscar el elemento más pequeño de la lista y lo coloca en la posición correcta. Este proceso lo hace con todos los elementos hasta que la lista esta ordenada.

```python
def ordenación_selección(lista):
    n = len(lista)
    for i in range(n):
        min_index = i  # para encontrar el elemento más pequeño
        for j in range(i + 1, n):
            if lista[j] < lista[min_index]: # Dependiendo de si queremos encontrar el mayor o menos, cambiamos el simbolo
                min_index = j
        temp = lista[i]
        lista[i] = lista[min_index]  # En estas tres ultimas lineas, se intercambia el elemento más pequeño por el de la posición "i" usando la variable temp
        lista[min_index] = temp
    return lista
        
```

#### Filtrar por elementos

- **Filtrar elementos**: Para crear una lista con elementos y condiciones específicas.

```python
def filtrar_pares(lista):
    return [x for x in lista if x % 2 == 0] # Devuelva una lista con los elementos pares de la lista dada anteriormente
```

#### Rotar una lista

- **Rotar una lista**: para rotar los elementos de una lista moviendo un número especifico de elementos.

```python
def ordenación_selección(lista: list, n: int) -> list:
    return lista[n:] + lista[:n]
```

#### Eliminar duplicados

- **Eliminar duplicados**: Para eliminar elementos duplicados en listas:

```python
def eliminar_duplicados(nums):
    resultado = []
    for num in nums:
        if num not in resultado:
            resultado.append(num)
    return resultado
```

#### Fusionar listas

- **Fusionar listas:** El simple hecho de combinar una o más listas (en este caso, sin repetidos)

```python
def fusionar_y_eliminar_duplicados(lista, lista2, lista3):
    resultado = []
    for elemento in lista + lista2 + lista3:
        if elemento not in resultado:
            resultado.append(elemento)
    return resultado
```

#### Encontrar mínimo/máximo (sin usar min() o max())

- **Encontrar mínimo/máximo:** Comparando cada valor con un valor actual para pillar el mínimo o máximo. para calcular el mínimo usamos el < y para el máximo el >.

```python
def encontrar_mínimo(lista):
    minimo = lista[0]
    for num in lista:
        if num < minimo:
            minimo = num
    return minimo
```


#### Aplanar listas

- **Aplanar listas:** Forma general para aplanar listas, da igual los niveles de anidamiento o los tipos de los elementos que hayan.
```python
def aplanar_lista(lista):
    # Lista donde se almacenará el resultado
    lista_aplanada = []
    # Iterar sobre los elementos de la lista
    for elemento in lista:
        # Si el elemento es una lista, se extiende
        if isinstance(elemento, list):
            lista_aplanada.extend(elemento)
        else:
            # Si no es una lista, se agrega directamente
            lista_aplanada.append(elemento)
    return lista_aplanada
```


#### Comprobar si el elemento de al lado es igual

- **Comprobar si el elemento de al lado es igual:** Se recorre la lista y se añade un elemento a la nueva lista solo si es diferente del último añadido.

```python      
    resultado = [lista[0]]  # Inicializa con el primer elemento
    for elemento in lista[1:]:  # Itera desde el segundo elemento
        if elemento != resultado[-1]:  # Compara con el último añadido
            resultado.append(elemento)
    return resultado
```


#### Calcular la suma de los valores de una diagonal de una matriz

- **Calcular la suma de los valores de una diagonal de una matriz:**

```python
def run(matrix: list) -> int | None:
    sum_diagonal = None    
    for row in matrix:  # Se recorre la diagonal de la matriz
        if len(row) == len(matrix):  # Si la longitud de la matriz es igual a la de la fila:
            sum_diagonal = 0  # Se iguala a 0 la variable para sumar a ella los valores de la diagonal 
            for num in range(len(matrix)):
                sum_diagonal += matrix[num][num]  # Se accede al elementos en la posición especificada (que pertenece a la siagonal)

    return sum_diagonal
```


#### Pasar un decimal a binario, sin usar bin():

- **Pasar un decimal a binario, sin usar bin():**

```python
def run(n: int) -> str:
    if n == 0:  # Si el número ya de por si es 0
        bin_repr = "0" # Se coloca como resultado 0
    else:  # Si no
        bin_repr = []  # Se crea una lista vacía para guardar los valores que se van calculando
        while n > 0:  # Se crea un bucle para ir haciendo los calculos
            bin_repr.append(str(n % 2))  # Se agrega el resto de dividir entre 2 el número
            n //= 2  # Y se divide el número acto seguido para pasar al siguiente número
        bin_repr.reverse()  # Se revierte la lista, porque el número se estaba generando al reves
        bin_repr = "".join(bin_repr)  # Y se une toda la lista de números
```


#### Encontrar el primer elemento (número) no consecutivo

- **Encontrar el primer elemento (número) no consecutivo**:

```python
def run(values: list) -> int:
    if not values: # Si todos los valroes son consecutivos 
        target = None
    else: # Si no ejecuta el codigo de abajo
        first_num = values[0] # Primer número de la lsita para comparar
        target = None # Hacemos hipotesis de la variable
        for num in values: # Recorremos la lista
            if num != first_num: # Si el numero es diferente al primero
                target = num # Target es ese número(el no consecutivo)
                break # Y paramos de revisar
            else:
                first_num += 1 # Si no, pasamos de número, sumando 1 al contador
```


#### Recrear el como funciona un reloj

- **Recrear el como funciona un reloj:** Dada una hora en formato HH:MM (como cadena de texto) y una cantidad de minutos (como valor entero), calcula la hora resultante (en formato HH:MM) si sumamos los minutos a la hora de entrada.

```python
def run(time: str, offset: int) -> str:
    time = time.split(':')
    h_offset = offset // 60 
    min_offset = offset % 60

    hours = h_offset + int(time[0])
    mins = min_offset + int(time[1])

    if mins > 60:
        hours += mins // 60
        mins -= 60
    if hours > 24:
        hours -= 24

    final_time = f'{hours}:{mins}'
```

#### Subconjuntos en cascada

- 
```python
def run(values: list, size: int) -> list:
    # Inicializamos una lista vacía para almacenar los subconjuntos generados
    cascading = []

    # Validar que el tamaño de los subconjuntos sea válido
    # Si 'size' es mayor que la longitud de 'values' o es menor o igual a 0, devolvemos una lista vacía
    if size > len(values) or size <= 0:
        return []

    # Iteramos desde el índice 0 hasta (len(values) - size), inclusivo
    # Esto asegura que solo se generen subconjuntos válidos de tamaño 'size'
    for value in range(len(values) - size + 1):
        # Extraemos un subconjunto desde el índice actual ('value') hasta 'value + size'
        subset = values[value:value + size]
        # Añadimos el subconjunto generado a la lista 'cascading'
        cascading.append(subset)

    # Devolvemos la lista con todos los subconjuntos generados
    return cascading

```


#### Mezcla ordenada

- **Mezcla ordenada**: Como datos de entrada se dispone de dos listas con valores num´ ericos que ya vienen ordenados. Obtenga una lista de salida con la mezcla de las dos listas de entrada (manteniendo el orden de los valores).

```python
# Combina ambas listas en una sola
all_values = values1 + values2

# Crea una nueva lista que inicialmente copia todos los elementos de 'all_values'
merged = [num for num in all_values]

# Recorre los elementos en 'merged' para eliminar duplicados
for value in merged:
    if merged.count(value) > 1:  # Si el elemento aparece más de una vez
        merged.remove(value)  # Elimina uno de ellos

# Ordena manualmente la lista 'merged' usando el algoritmo de selección
for index in range(len(merged) - 1):
    min_index = index  # Suponemos que el elemento actual es el menor
    for index_2 in range(index + 1, len(merged)):  # Comparamos con el resto
        if merged[min_index] > merged[index_2]:  # Si encontramos un elemento menor
            min_index = index_2  # Actualizamos el índice del menor
    # Intercambiamos el elemento actual con el menor encontrado
    temp_value = merged[index]
    merged[index] = merged[min_index]
    merged[min_index] = temp_value
```

<<<<<<< HEAD

## Ejemplos útiles y sencillos de listas por comprensión

### Convertir una lista a entero:

```python
lista_int = [int(v) for v in lista_str]
```

### Maximo o mínimo (ejercicio *minmax*):
```python
max_v = [v for v in num <= target]
min_v = [v for v in num > target]
```
aquí es importante fijarse en el *max_v* y poner ```<=``` para que incluya el valor máximo

### Convertir una lista de cuadrados:

```python
cuadrados = [x**2 for x in range(1, 11)]
```

### Filtrar números pares:
```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
pares = [x for x in numeros if x % 2 == 0]
```

### Crear una lista de pares ordenados:

```python
pares_ordenados = [(i, j) for i in [1, 2, 3] for j in [4, 5, 6]]
```

### aplanar listas:

```python
listas_anidadas = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
lista_aplanada = [elemento for sublista in listas_anidadas for elemento in sublista]
```

### Palabras que empiezan por una letra:

```python
palabras = ["apple", "banana", "cherry", "avocado", "grape"]
empiezan_con_a = [palabra for palabra in palabras if palabra.startswith('a')]
```

### Devolver una lista con la longitud de las palabras:

```python
palabras = ["apple", "banana", "cherry", "date"]
longitudes = [len(palabra) for palabra in palabras]
```


### Crear una lista de números negativos:

Dada una lista solo devolver los negativos
```python
numeros = [1, -2, 3, -4, 5, -6]
negativos = [x for x in numeros if x < 0]
```
=======
#### Cualificando números.

- Dado un número entero positivo, separa las cifras de millares por comas (como string).

```python
def run(number: int) -> str:
    result = ''
    n_str = str(number)
    n_str = n_str[::-1]  # Revertimos el numero ya convertido a str
    i = 0  # Este 0 equivale al inicio de el index que usaremos para colocar las comas en el numero
    while i < len(n_str):  # Si el número es menos que el largo del string, funciona este while
        if (i % 3 == 0 and i != 0):  # Si es divisible entre 3 (es decir, la cantidad de caracteres por los que colocaremos una coma) e i es disitinto a 0 (para que no haga conflicto con el inicio del index)
            result += ','  # Añadimos una coma al string
        result += n_str[i]  # Aqui se añade el siguiente numero
        i += 1 # Se suma 1 punto en el contador
    qnumber = result[::-1]  # Se vuelve a revertir la lista

    return qnumber
```

#### Range flotante

-  **Range flotante:** Escribe un programa Python que simule el comportamiento de la función “built-in” range() pero utilizando valores flotantes.

```python
def run(start: float, stop: float, step: float) -> list:
    values = []  # Lista para guardar los numeros del range
    while start < stop:  # Si el inicio es menor que el final (que siempre lo será hasta que llegue al número más cercano al final)
        values.append(start)  # Añade el numero del inicio
        start += step  # Añade un paso a star para que se vayan sumando hasta llegar al numero final
    return values

```


#### Ver primer número duplicado

- **Ver primer número duplicado**:
```python
def run(items: list) -> int | None:
    seen_items = []
    fdup = None
    for item in items:
        if item in seen_items:
            fdup = item
            break
        else:
            seen_items.append(item)
```
>>>>>>> origin/main
