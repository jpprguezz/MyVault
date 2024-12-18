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

- **Aplanar listas:** 
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