# Método Mostrar

Partiendo de un vector dado
```python
vec = [4, -12, 0, 7, -87, 2]
```

El método verifica si el vector en la posición dada es diferente de cero, **para no mostrar aquellos valores que tengan coeficiente CERO**, luego verifica si el coeficiente que se encuentra en la posición **k** es mayor a cero, si es mayor concatena con signo positivo (`+`) de lo contrario concatena con signo negativo (`-`)

## Implementación en Pseudocódigo
```
método mostrar( Entero vec[] )
  Cadena polinomio
  Entero k 
  Entero exp = 0
  Para( k=1; k < vec[0]+2 ); k++) 
    Si(vec[k] != 0)
      Si(vec[k]>0)
        polinomio = polinomio + " + " + vec[k] + "X^" + exp
      si_no
        polinomio = polinomio + " - " + ( vec[k] * (-1) ) + "X^" + exp;
      Fin_si
    Fin_si
  Fin_para
  imprima(polinomio)
Fin_método
```

## Implementación en Python
```python
def mostrar(vec):
    polinomio = ""
    k = 0
    exp = 0
    
    for k in range(1, vec[0] + 2):
        # Aplicar fórmula para encontrar el exponente
        exp = vec[0] + 1 - k
        
        if vec[k] != 0:
            if vec[k] > 0:
                polinomio = polinomio + " + " + str(vec[k]) + "X^" + str(exp)
            else:
                polinomio = polinomio + " - " + str(abs(vec[k])) + "X^" + str(exp)
    
    print(polinomio)

# Ejemplo de uso
vec = [4, -12, 0, 7, -87, 2]
mostrar(vec)
```