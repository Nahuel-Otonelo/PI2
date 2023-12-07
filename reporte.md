<center><p align="center"><h1>Accidentes de tránsito en la Ciudad de Buenos Aires, Argentina</h1></p>
</center>


Informe en base a datos extraidos de datos oficiales del Gobierno de la Ciudad durante el período Enero del 2016 a Diciembre del 2021

## Introducción
La ciudad de Buenos Aires es el principal conglomearado de la Argentina y en ella se producen a diario accidentes de tránsito que en muchos casos provocan víctimas fatales. La cantidad de tránsito que circula por ella no solo es debido a la población que en allí vive, sino que al ser la capital de la Republica Argentina, millones de personas provenientes del conurbano y de distintas localidades viajan a diario para trabajar, realizar trámites o desarrolar distintas actividades. En la ciudad no solo están los distintos ministerios, secreterarías y dependencias del gobierno, sino que la mayoría de las empresas tienen alli su cede central. 

En la Argentina es común el dicho "Dios está en todos lados, pero atiende en Buenos Aires", talvez ello explique el altisimo tránsito de gente que se dirige hacia la ciudad todos los días.

Dada la alta circulacion vehicular es de esperar un número importante de siniestros de todo tipo. 

Este informe está basado en datos oficiales del Gobierno de la Ciudad y busca mostrar tendencias, patrones e información que permita hacer foco en disminuir los accidentes que se producen con mayor frecuencia y tienen mayor impacto en vidas.


## Datos:

Desde la [página](https://data.buenosaires.gob.ar/dataset/víctimas-siniestros-viales) del gobierno, pueden descargarse datos de siniestros viales que provocaron lesiones, y homicidios en formato xlsx. En este trabajo se analiza solo el archivo **Homicidios (XLSX)**. Este archivo a su vez posee dos tablas, una llamada **hechos** y otra **víctimas**. En la tabla hechos hay información a cerca del accidente y en la tabla víctimas de las personas involucradas en el suceso.

Por si queres ir directo a [Conclusiones](#Conclusiones)


### Análisis de la tabla **hechos**

#### Número de siniestros segun cantidad de víctimas registradas
Aunque para mayor detalle, se recomienda ingresar al archivo ETL y EDA, la mayor cantidad de víctimas fatales registrada en un accidente es 3, siendo que en la mayoría de los accidentes se produjo una víctima unicamente.

#### Segregación por dia de la semana.

Para el campo fecha, se contabilizan la cantidad de siniestros registrados por días de la semana:

![accidentes por dia](Accidentes_dia.png)

Si bien no hay mucha diferencia en cantidad de siniestros, el primer dia de la semana es cuando se producen la mayor cantidad de accidentes y podría entenderser que es por un mayor tránsito. 

En los días Sabado y Domingo se supone que hay menos tránsito por no ser días laborables y uno esperaría menores accidentes, por eso debería estudiarse con mayor profundidad si estos accidentes son por actividades nocturnas.


#### Segregación por mes del año.

Del mismo modo, puede verse la distribución de los accidentes por meses del año. 

![accidentes por mes](Accidentes_mes.png)

A priori, uno supondria que dado que en Enero el tránsito es menor que en los otros meses, podría esperar menor cantidad de accidentes, debera analizarse este punto con mayor profundidad. 

#### Accidentes fatales por año cada 100000 habitantes.

Utilizando informacion de los censos del 2010 y del 2022 respecto a la cantidad de población de la Ciudad, se interpola la población para calcular la población en los años de analisis.

![accidentes por c 100 k](Accidentes_c100k.png)

Puede verse una disminución progresiva de los accidentes con víctimas fatales a medida que pasan los años cada 100000 habitantes. Aun asi tener encuenta que durante los años 2020 y 2021 pero sobre todo 2020, el tránsito vehicular ha disminuido debido a las medidas de aislamiento  preventivo a causa del covid impulsadas por el gobierno nacional.


#### Víctimas por hora del dia


![accidentes por hora](Accidentes_hora.png)



#### Accidentes por tipo de vía.



![accidentes por tipo via](Accidentes_via.png)




#### Siniestros en esquinas

De acuerdo a las definiciones del diccionario (información a cerca de los datos de las planillas), en caso de que el siniestro se haya producido en una esquina, entonces en la columna 'Cruce' debería verse el nombre de la calle. Puede deducirse entonces que si el registro en esa columna esta en NaN, el siniestro no se produjo entonces en una esquina. De acuerdo a este análisis, el 75 % de los accidentes se produjeron en esquinas.



#### Cantidad de accidentes por comuna


En la Ciudad de Buenos Aires hay una división política por [comunas](https://buenosaires.gob.ar/comunas). En la planilla de hechos esta especificado en que comuna se produjeron.


![accidentes por comuna](Accidentes_comuna.png)

#### Participantes del siniestro

En el diccionario de los datos definen al campo "participantes" como la conjunción de víctima y acusado. Se muestra en el gráfico de aqui abajo la frecuencia de las distintas convinaciones de victima-acusado


![participantes del siniestro](Accidentes_participantes.png)

#### Víctimas del siniestro

Teniendo en cuenta el diccionario de homicidios, "víctimas" se refiere al vehículo que ocupaba la persona perjudicada.

![víctimas del siniestro](Accidentes_victimas_siniestro.png)


La mayoría de las víctimas en accidentes de tránsito son motociclistas y peatones.

No confundir con el apartado anterior, en donde se contabiliza la cantidad de siniestros de cada tipo y en donde el siniestro pasajeros-peaton es el mas númeroso. Si se ve en esa misma sección puede verse que el segundo tipo de siniestro y el tercero involucran a una moto. Es decir, si bien el tipo de accidente mas frecuente es peaton-pasajeros, la principal víctima de los accidentes son los motociclistas.


#### Acusados del siniestro

![acusados del siniestro](Accidentes_acusado.png)

Puede verse de nuevo aqui la relación con los gráficos anteriores en donde las motos y los peatones son las principales víctimas de los accidentes. Ahora bien, los acusados son los autos, vehículos de pasajeros y de cargas.

## Analisis de la planilla **víctimas**

Esta planilla tiene la información de cada victima de cada accidente registrado en la tabla de hechos. Se realiza un analisis similar de cada campo y la relación entre ellos.

#### Rol de las víctimas en el siniestro

Si se realiza un conteo, el rol que mayor ocupaban las víctimas es el de conductor. Ahora bien, conductor tambien incluye a conductor de moto. 

De acuerdo al cálculo realizado en el archivo EDA y ETL que forma parte de este directorio, 261 de 330 personas (aprox 80 %) conductoras fallecidas, pertenecian a conductores de moto.

#### Rango etario de las víctimas y vehículo que ocupaban en el accidente

Se grafica segun rango etario, los vehículos ocupados por las víctimas en el accidente (incluido peatones)


![vehículos rango etario](Accidentes_rangoetario_vehiculo.png)




En este gráfico puede verse las víctimas segun el rango etario. En el rango de 16 a 27 años ("adolescentes") puede verse la gran diferencia de la principal causa de muerte respecto al rango que sigue de 27 a 40 años. Si bien en ambos es la moto, en el segundo caso la diferencia con respecto a peaton y a auto es mucho menor. Ya en el rango de 40 a 60 puede verse que la moto deja de ser el vehículo que tiene mayor número de muertes.

## Conclusiones:

Las conclusiones son con los datos disponibles y estan basadas solo en la información de homicidios entre el 2016 y 2021. No se tiene en cuenta la medición real del tránsito que ingresa a la ciudad (que también puede descargarse de la pagina oficial del Gobierno de la Ciudad de Buenos Aires).

* Mas allá de que sabemos que el tránsito durante el año 2020 fue mucho menor al de años anteriores por las restricciones de circulación por la pandemia Covid-19, puede verse una disminución sostenida de los accidentes viales cada 100000 habitantes entre 2016 y 2021.

* Mas del 60 % de los homicidios se producen en avenidas y el 19 % se produce en autopistas (el tipo de vía en donde se registraron menor cantidad de homicidios).

* El tipo de siniestro con muertes mas registrado es el de "vehículo pasajeros" - "peaton".

* La principal causa de muerte en siniestros, es provocada por accidentes viales de motociclistas y en segundo lugar peatones. Los peatones son atropellados principalmente por vehículos de pasajeros y en menor medida por vehiculos particulares.

* El mayor número de acusados del accidente (acusado no implica implicacion legal) son automovilistas.

* La comuna con mayor cantidad de siniestros es la 1 seguida de la 4, y la 9.

* El 75 % de las victimas son hombres.

* En el rango de 16 a 27 años de edad, el mayor número de víctimas es por muy lejos motociclistas, en el rango de 27 a 40 también lo sigue siendo pero con menor diferencia y toma mayor relevancia las muertes por peatones y automovilistas. Para mayores de 40 el mayor número de muertes es de peatones.

* En el rango etario en donde hay mayor muertes de ciclistas es de 40 a 60.