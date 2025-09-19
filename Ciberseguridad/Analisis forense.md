# <p align="center">Informática forense</p>
Buenas! Antes de empezar con este apartado, recomiendo ver primero el apartado de ciberseguridad conceptos y csoas, ya que es una introduccion que te ayudará a en tender mejor los conceptos de cada apartado, ademas de mencionar que toda la información que vea en estos repositorios procede del curso de especializacion que he realizado en ciberseguridad, su obtetivo es plasmar conocimientos y asegurarme de que permanencen aqui, por si en algun momento necesito regresar a esta información.

Dicho esto, en este apartado explico que es la informatica forese, como funciona y como se realiza un analisis forense completo, ademas de especifciar que herramientas se usan y como se deben empelar.

Comenzaremos con la parte teorica del proceso y los objetivos y continuaremos con casos practicos yveremos como se realizan, además de que resultados aportan y como deben ser tratados.
> [!NOTE]
> <h3>Al final del documento se especifican 3 casos distintos con los que se realizan 3 analisis forenses distintos.</h3>

## 📑 Índice

1. [¿Qué es la informática forense?](#que-es-la-informatica-forense)
   
   - [Objetivos de la informatica forense](#Objetivos-de-la-informatica-forense)
   - [Identificación de evidencias digitales](#identificacion-de-evidencias-digitales)
   - [Recopilación de evidencias](#recopilacion-de-evidencias)
   - [Preservar la integridad de las evidencias](#preservar-la-integridad-de-las-evidencias)
   - [Presentar un informe de conclusiones y recomendaciones](#presentar-un-informe-de-conclusiones-y-recomendaciones)
     
2. [Proceso para realizar un análisis forense](#proceso-para-reaalizar-un-analisis-forense)
   
3. [Análisis de la línea de tiempo (TimeStamp)](#aalisis-de-la-linea-de-tiempo-timestamp)
   
4. [Análisis de la memoria volátil](#analisis-de-la-memoria-volatil)

5. herramientas y software forense
6. [Análisis de logs](#analisis-de-logs)
   - [Tipos de logs y fuentes](#tipos-de-logs-y-fuentes)
7. Casos practicos
   - caso 1 
   - caso 2 
   - caso 3 
8. detalles ha tener en cuenta

## ¿Que es la informatica forense?
Para comenzar, la informatica forense, tambien llamada analisis forense digital, es una disciplina enfocada en la identificacion, preservacion, analisis y presentación de evidencias digitales, comunemente se enfoncan en casos legales y situaciones realicionada a la seguridad de la informacion.

El proposito de la informatica forense es investigar y resolver situaciones relacionadas a ciberdelitos o ataques informaticos, asi como analizar y responder de manera adecuada a los delitos y violaciones de seguridad que ocurren en el entorno digital.
Ademas, tambien podemos destacar los siguientes objetivos:

## Objetivos de la informatica forense
basandonos en esta definición, podemos dividir los objetivos en los siguientes puntos.
### 1. Identificacion de evidencias digitales
Para comenzar, el primer objetivo es esclarecer la situacion identificando la amenaza o evidencia digital necesaria para llegar a una conclusion oficial.
### 2. Recopilacion de evidencias
A continuacion se debe recopilar las evidencias detectadas lo que nos permitira identifciar las acciones realizadas y los posibles responsables.
Para realizar una recopilacion de evidencias de debe esclarecer la magnitud o el rango del inidente.
### 3. Preservar la integridad de las evidencias
A la hora de preservar las evidencias se debe hacer de forma adecuada mediante el empleo de herramiantas de software forense como x o x, las cuales son herramientas oficializadas con las que se pueden a llegar a conclusiones validas en un juicio.
para mas informacion sobre estas herramientas visita: zzzz
### 4. Presentar un informe de conclusiones y recomendaciones
A la hora de presentar las conclusiones, un analista forense debe presentar un tipo de documento en concreto en el que consta las siguientes partes:

### Partes de un informe de conclusiones
1.
2.
3.
4.
5.
## Proceso para realizar un analisis forense
> [!IMPORTANT]
> Apartir de este punto, tendremos que tener conocimientos especificos y cierto control sobre las herrmaientas implementadas
Para realizar un analisis forense efectivo.
Tendremos que seguir una serie de puntos clave, los cuales son los siguientes:
1. Estudiar el caso y determinar el rango de afección
2. recopilar, preservar y esclareder las evidencias del caso
3. elaborar un informe oficial

A continuacion se espeficica como re realiza de forma practica cada etapa:
### Estudiar el caso y determinar la afección
para comenzar, en la recoleccion de evidencias suelen usarse herramientas como x o x, los cuales recopilan logs y x respegtivamente, como podemos ver, consiste esencialmente, en investigar cuidadosamente el sistema en si en busca de registros o elementos sospechosos como pueden ser: lineas de codigo maliciosas, correos o archivos infectados, perdida de informacion repentina o metadatos.

Para mas informacion sobre los metadatos visita el siguiente enlace "", una pagina web con información sobre x en epecifico. Pero en resumen, son rastros de datos que dejan diferentes archivos al usarlos o ser generados, por ejemplo una foto, pudiendo ser la fecha, ubicacion, o modelo de camara, por ejemplo, acaban resultando muy utiles en investigaciones forenses, aunque no siempre estan presentes, pero compensa mucho tener los metadatos en cuenta en la mayoria de casos.

En resumidas cuentas, antes de usar una herramienta u otra, primero debemos tener claro cuales han sido los eventos sucedidos y el resultado del ataque en si, debido a esto y a la necesidad de inspeccionar potencialmente el sistema entero, para considerarse un analista forense y poder hacer el proceso de forma adecuada y prfoesional, se requieren ciertas habilidades y conocimientos, sim embargo, se pueden realizar analisis simples e incluso automatizarlos, de tal manera, que no se requeriria la intervencion de un especialista en ciberseguridad, ya que puede tratarse de un caso sencillo o que se este utilizando un software analizador, el cual analiza el sistema en busca de walware o infiltraciones en el sistema y es capaz de elaborar conclusiones e incluso informes oficiales, siempre y cuando se trate de casos simples.

## Aalisis de la linea de tiempo (TimeStamp)
importancia del 

## Analisis de la memoria volatil


## Analisis de logs

### Tipos de logs y fuentes

### Herramientas para todo lo de arriba

## Detalles a tener en cuenta

A partir de este punto, necesitaremos conocimientos extensos y concretos sobre multiples aspegtos de la informatica, trataremos unos ejemplos para que se aprecie a que me refiero concretamente.
caso 1, las credenciales de un trabajador an sido filtradas mediante fishing, es decir, tratar de engañar al trabajador mediante correos electronicos, llamadas u otras formas de ingeñeria social con el fin de obtener las credenciales de acceso al servidor de la empresa, acto seguido, se uso este acceso para copiar la base de datos de la empresa y posteriormente eliminarla por completo, provocando grandes perdidas y daños graves a la empresa, por ultimo el ataque termina con una amenaza realizada por el ciberatacante, en la cual, nos exige una suma de dinero o nuestra base de datos con informacion privada de nuestros clientes sera publica o vendida a uan entidad muy interesada en esta información.

Por cierto, os sorporendderia la cantidad de veces que ha ocurrido, para más información visita esta pagina "nombre", su objetivo es listar las bases de datos de empresas que han sido filtradas y liberadas al publico, es decir, han sido victimas de un ciberataque.
En este caso, tendriamos que comenzar con una investigación en el sistema para averiguar que ha pasado, en este caso, se trata de un acceso no permitido, si bien es posible que el trabajador por si mismo reporte el mal uso de sus credenciales, es posible que dedica no comunicarlo ya que se consideraria un fallo grave del trabajador, para saber que ha ocurrido deveremos explorar los sistemas de logs, como hemos visto antes, estos sistemas se encuentran en muchos de los sistemas que se usan en la empresa, como bases de datos, acceso a internet a traves del firewall, o incluso iniciar sesion en el propio equipo ya que tanto Windows como Linux tienen sus propios registros.

En cualquier caso, en este caso se detectaria un acceso al sistema con las credenciales de este trabajador y, acontinuacion, se realizan las acciones que hemos planteado, realizar una copia y luego borrar por completo la base de datos, estos registros serian nuestro objetivo, ademas, se consideran pruebas importantes y debe 
## Enlaces de interes 

