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