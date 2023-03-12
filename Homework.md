# 1. Considere el siguiente areglo que contiene la altura de un grupo de estudiantes de Henry y cálcule:

```python
muestra = np.array( [[1.85, 1.8, 1.8 , 1.8],
                    [1.73,  1.7, 1.75, 1.76],
                    [ 1.65, 1.69,  1.67 ,  1.6],
                    [1.54,  1.57, 1.58, 1.59],
                    [ 1.4 , 1.42,  1.45, 1.48]]) 
```
- Media.
- Mediana.
- Moda
- Varianza
- Desvío estándar.

## Solucion

- [ ] Instalar numpy, scipy, pandas y matplotlib con **"pip install (libreria)"** en VSC
- [ ] Importar lo instalado
```python
import numpy as np # importando numpy
from scipy import stats # importando scipy.stats
import pandas as pd #importando pandas
import matplotlib.pyplot as plt # importando matplotlib
```
####   * Calculo de ma meda aritmetica
```python
muestra = np.array( [[1.85, 1.8, 1.8 , 1.8],
                    [1.73,  1.7, 1.75, 1.76],
                    [ 1.65, 1.69,  1.67 ,  1.6],
                    [1.54,  1.57, 1.58, 1.59],
                    [ 1.4 , 1.42,  1.45, 1.48]])

```

El comando **shape** de la librería Numpy, el cual **nos muestra las dimensiones de un array**. Nos es útil para ver cómo funcionan diferentes comandos que se aplican a arreglos. Para poder usar el comando Shape, primero necesitamos importar la librería de Numpy en Python. Tiene solamente un parámetro y esta es su sintaxis.
**np.shape( arreglo )**
Dónde:
-   Np, hace referencia a la librería Numpy.
-   Arreglo, es el array del que queremos conocer sus dimensiones.
**Resultado**: el resultado es un arreglo que indica el número de filas y el número de columnas **(filas, columnas)**.

```python
muestra.shape
```
R. (5,4)

Cuando trabaje con arreglos Numpy, a menudo querrá remodelar un arreglo existente en un arreglo de diferentes dimensiones. Esto puede ser particularmente útil cuando transforma datos en varios pasos.

y numpy `reshape()` te ayuda a hacerlo fácilmente. En los próximos minutos, aprenderá la sintaxis para usar `reshape()`, y también reformar matrices a diferentes dimensiones.

```python
nueva_muestra = muestra reshape(20, )
```

```python
nueva_muestra

array([1.85, 1.8 , 1.8 , 1.8 , 1.73, 1.7 , 1.75, 1.76, 1.65, 1.69, 1.67, 1.6 , 1.54, 1.57, 1.58, 1.59, 1.4 , 1.42, 1.45, 1.48])
```
R. array([1.85, 1.8 , 1.8 , 1.8 , 1.73, 1.7 , 1.75, 1.76, 1.65, 1.69, 1.67, 1.6 , 1.54, 1.57, 1.58, 1.59, 1.4 , 1.42, 1.45, 1.48])

- [ ] Para sacar la media aritmetica se debe sumar todos los elementos y dividir entre la cantidad de elementos para ello se realiza el siguiente codigo:
```python
def media(lista):
	suma = 0
	conteo = 0
	for i in lista:
		suma += i
		conteo += 1
	media = suma/conteo
return media

```

otra forma de determinar la media es:

```python
nueva_muestra.mean()
```
R = 1.6415

tambien

```python
media(nueva_muestra)
```
R = 1.6415

#### * Determinar la MEDIANA
- [ ] Determinar la mediana, el siguiente codigo nos ayuda a determinarlo.
```python
def mediana(lista):
	ordenado = np.sort(lista)
	if len(lista) % 2 == 0:
		posicion = int(len(ordenado)/2)
		mediana = (ordenado[posicion - 1] + ordenado[posicion]) / 2
	return mediana
else:
	posicion = int(len(ordenado)/2) + 1
```

otra forma de determinar la mediana:
```python
np.median(nueva_muestra)
```
R. 1.66


```python
mediana(nueva_muestra)
```
R. 1.66

#### * Determinar LA MODA
- [ ] Determinar la moda, el siguiente codigo nos ayuda a determinarlomediana(nueva_muestra) 
```python
def moda(lista):
	elemento = 0
	max_repetido = 0
	for i in lista:
		cantidad = 0
		for j in lista:
			if j == i:
				cantidad += 1
	if max_repetido < cantidad:
		max_repetido = cantidad
		elemento = i
	return elemento
```


```python
moda(nueva_muestra)
```
R. 1.8

Para determinar la moda se debe importar statistics si no se tiene instalar con pip install statistic
```python
import statistics as stat
```

```python
stat.mode(nueva_muestra)
```
R. 1.8

#### * Determinar LA VARIANZA

- [ ] Determinar la varianza, el siguiente codigo nos ayuda a determinarlomediana(nueva_muestra) 

```python
def varianza(lista):
	suma = 0
	media_lista = media(lista)
	for i in lista:
		suma += (i - media_lista)**2
	varia = suma/len(lista)
return varia
```


```python
varianza(nueva_muestra)
```
R. 0.017642750000000006

```python
np.var(nueva_muestra)
```
R. 0.017642750000000006

#### * Determinar LA DESVIACION STANDAR

- [ ]  Determinar la desviacion standar se determina con el siguiente codigo:

```python
np.sqrt(varianza(nueva_muestra))
```
R. 0.13282601401833907

tambien se puede determinar con :
```python
nueva_muestra.std()
```
R.  0.13282601401833907


# 2. Convierta el arreglo en una lista y realice un Histograma de 5 intervalos. ¿Tiene distribución normal?.

### Solución

Primero importar matplotlib si no se tiene, instalar con ** pip install matplotlib**

```python
import matplotlib.pyplot as plt
```


```python
plt.hist(nueva_muestra, bins = 5)
plt.grid()
plt.show()
```

R.
![[Pasted image 20230312082046.png]]

==**NO tiene una distribuicion normal**==


# 3. Utilizando pandas describa el dataframe.

### Solucion
 - [ ]  Importar pandas y con ello se realizara el dataframe.

```python
import pandas as pd
```

```python
df = pd.DataFrame(nueva_muestra)
```

```python
df.describe()
```
R.   
| Parametro | valor     |
| ----- | --------- |
| count | 20.000000 |
| mean  | 1.641500  |
| std   | 0.136277  |
| min   | 1.400000  |
| 25%   | 1.562500  |
| 50%   | 1.660000  |
| 75%   | 1.752500  |
| max   | 1.850000  |


# 4. Con los siguientes datos construye un df y un array que permitan describir adecuadamente la muestra.

'Ingreso en miles' : 10.5	6.8	20.7	18.2	8.6	25.8	22.2	5.9	7.6	11.8 
'Años de estudio': 17	18	21	16	16	21	16	14	18	18 

### Solucion
- [ ] Primero crearemos un dicccionario con los datos que nos dan

```python
diccionario = {'Ingreso en miles' : [10.5, 6.8, 20.7, 18.2, 8.6, 25.8, 22.2, 5.9, 7.6, 11.8],
			'Años de estudio': [17, 18, 21, 16, 16, 21, 16, 14, 18, 18]}
```

El diccionario anterior lo convertimos a un dataframe 
```python
df1 = pd.DataFrame(diccionario)
```

```python
df1
```
R
| Ord | Ingreso en miles | Años de estudio |
| --- | ---------------- | --------------- |
| 0   | 10.5             | 17              |
| 1   | 6.8              | 18              |
| 2   | 20.7             | 21              |
| 3   | 18.2             | 16              |
| 4   | 8.6              | 16              |
| 5   | 25.8             | 21              |
| 6   | 22.2             | 16              |
| 7   | 5.9              | 14              |
| 8   | 7.6              | 18              |
| 9   | 11.8             | 18              |


# 5. Realice un histograma para de 6 secciones para 'Ingreso en miles' y 'Años de estudio'.

### Solucion

```python
plt.hist(df1["Ingreso en miles"], bins = 6)
plt.grid()
plt.show()
```
R.
![[Pasted image 20230312084334.png]]

```python
plt.hist(df1["Años de estudio"], bins = 6)
plt.grid()
plt.show()
```
R.
![[Pasted image 20230312084438.png]]



# 6. Cálcula la media de 'Ingreso en miles' (df) utilizando pandas.

### Solución

```python
df1["Ingreso en miles"].mean()
```
R. 13.809999999999999



# 7. Cálcula la media de 'Ingreso en miles' (array) utilizando numpy.

### Solución
```python
np.mean(df1["Ingreso en miles"])
```
R. 13.809999999999999

# 8. Agregue los siguientes valores extremos al df [ 50, 35 ], [ 120, 30 ]. ¿En cuanto vario la media?, ¿Qué conclusiones obtiene de este resultado sobre la media?.

### Solución

primero creamos una copia del dataframe

```python
df2 = df1.copy()
```


Agregamos los valores indicados
primero se define los campos de ingreso
```python
nuevos_elementos = {"Ingreso en miles": 50, "Años de estudio":35}
nuevos_elementos1 = {"Ingreso en miles": 120 , "Años de estudio":30}
```

Se agrega los datos al DF2
```python
df2 = df2.append(nuevos_elementos, ignore_index=True)
df2 = df2.append(nuevos_elementos1, ignore_index=True)
```

Resultado
```python
df2
```
R.
| Ord | Ingreso en miles | Años de estudio |
| --- | ---------------- | --------------- |
| 0   | 10.5             | 17              |
| 1   | 6.8              | 18              |
| 2   | 20.7             | 21              |
| 3   | 18.2             | 16              |
| 4   | 8.6              | 16              |
| 5   | 25.8             | 21              |
| 6   | 22.2             | 16              |
| 7   | 5.9              | 14              |
| 8   | 7.6              | 18              |
| 9   | 11.8             | 18              |
| 10  | 50               | 35              |
| 11  | 120              | 30              |



