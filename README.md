# Rocketbot 🚀 : Proyecto Mercado Libre

![rpa_foto_portada](https://github.com/user-attachments/assets/5856b017-6874-4660-8dd6-6d0b7e582bd8)

## Índice 📋

1. Descripción del proyecto.
2. Acceso al proyecto.
3. Demostración del funcionalidades y aplicaciones.
4. Tecnologías utilizadas.
5. Colaboradores.
6. Desarrollador del proyecto.

## 1. Descripción del proyecto 📚

Este proyecto mustra tan solo una parte de la capacidad de automatizar un proceso de web scrapping utilizando tencología RPA (Robot Process Automation), en particular **Rocketbot** 🚀. El proyecto esta compuesto por 3 robots, el padre llamado **main**, y luego dos robots hijos, llamados **busqueda_suplementos_deportivos** que se encarga de realizar la búsqueda de productos dentro de la página de Mercado Libre, listándolos en un archivo Excel, y luego el segundo, llamado **alerta_suplementos_deportivos**, que toma un precio máximo para cada producto, y luego recorre los registros del archivo hecho por el primer primer robot, y en caso de encontrar un artículo cuyo precio se encuentre por debajo de este umbral, envía un correo electrónico ofertando el producto. Veremos como es posible abrir una pagina web y realizar una búsqueda de, en este caso, artículos en la página de Mercado Libre, extrayendo la información relevante que buscamos analizar, como puede ser: criterio de búsqueda, artículos encontrados, precio, descuento que poseen dichos artículos y el link correspondiente para llegar a ellos, y luego utilizar esta información para generar campañas publicitarias.

Resulta importante remarcar que esto es tan solo un ejemplo, ya que es posible extraer cualquier información de un sitio web usando RPA.

## 2. Acceso al proyecto 📂

## 3. Demostración de funcionalidades y aplicaciones 📝

![upload_db](https://github.com/user-attachments/assets/6bc8dbd9-a81b-41c3-bbd5-1e749ee49017)

Al cargar el archivo `robot.db` 📄, la base de datos aparecerá a la derecha del panel. Al hacer click en esta, nos aparecerá el siguiente menú:

![menu_db](https://github.com/user-attachments/assets/958f3e9a-0fa9-4ccb-a3df-0008c8970556)

En él, se pueden visualizar los robots alojados dentro de la base de datos.

### **Main** 🤖

![main](https://github.com/user-attachments/assets/58d2c408-be87-45f5-bdc0-25051a098282)

Este robot solo cuenta con algunas configuraciones iniciales que se respetan dentro de todos los robots de la base de datos, extraidos del archivo `config.ini` 📄 que se encuentra dentro de la carpeta `resources` 📁, y dos comandos que ejecutan los robots hijos en el orden apropiado para la ejecución del proceso completo, que se efectúa al presionar el botón **Run** marcado en la parte superior de la imagen.

### **Busqueda_suplementos_deportivos** 🤖

![pantalla_inicial](https://github.com/user-attachments/assets/1d3a6160-2775-43c2-9a00-98724c82aee4)


Esta es la pantalla inicial una vez ingresamos al menú del robot. Para ejecutarlo, solo debemos presionar el botón marcado en un recuadro rojo que dice **Run**. Este ejecutará el robot con las variables predeterminadas.

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

### **Alerta_suplemento_deportivo** 🤖

Al igual que en los robots anteriores, para ejecutar el proceso solo se necesita presionar el botón de **Run**.
Después de algunas configuraciones iniciales traidas del archivo `config.ini` 📄, esta automatización intentará abrir el archivo creado por el robot **busqueda_suplementos_deportivos**🤖.

![obtener_productos](https://github.com/user-attachments/assets/8e872c98-4537-482a-9769-90a36a116a96)

Lo primero que hará sera obtener los productos (criterios de busqueda utilizado para listar los artículos) y mantener los valores únicos presentes en el archivo.

![producto_filtro](https://github.com/user-attachments/assets/152f40ea-5512-42d8-a74a-cb0212dd72c2)

Luego, el proceso iterará sobre esta lista con los valores únicos obtenidos en la etapa anterior, y determinará el precio máximo para cada uno de los productos, también alojados en el archivo `config.ini` 📄.

![segundo_bucle](https://github.com/user-attachments/assets/c6017395-cb6d-455c-921e-4a30a77e7f27)

Luego, dentro del primer bucle tenemos otro, que recorrerá todos los registros que se encuentran dentro del archivo Excel una vez por cada valor único de producto (criterio de búsqueda).

![condicional](https://github.com/user-attachments/assets/48d5d258-323f-43c9-930e-5638159cd3fa)

Por cada iteración, si el artículo coincide con el producto que estamos analizando, y su precio es menor al precio máximo establecido, almacenará dicho registro en una variable que contendrá los artículos a ofertar en la campaña de marketing.

![conexion_gmail](https://github.com/user-attachments/assets/5114e939-6228-44a6-ad55-c1900d09d0f8)


Si la variable que contiene los artículos a ofertar contiene al menos un registro, se establecerá la conexión al servidor de Gmail✉️.

*Nota: el correo y la contraseña han sido encriptados para protección de datos sensibles*

Luego se hara una validación para asegurarse que la conexión al servidor se ha realizado correctamente, y entrará en un nuevo bucle:

![alerta_marketing](https://github.com/user-attachments/assets/3b915cd8-cdee-4bae-8b70-6edf9d9dfd2e)

Este, itera sobre la lista que contiene los artículos que cumplieron con la condición de tener un precio menor al máximo establecido, y obtiene de cada registro:

* Nombre del artículo
* Precio
* Descuento (si aplica)
* Link del artículo

Por último, el robot enviará un correo al usuario con la información anterior para ofertar los artículos que pueden interesarle.


## 4. Tecnologías utilizadas 🛠️

* `Rocketbot Studio (v.2025.01.06)`
* `Git and GitHub`
* `OBS (screen recorder)`
* `HTML`
* `Python`
* `Excel (requerido para ejecutar el robot)`

## 5. Colaboradores del proyecto 🏗️

Quiero agradecer a:

![BotSolutions](https://github.com/user-attachments/assets/4dda0262-5b97-4b60-a692-db5aa7825d4b)

#### BotSolutions

Por la capacitación en la herramienta y en la oportunidad de aprender de la mano de ellos.

------------------------------------------------------------------------------------------------------
![Rocketbot](https://github.com/user-attachments/assets/5e61e12c-8fe3-4505-8463-0cf648ecda96)

#### Rocketbot

Por desarrollar la herramienta y proveer cursos gratuitos para aprender a utilizarla.


## 6. Desarrollador del proyecto 👷

![imagen-readme](https://github.com/user-attachments/assets/133bc743-0424-4120-a7a6-7245d2f28f8c)

**| Ignacio Majo | Data Scientist Junior | Junior RPA Developer |**

