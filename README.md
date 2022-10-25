<h1 align=center><font size = 6>Brecha salarial en el sector privado de Argentina</font></h1>
<br>

###  **Introducción**
***
En este proyecto se evalúa la brecha salarial existente en Argentina dentro del sector privado, utilizando los salarios brutos informados por las empresas a la Administración Federal de Ingresos Públicos (AFIP) sobre la nómina del personal en relación de dependencia. Estos informes se realizan mediante el formulario N° 931 y tienen carácter de declaración jurada. Las mismas empresas también deben declarar su actividad principal según un sistema de clasificación conocido como Clasificador de Actividades Económicas (CLAE).  
El período analizado va desde Enero del 2007 a Junio 2022 basado en la información proporcionada a la fecha por las autoridades.  
Por otro lado, la clasificación sobre el género que realizaron en este dataset es determinada a partir de la Clave Única de Identificación Tributaria (CUIT) o Documento Nacional de Identidad (DNI).  
En consiguiente, se van a obtener datos que permitan comparar los salarios brutos entre hombres y mujeres durante todo ese período y segmentado por las distintas actividades.


### **Consideraciones generales**
***
Cabe destacar que la clasificación binaria realizada (hombre y mujer) resulta ineficiente para cubrir la complejidad comprendida en el concepto de género. Sin embargo, a los fines de este estudio cuando se mencione la brecha salarial o de género será desde este enfoque tradicional debido a que los datos recolectados se encuentran plasmados de esta forma.  

Los salarios informados son salarios brutos mensuales (exentos de aportes y deducciones  particulares) y se encuentran en pesos argentinos. Debido a lo dificultoso de interpretar los datos y visualizaciones del salario en pesos durante un período de varios años, a causa de la depreciación frente a la inflación, se van a utilizar salarios dolarizados. Dicha dolarización de los salarios no altera la brecha salarial que se obtendría al comparar salarios en pesos pero si permite una comparación en gráficas con mucha mayor claridad. La dolarización fue calculada con el valor del dólar libre o dólar blue respectivo de cada fecha para evitar confusiones al utilizar el dólar oficial en períodos de restricción cambiaria.  

De las distintas clasificaciones de actividad que hay sobre las empresas se seleccionó la CLAE2 que cuenta con más de 80 categorías perfectamente descriptas.

### **Data**
***
Toda la información utilizada es pública, proveniente del Ministerio de Economía de la Nación Argentina y obtenida por medio de la web https://datos.gob.ar/. Para este estudio en particular se utilizaron los datasets de <a href='http://datos.produccion.gob.ar/dataset/803a2436-0240-4f87-916b-25cad0213918/archivo/'> Percentiles de salario total empresas por género y clae2 </a> y <a href='http://datos.produccion.gob.ar/dataset/803a2436-0240-4f87-916b-25cad0213918/archivo/82c6602b-0138-4de5-a7c3-33e397750dec'> Diccionario de claes </a>.    

Estos datos se obtienen en formato CSV listos para iniciar su proceso de transformación y carga en la Jupyter Notebook.

Por otro lado, para la obtención del valor del dólar libre o dólar blue histórico se utilizó la página web de <a href='https://www.ambito.com/contenidos/dolar-informal-historico.html'> Ámbito Financiero </a>. En este caso, el archivo obtenido fue un .xlsx de Excel al que se le realizaron operaciones de transformación mínimas para obtener el CSV de trabajo.

Si desea consultar la metodología utilizada por el Ministerio de Economía de la Nación Argentina para la realización de estas series de información puede hacerlo en el siguiente  <a href='https://datos.gob.ar/dataset/produccion-percentiles-salarios-por-genero-actividad/archivo/produccion_3bcac8aa-7636-4e18-80d3-1f63da309ec3'>  link </a>.

### **Metodología**
***
La metodología de extracción, transformación y carga de los datos se realizó en Python por medio de librerías como Numpy y Pandas. Dejo una referencia a la <a href='https://github.com/gastonvermeulen/brecha_salarial/blob/main/notebooks/brecha_salarial_notebook.ipynb'> Jupyter Notebook </a> donde se encuentra todo el proceso documentado. 


### **Comparación y visualización de los datos**
***
Los datos procesados dieron origen a 4 archivos CSV: valor histórico del dólar, diccionario de actividades clae2, salarios dolarizados de hombres según actividad y salarios dolarizados de mujeres según actividad. Tras un correcto modelado de los datos a través de PowerBI se obtienen diversas gráficas que permiten comparar, visualizar y extraer información relevante.

En el siguiente <a href='https://app.powerbi.com/view?r=eyJrIjoiYjRhN2RiOGMtNzM2OC00N2U1LTg4YjQtYzIxMTBmMTlhMzA2IiwidCI6Ijc5M2I4YWQ1LTU0ZWMtNDYyOS04ZWViLWM4MDRjMWEzOGM1ZCJ9'> link </a> puede interactuar de forma dinámica con estas visualizaciones y sacar sus propias conclusiones. -Se recomienda utilizar una PC para interactuar de la mejor forma con la visualización aunque es posible realizarse mediante celulares o móviles-

Esta visualización le permite segmentar por todas, una o varias actividades y también segmentar por diversos períodos de tiempo (dentro del 01/2007 al 06/2022). Las gráficas muestran la comparación entre el salario bruto dolarizado de hombres y mujeres, y la evolución de la brecha salarial en el tiempo.

### **Resultados y discusión**
***
El análisis arroja resultados que van en línea con las estimaciones actuales sobre la brecha salarial o de género existente en Argentina. En Junio del 2022 se registra una brecha salarial en el sector privado del 16,4 %. Sin embargo, se observa una clara diferencia cuando se analizan actividades económicas en particular.

En actividades como la Pesca y acuicultura o el Transporte acuático la brecha salarial actual asciende a más del 50 % (57,5 % y 50,3 % respectivamente). También, se observa una brecha salarial elevada en actividades de Transporte aéreo durante todo el período evaluado con un valor promedio del 35,1 %. Será motivo para otro estudio el investigar si esta situación puede deberse a la disparidad entre el salario percibido por realizar la misma tarea o a la falta de mujeres en puestos ejecutivos o de mayor jerarquía en este tipo de sectores, que le permitan cosechar salarios más abultados. El top de actividades con mayor brecha salarial lo completan Servicios asociados a la actividad financiera y de seguros, y Actividades de apoyo al petróleo y la minería con una brecha salarial promedio del 38,1 % y 34,7 % respectivamente.

Por otro lado, existen actividades donde las mujeres ganan más que los hombres y algunos casos son realmente llamativos. El dato más sorprendente es el de Construcción de edificios y partes donde la brecha salarial es del -39,3 % en favor de las mujeres; similar a ésta, en Actividades especializadas en construcción la brecha salarial es del -4,2 %. Escapa del objetivo de este informe esclarecer o poder fundamentar estos valores pero podría estar relacionado con el grado de informalidad que se maneja en este sector y en varios sectores, lo cual complicaría el análisis del salario real percibido por los trabajadores. Dentro del top de las actividades donde las mujeres se encuentran por encima le siguen Silvicultura y explotación forestal (-29,5 %), Elaboración de productos de madera (-14,5 %), Obras de ingeniería civil (-7,8%) y Enseñanza (-3,2 %) a lo largo de todo el período evaluado.

Por último, si comparamos la brecha salarial del sector privado en Junio 2022 del 16,4 % con la que existía en Enero del 2007 del 21,8 %, se observa una reducción de la misma en más de 5 puntos porcentuales que equivalen a una disminución del 24,8 %.

### **Conclusión**
***
Teniendo en cuenta que este estudio no profundiza en la participación existente de hombres y mujeres en las diversas actividades económicas ni su distribución en cuanto a puestos que ocupan dentro de las organizaciones o empresas, es difícil determinar las causas que expliquen los números informados. Es cierto que hoy hay diversos enfoques y analizar esta problemática en detalle es sumamente complejo. Sin embargo, se hace evidente que tanto por una menor participación, por cobrar un menor salario a misma tarea realizada o por una menor cantidad de mujeres en puestos ejecutivos o de mayor jerarquía, las mujeres quedan rezagadas en cuanto al salario percibido plasmando la brecha salarial actual.

Otra cuestión que escapa de la incumbencia de este análisis es la informalidad existente en Argentina. El trabajo informal, que se calcula está cercano al 40 % de los trabajadores totales, seguramente altere los resultados presentados y posiblemente los empeore.

A pesar de todo, es notorio destacar que en la gran mayoría de actividades hay una evolución favorable de esta brecha que se refleja con la disminución de la misma durante los 15 años comprendidos en el período 2007 al 2022. Esperemos que los factores que están influyendo positivamente, como políticas con perspectiva de género y fundamentalmente el abordamiento y una conciencia social diferente sobre estos temas, continúen ayudando para lograr lo más pronto posible un escenario de igualdad total.
 

***
Este informe fue realizado por  <a href='https://www.linkedin.com/in/gast%C3%B3n-vermeulen-73a93239/'> Gastón Vermeulen </a>
