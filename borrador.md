## Algunos temas a discutir:

Notación:
Las columnas de las tablas continenen códigos que representan valores. Las relaciones código-valor están descritas en una hoja a parte (VARIABLES ó VALOR ASIGNADO).

Por ejemplo:
pares código-valor de la columna  CAUSA_DE_DESCOMPENSACION:

```
código | valor
1 | CAUSA INFECCIOSA
2 | CAUSA FACTICIA
3 | CARDIOVASCULAR
4 | DEBUT
5 | OTRAS
```

#### Reporte limpieza de datos:
- códigos con "no|datos" -> NA
- valores con "no hay|sin" -> NA
- Igualar nombres de columnas 2018-2021.
- Igualar valores con nombres diferentes 2018-2021.
- recuperar "causas_de_descompensacion" a partir de "ingresos" base 2018.

### Diferencias en códigos-valores en bases 2018-2021

- Diferencias en pares código-valor. Uso valores.
- Problemas al comparar algunas características:

Por ejemplo, debut no es un valor en 2021:

![[Screen Shot 2022-08-16 at 14.54.38.png|350x220]]

#### Códigos que no corresponden a valores. 

Por ejemplo:

```
código | valor
4 | tiempo_de_enfermedad
5 | tomografia_de_torax
```

#### Electocardiograma: 5 y 3.

#### Datos faltantes
- 11 personas con varios datos faltantes en la base 2021.

![[row_nas_2021.jpeg|500x350]]
![[col_nas_2021.jpeg|500x350]]

### Estadísticas 
#### Comparación 2018-2021
Las poblaciones 2018-2021 se parecen en términos de edad y sexo.

![[Screen Shot 2022-08-16 at 14.10.46.png|450x230]]
![[Screen Shot 2022-08-16 at 14.11.40.png|450x450]]

Para el resto de variables relativas a las frecuencia y causas de descompensación, y tiempo de enfermedad ver tabla "descompensacion.xlsx".

#### Comparación pacientes 2021 con/sin Covid

Ver tablas "all_covid.xlsx" y "detail_covid.xlsx".