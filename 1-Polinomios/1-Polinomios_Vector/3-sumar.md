# Método Sumar

El siguiente método suma dos polinomios A y B y representa la suma de ellos en un nuevo polinomio C.

El método realiza las siguientes tareas:

1. Se determina cual de los dos polinomios a sumar tiene el mayor grado.
2. Se construye el polinomio C con un tamaño igual al mayor grado más dos posiciones.
3. Mientras hay datos en los dos polinomios se realizan las siguientes acciones:

- Si sus exponentes son iguales se inserta en el polinomio C la suma de los dos coeficientes y se avanza a la siguiente posición en los dos polinomios.

- Si el exponente del polinomio A es mayor al exponente del polinomio B se inserta en el polinomio C el coeficiente del polinomio B  y se avanza a la siguiente posición del polinomio A.

- Si el exponente del polinomio B es mayor al exponente del polinomio A se inserta en el polinomio C el coeficiente del polinomio B y se avanza a la siguiente posición del polinomio B.

## Implementación en Pseudocódigo

```js
metodo_sumar(Entero A[], Entero B[]){
    Entero k, j = 1
    Entero mayor, expA, expB, posC = 0
    
    Si (A[0] > B[0]) Entonces
        mayor = A[0]
      si_no
        mayor = B[0]
    Fin_si
    
    Entero C [mayor+2]
    
    C[0] = mayor

    Mientras ((k < A[0]+2) y (j< B[0]+2)) Haga

        expA = A[0] + 1 - k
        expB = B[0] + 1 - j
        
        Si ( expA == expB) Entonces
            posC = C[0] + 1 - expA
            C[posC] = A[k] + B[j]
            k++
            j++
          si_no 
            Si (expA > expB) Entonces
              posC = C[0] + 1 - expA
              C[posC] = A[k]
              k++
            si_no
              Si (expA < expB) Entonces
                posC = C[0] + 1 - expB
                C[posC] = B[j]
                j++
              Fin_si
            Fin_si
        Fin_si
    Fin_mientras
    ajustar(C)
Fin_método
```

## Implementación en Python
```python
def sumar(A, B):
    k = 1
    j = 1
    mayor = 0
    expA = 0
    expB = 0
    posC = 0
    
    # 1. Identificar el polinomio con mayor grado
    if A[0] > B[0]:
        mayor = A[0]
    else:
        mayor = B[0]
    
    # 2. Crear un nuevo vector donde se va a almacenar la suma del polinomio A y B
    C = [0] * (mayor + 2)
    C[0] = mayor

    while (k < A[0] + 2) and (j < B[0] + 2):
        # 3. Identificar el exponente de cada uno de los polinomios A y B
        expA = A[0] + 1 - k
        expB = B[0] + 1 - j
        
        # 4. Identificar los tres casos posibles (expA == expB) (expA > expB) (expA < expB)
        if expA == expB:
            posC = C[0] + 1 - expA
            C[posC] = A[k] + B[j]
            k += 1
            j += 1
        elif expA > expB:
            posC = C[0] + 1 - expA
            C[posC] = A[k]
            k += 1
        elif expA < expB:
            posC = C[0] + 1 - expB
            C[posC] = B[j]
            j += 1
    
    # 5. Ajustar el polinomio resultado
    ajustar(C)
    return C

# Ejemplo de uso
if __name__ == "__main__":
    # Ejemplo: (2x^3 + 4x^2 - 2x + 1) + (3x^2 + 5x - 3)
    A = [3, 2, 4, -2, 1]   # 2x^3 + 4x^2 - 2x + 1
    B = [2, 0, 3, 5, -3]   # 3x^2 + 5x - 3
    
    C = sumar(A, B)
    print("Polinomio A:", A)
    print("Polinomio B:", B)
    print("Resultado de la suma:", C)
```

### Aspectos claves:

1. En Python, la creación del vector C se realiza usando multiplicación de listas: `[0] * (mayor + 2)`
2. No es necesario declarar el tipo de las variables
3. La función retorna el vector C para mayor flexibilidad
4. Se incluye un ejemplo de uso con `if __name__ == "__main__":`
5. Los incrementos se escriben como `k += 1` en lugar de `k++`