
# PANDAS

_autor: Robert Moreno Carrillo_ 

Pandas es una librería de Python utilizada el manejo y análisis de grandes cantidades de datos organizados, ofrece una gran facilidad en el trabajo con hojas de cálculos y esta se maneja mediante DataFrames y Series.


```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
```

### De diccionario a DataFrame

Es posible convertir a un diccionario del tipo {"clave1" : [v1,v2,..,vn] , "clave2" : [z1,z2,..,zn]... } usando pd.DataFrame()


```python
diccionario={"Nombre":["Robert", "Denisse", "Carlos"], "Edad":[20,20,19]}
DataF=pd.DataFrame(diccionario)
DataF
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Edad</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Robert</td>
      <td>20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Denisse</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Carlos</td>
      <td>19</td>
    </tr>
  </tbody>
</table>
</div>



Es posible anadir una columna de la misma forma que un diccionario nombreDataframe["nombreColumnaNueva"]=ListaDeValores


```python
DataF["Semestre"]=[4,3,3]
DataF
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Edad</th>
      <th>Semestre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Robert</td>
      <td>20</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Denisse</td>
      <td>20</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Carlos</td>
      <td>19</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



Para seleccionar varias columnas del dataFrame se lo puede hacer mediante una lista del nombre de las columnas
nombreDataframe[[nomColumna1, nomColumna2,...]]


```python
DataF[["Nombre", "Semestre"]] # Solo selecciono la columna Nombre y Semestre
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Semestre</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Robert</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Denisse</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Carlos</td>
      <td>3</td>
    </tr>
  </tbody>
</table>
</div>



Es posible eliminar una columan utilizando del 


```python
#del DataF["Semestre"]
```


```python
DataF
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Nombre</th>
      <th>Edad</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Robert</td>
      <td>20</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Denisse</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Carlos</td>
      <td>19</td>
    </tr>
  </tbody>
</table>
</div>



### Leer archivo csv con pandas:
Por defecto se utiliza de separador la coma, pero en caso de tener otro separador utilizamos el parámetro "sep"
Ejemplo:
DF=pd.read_csv("nombre_de_archivo.csv", sep=";") 



```python
servings= pd.read_csv("bebidas.csv", sep=",") 
```

La funcion head(n) retorna las n primeras filas del DataFrame, y tail(n) retorna las n ultimas filas, por defecto n es 5


```python
servings.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>AS</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>89</td>
      <td>132</td>
      <td>54</td>
      <td>4.9</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>25</td>
      <td>0</td>
      <td>14</td>
      <td>0.7</td>
      <td>AF</td>
    </tr>
  </tbody>
</table>
</div>



### Datos Estadísticos:

Es posible obtener una serie de datos estadisticos de una columna mediante .describe(), incluye cantidad, promedio, desviacion estandar, min, max y cuartiles


```python
servings["beer_servings"].describe()
```




    count    193.000000
    mean     106.160622
    std      101.143103
    min        0.000000
    25%       20.000000
    50%       76.000000
    75%      188.000000
    max      376.000000
    Name: beer_servings, dtype: float64



 También es posible obtener estas medidas individualmente por ejemplo .max(), .mean() , .std()


```python
servings["beer_servings"].mean()
```




    106.16062176165804



### Es posible hacer filtrado de filas mediante condiciones al igual que en numpy:


```python
condicion1 = servings["continent"]=="EU" #voy a filtrar los registros solo del continente Europeo
servings[condicion1].head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>89</td>
      <td>132</td>
      <td>54</td>
      <td>4.9</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>245</td>
      <td>138</td>
      <td>312</td>
      <td>12.4</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Armenia</td>
      <td>21</td>
      <td>179</td>
      <td>11</td>
      <td>3.8</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Austria</td>
      <td>279</td>
      <td>75</td>
      <td>191</td>
      <td>9.7</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Azerbaijan</td>
      <td>21</td>
      <td>46</td>
      <td>5</td>
      <td>1.3</td>
      <td>EU</td>
    </tr>
  </tbody>
</table>
</div>




```python
condicion2 = servings["beer_servings"]> servings["beer_servings"].mean() #filtra que se presenten valores mayores al promedio en beer_servings
servings[condicion1 & condicion2].head() #es posible aplicar más de una condiciones mendiante el operador "&" como and y "|" como or
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>245</td>
      <td>138</td>
      <td>312</td>
      <td>12.4</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Austria</td>
      <td>279</td>
      <td>75</td>
      <td>191</td>
      <td>9.7</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Belarus</td>
      <td>142</td>
      <td>373</td>
      <td>42</td>
      <td>14.4</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Belgium</td>
      <td>295</td>
      <td>84</td>
      <td>212</td>
      <td>10.5</td>
      <td>EU</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Bulgaria</td>
      <td>231</td>
      <td>252</td>
      <td>94</td>
      <td>10.3</td>
      <td>EU</td>
    </tr>
  </tbody>
</table>
</div>



Tambien es posible hace operaciones con las filas (sumar, multiplicar, dividir, entre otras..) aplicandolas a las columas directamente

### Groupby:
Funciona para agrupar y trabajar con una seccion específica una funcion en específico(sum, max, min, mean)


```python
servings.groupby("continent").mean() #promedio
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AF</th>
      <td>61.471698</td>
      <td>16.339623</td>
      <td>16.264151</td>
      <td>3.007547</td>
    </tr>
    <tr>
      <th>AS</th>
      <td>37.045455</td>
      <td>60.840909</td>
      <td>9.068182</td>
      <td>2.170455</td>
    </tr>
    <tr>
      <th>EU</th>
      <td>193.777778</td>
      <td>132.555556</td>
      <td>142.222222</td>
      <td>8.617778</td>
    </tr>
    <tr>
      <th>OC</th>
      <td>89.687500</td>
      <td>58.437500</td>
      <td>35.625000</td>
      <td>3.381250</td>
    </tr>
    <tr>
      <th>SA</th>
      <td>175.083333</td>
      <td>114.750000</td>
      <td>62.416667</td>
      <td>6.308333</td>
    </tr>
  </tbody>
</table>
</div>




```python
servings.groupby("continent").sum() #suma
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
    </tr>
    <tr>
      <th>continent</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>AF</th>
      <td>3258</td>
      <td>866</td>
      <td>862</td>
      <td>159.4</td>
    </tr>
    <tr>
      <th>AS</th>
      <td>1630</td>
      <td>2677</td>
      <td>399</td>
      <td>95.5</td>
    </tr>
    <tr>
      <th>EU</th>
      <td>8720</td>
      <td>5965</td>
      <td>6400</td>
      <td>387.8</td>
    </tr>
    <tr>
      <th>OC</th>
      <td>1435</td>
      <td>935</td>
      <td>570</td>
      <td>54.1</td>
    </tr>
    <tr>
      <th>SA</th>
      <td>2101</td>
      <td>1377</td>
      <td>749</td>
      <td>75.7</td>
    </tr>
  </tbody>
</table>
</div>



### Agregar nueva columna:
Simplemente se asigna a un nuevo nombre de columna una serie.



```python
servings["wine_beer"]= servings["wine_servings"] + servings["beer_servings"]
prom=servings["spirit_servings"].mean()
servings["spirit_promedio"]=(servings["spirit_servings"]/prom)
servings.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
      <th>wine_beer</th>
      <th>spirit_promedio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Afghanistan</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0.0</td>
      <td>AS</td>
      <td>0</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Albania</td>
      <td>89</td>
      <td>132</td>
      <td>54</td>
      <td>4.9</td>
      <td>EU</td>
      <td>143</td>
      <td>1.629734</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Algeria</td>
      <td>25</td>
      <td>0</td>
      <td>14</td>
      <td>0.7</td>
      <td>AF</td>
      <td>39</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Andorra</td>
      <td>245</td>
      <td>138</td>
      <td>312</td>
      <td>12.4</td>
      <td>EU</td>
      <td>557</td>
      <td>1.703813</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Angola</td>
      <td>217</td>
      <td>57</td>
      <td>45</td>
      <td>5.9</td>
      <td>AF</td>
      <td>262</td>
      <td>0.703749</td>
    </tr>
  </tbody>
</table>
</div>



# ILOC:
Utilizado para indexacion/seleccion basada en la ubicacion de numeros enteros por posicion:
sintaxis: data.iloc(seleccion_de_filas,seleccion_de_columnas)



```python
#servings.iloc[0:45,[1,2,5]] filas del 0 al 44, y columnas 1 2 y 5
```

# Concatener Datos:

pd.concat([df1,df2,df3,df4,...,dfn])



```python
df1=servings["country"][:10]
df1.head()
```




    0    Afghanistan
    1        Albania
    2        Algeria
    3        Andorra
    4         Angola
    Name: country, dtype: object




```python
df2=servings["country"][10:30]
df2.head()
```




    10    Azerbaijan
    11       Bahamas
    12       Bahrain
    13    Bangladesh
    14      Barbados
    Name: country, dtype: object




```python
df3=servings["country"][30:70]
df3.tail()
```




    65      Germany
    66        Ghana
    67       Greece
    68      Grenada
    69    Guatemala
    Name: country, dtype: object




```python
#pd.concat([df1,df2,df3]) #se concatena uno debajo de otro
```

# Ordenar Datos:


```python
Sorted= servings.sort_values(["beer_servings"], ascending=False)
#Por defecto asciende de menor a mayor
Sorted.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>country</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
      <th>wine_beer</th>
      <th>spirit_promedio</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>117</th>
      <td>Namibia</td>
      <td>376</td>
      <td>3</td>
      <td>1</td>
      <td>6.8</td>
      <td>AF</td>
      <td>377</td>
      <td>0.037039</td>
    </tr>
    <tr>
      <th>45</th>
      <td>Czech Republic</td>
      <td>361</td>
      <td>170</td>
      <td>134</td>
      <td>11.8</td>
      <td>EU</td>
      <td>495</td>
      <td>2.098900</td>
    </tr>
    <tr>
      <th>62</th>
      <td>Gabon</td>
      <td>347</td>
      <td>98</td>
      <td>59</td>
      <td>8.9</td>
      <td>AF</td>
      <td>406</td>
      <td>1.209954</td>
    </tr>
    <tr>
      <th>65</th>
      <td>Germany</td>
      <td>346</td>
      <td>117</td>
      <td>175</td>
      <td>11.3</td>
      <td>EU</td>
      <td>521</td>
      <td>1.444537</td>
    </tr>
    <tr>
      <th>98</th>
      <td>Lithuania</td>
      <td>343</td>
      <td>244</td>
      <td>56</td>
      <td>12.9</td>
      <td>EU</td>
      <td>399</td>
      <td>3.012538</td>
    </tr>
  </tbody>
</table>
</div>




```python
servings=servings.reset_index()
servings.set_index("country").loc[["Germany","Spain"]] #cambiamos el indice de numeros a paises
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>level_0</th>
      <th>index</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
      <th>continent</th>
      <th>wine_beer</th>
      <th>spirit_promedio</th>
    </tr>
    <tr>
      <th>country</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Germany</th>
      <td>65</td>
      <td>65</td>
      <td>346</td>
      <td>117</td>
      <td>175</td>
      <td>11.3</td>
      <td>EU</td>
      <td>521</td>
      <td>1.444537</td>
    </tr>
    <tr>
      <th>Spain</th>
      <td>160</td>
      <td>160</td>
      <td>284</td>
      <td>157</td>
      <td>112</td>
      <td>10.0</td>
      <td>EU</td>
      <td>396</td>
      <td>1.938396</td>
    </tr>
  </tbody>
</table>
</div>




```python
servings.set_index("country").loc[["Germany","Spain"], ["beer_servings","wine_servings"]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>beer_servings</th>
      <th>wine_servings</th>
    </tr>
    <tr>
      <th>country</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Germany</th>
      <td>346</td>
      <td>175</td>
    </tr>
    <tr>
      <th>Spain</th>
      <td>284</td>
      <td>112</td>
    </tr>
  </tbody>
</table>
</div>



# GRAFICAS:



```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt
df=servings.groupby("continent").mean().reset_index()
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>continent</th>
      <th>beer_servings</th>
      <th>spirit_servings</th>
      <th>wine_servings</th>
      <th>total_litres_of_pure_alcohol</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>AF</td>
      <td>61.471698</td>
      <td>16.339623</td>
      <td>16.264151</td>
      <td>3.007547</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AS</td>
      <td>37.045455</td>
      <td>60.840909</td>
      <td>9.068182</td>
      <td>2.170455</td>
    </tr>
    <tr>
      <th>2</th>
      <td>EU</td>
      <td>193.777778</td>
      <td>132.555556</td>
      <td>142.222222</td>
      <td>8.617778</td>
    </tr>
    <tr>
      <th>3</th>
      <td>OC</td>
      <td>89.687500</td>
      <td>58.437500</td>
      <td>35.625000</td>
      <td>3.381250</td>
    </tr>
    <tr>
      <th>4</th>
      <td>SA</td>
      <td>175.083333</td>
      <td>114.750000</td>
      <td>62.416667</td>
      <td>6.308333</td>
    </tr>
  </tbody>
</table>
</div>



## Graficación en Seaborn 

## Boxplot:


```python
a4_dims = (12,7) #dimensiones del grafico
fig, ax = plt.subplots(figsize=a4_dims)
plt.suptitle('Titulo',size=25) 

sns.boxplot(x="continent", y="wine_servings", data=servings, palette="Set2") # Linea IMPORTANTE
# x: valores del eje x (nombre de la columna)
# y: valores del eje y (nombre de la columna)
# data: en este caso el nombre del dataframe
# palette: se puede omitir, maneja simplemente los colores, pueden encontrar más palette en la página oficial de seaborn 

plt.xlabel("NOMBRE PARA EL EJE X", size=12) # le da nombre al eje x
plt.ylabel("NOMBRE PARA EL EJE Y", size=12) # le da nombre al eje y
#plt.savefig("archivo.png")   # Guardar en formato .png
#plt.savefig("archivo.pdf")   # Guardar en formato .pdf

#plt.show()  #Si se trabaja en pycharm es necesario colocar esta linea para visualizar la grafica
```




    Text(0,0.5,'NOMBRE PARA EL EJE Y')




![png](output_47_1.png)


## Barplot:


```python
a4_dims = (12,7) #dimensiones del grafico
fig, ax = plt.subplots(figsize=a4_dims)
plt.suptitle('Titulo',size=25) 

sns.barplot(x="continent", y="beer_servings", data=df)
plt.xlabel("NOMBRE PARA EL EJE X", size=12) # le da nombre al eje x
plt.ylabel("NOMBRE PARA EL EJE Y", size=12) # le da nombre al eje y
```




    Text(0,0.5,'NOMBRE PARA EL EJE Y')




![png](output_49_1.png)


## Lineplot:


```python
sns.lineplot(x="continent", y="wine_servings", data=df)
```




    <matplotlib.axes._subplots.AxesSubplot at 0x2154ffede80>




![png](output_51_1.png)


### Otra graficas
_autor: Denisse Orozco_

__PieChart__


```python
df2=df.set_index("continent")
explode = (0, 0, 0.05, 0, 0)  # explode 3rd slice
cmap = plt.get_cmap('Spectral')
colors = [cmap(i) for i in np.linspace(0, 1, 8)]
df2["beer_servings"].plot(kind="pie", figsize=(5, 5), colors= colors, explode= explode)

plt.tight_layout()
```


![png](output_54_0.png)


VARIOS GRAFICOS EN UNA MISMA VENTANA


```python
names =  df["continent"]
values= df["wine_servings"]

fig, axs = plt.subplots(1, 3, figsize=(10, 5), sharey=True)
axs[0].bar(names, values, )
axs[1].scatter(names, values)
axs[2].plot(names, values)
fig.suptitle("Promedio del consumo de vino por continentes")
```




    Text(0.5,0.98,'Promedio del consumo de vino por continentes')




![png](output_56_1.png)



```python

```
