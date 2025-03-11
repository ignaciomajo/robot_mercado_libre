# Rocketbot: busqueda_suplementos_deportivos

![rpa_foto_portada](https://github.com/user-attachments/assets/5856b017-6874-4660-8dd6-6d0b7e582bd8)

## Índice 📋

1. Descripción del proyecto.
2. Demostración del funcionalidades y aplicaciones.
3. Tecnologías utilizadas.
4. Colaboradores.
5. Desarrollador del proyecto.

## 1. Descripción del proyecto 📚

Este proyecto mustra tan solo una parte de la capacidad de automatizar un proceso de web scrapping utilizando tencología RPA (Robot Process Automation), en particular **Rocketbot** 🚀. En él, se puede ver como es posible abrir una pagina web y realizar una búsqueda de, en este caso, artículos en la página de Mercado Libre, extrayendo la información relevante que buscamos analizar, como puede ser: criterio de búsqueda, artículos encontrados, precio, descuento que poseen dichos artículos y el link correspondiente para llegar a ellos.

Resulta importante remarcar que esto es tan solo un ejemplo, ya que es posible extraer cualquier información de un sitio web usando RPA.


## 2. Demostración de funcionalidades y aplicaciones 📝


![pantalla_inicial](https://github.com/user-attachments/assets/1d3a6160-2775-43c2-9a00-98724c82aee4)



Esta es la pantalla inicial una vez ingresamos al menú del robot. Ejecutarlo, solo debemos presionar el botón marcado en un recuadro rojo que dice **Run**. Este ejecutará el robot con las variables predeterminadas.

A su vez, podemos ver que los pasos que sigue el robot están enumerados en el lado izquierdo encerrados en un recuadro verde, comenzando con el número 1. Esto nos permite entender la lógica que sigue el robot.

Cuando existen pasos dentro de otro, vemos como se produce una pequeña indentación en el panel, y el contador empieza desde el número 1 nuevamente, esto nos dice que dichos pasos, son *hijos* de un paso *padre*. Esto es de suma importancia para poder entender como el robot ejecuta cada actividad.

En este caso, el robot está diseñado para buscar productos que podríamos caracterizar como **"Suplementos Deportivos"**. 

![variable_buscar](https://github.com/user-attachments/assets/54bc2397-8518-41b6-ae1b-066a16dcdbbb)

Como vemos en este paso, se asigna a la variable **{producto}** el valor de 'whey protein' que será el artículo que buscará la automatización dentro de la página de Mercado Libre.

Si se desea que el robot busque otro producto, podemos hacer doble click en el comando, que abrirá la siguiente pantalla:

![cambio_variable](https://github.com/user-attachments/assets/1b8dc7fe-a0d8-44b1-955e-39ddd5562143)

Una vez aquí solo debemos cambiar el valor que se le asigna a la variable.

![abrir_archivo](https://github.com/user-attachments/assets/2e7df83a-72cc-471d-b2c1-81560bde04d5)


Una vez que el robot se asegura que ha encontrado la página, intentará buscar el archivo "suplementos_deportivos.xlsx" en la ruta correspondiente, aquí se debera modificar la ruta hacia donde tengamos el robot guardado. Pero es buena práctica dejar el archivo en la carpeta **resources** dentro del main.

Si este no encuentra un archivo existente, creará uno nuevo con los siguientes encabezados de celda: **id, producto**(correspondiente a la búsqueda realizada), **nombre_articulo, precio**(en pesos), **descuento y link**(correspondiente a dicho artículo).


![while](https://github.com/user-attachments/assets/346aa100-e0fa-4b38-b013-20e1f8753473)

Aquí el robot comenzará a iterar sobre cada uno de los artículos encontrados en la búsqueda. De forma predeterminada, este extraerá la información de los primeros 10 artículos encontrados. 

![image](https://github.com/user-attachments/assets/fcf188c5-a231-47b9-9581-d292f2e58222)

Si se desea cambiar el numéro de artículos de los cuales queremos extraer información, solo se necesita hacer doble click en el comando **while** y cambiar el 10 por el número de artículos deseados.

*Nota: Mercado Libre muestra un máximo de 58 productos por página. Actualmente, el robot no cuenta con el comando para pasar de página.*

![guardado_archivo](https://github.com/user-attachments/assets/a3f24a06-76ca-4001-926f-4f22606c4ce7)


Una vez que el robot haya extraído la información de los artículos delimitados, guardará el archivo en la ruta correspondiende. Este comando tambien debe ajustarse para seleccionar la ruta donde este almacenado el robot. Se mostrará un mensaje en pantalla informando si el archivo se ha guardado o no correctamente.

*Nota: En caso de recibir un error, revisar el formato en que se ha escrito la ruta donde el robot debe guardar el archivo.*


#### El proceso vuelve a repetirse con un segundo producto, por lo que debemos repetir el proceso, comenzando con el comando que asigna un nuevo valor a la variable **{producto}**.

Finalmente el archivo Excel que contiene toda la información extraída quedará guardado en la carpeta **resources** que se encuentra dentro de **main**.

## 3. Tecnologías utilizadas 🛠️

* `Rocketbot Studio (v.2025.01.06)`
* `Git and GitHub`
* `OBS (screen recorder)`
* `HTML`
* `Python`
* `Excel (requerido para ejecutar el robot)`

## 4. Colaboradores del proyecto 🏗️

Quiero agradecer a:

![BotSolutions](https://github.com/user-attachments/assets/4dda0262-5b97-4b60-a692-db5aa7825d4b)

#### BotSolutions

Por la capacitación en la herramienta y en la oportunidad de aprender de la mano de ellos.

------------------------------------------------------------------------------------------------------
![Rocketbot](https://github.com/user-attachments/assets/5e61e12c-8fe3-4505-8463-0cf648ecda96)

#### Rocketbot

Por desarrollar la herramienta y proveer cursos gratuitos para aprender a utilizarla.


## 5. Desarrollador del proyecto 👷

![imagen-readme](https://github.com/user-attachments/assets/133bc743-0424-4120-a7a6-7245d2f28f8c)

**| Ignacio Majo | Data Scientist Junior | Junior RPA Developer |**

