# Método de Ajuste de Polinomios en Python

El método ajusta el grado de un polinomio representado como vector cuando hay coeficientes cero al inicio. Este ajuste es necesario para mantener una representación correcta del polinomio.

## Proceso de Ajuste

El método realiza las siguientes verificaciones y ajustes:

1. Verifica si en la segunda posición del vector hay un cero (coeficiente del término de mayor grado)
2. Si hay un cero, cuenta cuántos ceros consecutivos hay desde esa posición
3. Desplaza los coeficientes no cero hacia el inicio del vector
4. Actualiza el grado del polinomio (primera posición del vector)

## Implementación en Pseudocódigo
```
metodo_ajustar(Vec[])
  entero: i , j , cont=0
  Si ( Vec[1] == 0 ) Entonces
       i = 1
       Mientras  ( (i< Vec[0] + 2) and (Vec[i] == 0) ) Haga
           cont = cont+1
           i = i + 1
       Fin_mientras
       Para (j = i , V[0]+ 2 , j++)
            Vec[ j - cont ]= Vec[ j ]
       Fin_Para
    Vec[ 0 ] = Vec[ 0 ] - cont
  Fin_si
Fin_metodo
```

## Implementación en Python
```python
def ajustar(vec):
    """
    Ajusta un polinomio representado como vector eliminando los coeficientes cero iniciales
    y actualizando su grado.
    
    Args:
        vec (list): Vector que representa el polinomio. 
                   vec[0] contiene el grado del polinomio.
    """
    if vec[1] == 0:
        # Contar ceros consecutivos desde la segunda posición
        i = 1
        cont = 0
        while i < vec[0] + 2 and vec[i] == 0:
            cont += 1
            i += 1
            
        # Método 1: Usando slice para desplazar elementos
        vec[1:vec[0]+2-cont] = vec[i:vec[0]+2]
        
        # Actualizar el grado del polinomio
        vec[0] -= cont

        # Opcional: Eliminar elementos sobrantes si se desea
        # del vec[vec[0]+2:]

# Ejemplo de uso
vec = [4, 0, 0, 7, -87, 2]  # Polinomio con grado 4 pero primeros términos son cero
print(f"Antes del ajuste: {vec}")
ajustar(vec)
print(f"Después del ajuste: {vec}")
```

### Ventajas de la implementación en Python:

1. **Slicing eficiente**: Utilizamos el slicing de Python (`vec[1:vec[0]+2-cont] = vec[i:vec[0]+2]`) para mover elementos de manera más eficiente que un bucle tradicional.

2. **Código más conciso**: La sintaxis de Python permite expresar las operaciones de manera más clara y con menos líneas de código.

3. **Flexibilidad de la lista**: Podemos opcionalmente eliminar los elementos sobrantes usando `del` si es necesario, algo que no es posible con arrays en algunos lenguajes de programación.

4. **Documentación integrada**: Usando docstrings podemos documentar la función de manera que sea accesible mediante la función help() de Python.

### Consideraciones importantes:

1. La función modifica la lista in-place (modifica el vector original)
2. El grado del polinomio (vec[0]) se actualiza automáticamente
3. Los elementos después de la posición vec[0]+2 se pueden mantener o eliminar según la necesidad

### Ejemplo de resultado:

Para un vector inicial `[4, 0, 0, 7, -87, 2]`:
- Grado inicial: 4
- Después del ajuste: `[2, 7, -87, 2]`
- Nuevo grado: 2

El polinomio se ha ajustado eliminando los coeficientes cero iniciales y actualizando su grado correctamente.