# Ranking Garka API 🧐

Ranking Garka es una API con la finalidad de poder recopilar la mayoría de los "10 DE LA C\*NCHA' LA MADRE" que fueron trasmitidos en Radio Garka. <br>
> [!NOTE]
> Este proyecto está en constante evolución, y en el futuro se planea agregar nuevas funcionalidades que amplíen la experiencia y capacidades de la API.

## Desarrollador 👨‍💻:

- **Desarrollador:** Matías Di Risio 👍
- **GitHub:** [DiriARG](https://github.com/DiriARG)

## Tabla de contenidos 📚:

- [Previo a iniciar](#previo-a-iniciar-)
- [Instalación](#instalación-)
- [Configuración de la Base de Datos](#configuración-de-la-base-de-datos-️)
- [Iniciando el proyecto](#iniciando-el-proyecto-)
- [Configuramos el archivo .env (Environment Variables)] (#configuramos-el-archivo-env-environment-variables-%EF%B8%8F)
- [Estructura del proyecto](#estructura-del-proyecto-)
- [Descripción de archivos](#descripción-de-archivos-)
- [Rutas de la API](#rutas-de-la-api-%EF%B8%8F)
- [Ejemplos de uso](#ejemplos-de-uso-)
- [Recursos](#recursos-)

## Previo a iniciar 🕒:

- **Descarga e instala** Visual Studio Code. Es el editor de código recomendado para abordar este proyecto.
- **Descarga e instala** Node.js, un entorno de ejecución de JavaScript de código abierto y multiplataforma que permite crear servidores, aplicaciones web, APIs, herramientas de línea de comandos y scripts.
- **Crea una cuenta** en MongoDB y **descarga e instala** Compass, que es una herramienta gráfica interactiva para consultar, optimizar y analizar datos en MongoDB.

## Instalación 📥:

1. **Fork** el repositorio desde [aquí](https://github.com/DiriARG/Ranking_Garka_API/fork).
2. **Clona** tu fork en tu máquina local:

```bash
git clone https://github.com/tu-usuario/tu-repositorio-fork.git
```

3. Ahora **abre** Visual Studio Code y la carpeta correspondiente (Ranking_Garka_API).
4. **Inicia** una nueva terminal y escribe `npm install`, este comando en un directorio que ya contiene el archivo `package.json` genera que <u>npm</u> instale las dependencias especificadas en ese `package.json` y actualice el `package-lock.json` con las versiones exactas de esas dependencias.
> [!TIP]
> Si seguiste estas instrucciones de instalación mediante forkear el repositorio y clonandolo a tu máquina local, evita el apartado [Iniciando el proyecto](#iniciando-el-proyecto-), ya que esta orientado a las personas que simplemente han descargado algunos archivos individuales del proyecto

## Configuración de la Base de Datos 🗄️:

1. **Crea** una nueva base de datos en MongoDB Compass:
   - Abre MongoDB Compass.
   - En el panel izquierdo, sobre la "connection string", haz click en **Create database**.
   - Dale un nombre significativo a tu base de datos, por ejemplo: `RankingGarka`.
   - Crea también una colección inicial llamada `trailerazos` o cualquier otro nombre que prefieras.
2. **Importa** los archivos JSON que se encuentran en la carpeta "datos_json":
   - Ve a la colección que acabas de crear.
   - Haz click en "ADD DATA" --> "Import JSON or CSV file" y selecciona el archivo correspondiente a esta colección, en este caso, "10_TRAILERAZOS.json".
   - Repite este proceso para cada archivo JSON que necesites importar, creando una nueva colección para cada archivo. Es recomendable nombrar cada colección en base a su contenido, por ejemplo: `trailerazos`, `guitarristas`, etc.
3. **Verifica** que las colecciones hayan sido creadas correctamente:
   - Una vez importados los archivos, revisa cada colección en MongoDB Compass para asegurarte de que los documentos JSON se hayan importado correctamente.
   - Asegúrate de que no haya duplicados ni problemas de formato en los documentos importados.

## Iniciando el proyecto 🚀:

Este apartado esta orientado a las personas que simplemente quieran descargar los archivos individualmente sin forkear el repositorio, por lo tanto, los archivos que son necesarios para el correcto funcionamiento de la API son los siguientes:

```plaintext
/src
  /config
    - base_de_datos.js
  /controladores
    - controlador_principal.js
    - controlador_ranking.js
  /datos_json
    - 10_BALADAS_DEL_ROCK.json
    - 10_CANCIONES_CON_IRA.json
    ... (TODOS los otros archivos JSON restantes)
  /modelos
    - baladas_del_rock.js
    - canciones_con_ira.js
    ... (TODOS los otros modelos restantes)
    - modelos_de_ranking.js
  /rutas
    - ruta_principal.js
    - rutas_ranking.js
  /tests
    - api.http
    - Ranking_Garka_API.postman_collection.json
/.env-copia
/app.js

```
> [!IMPORTANT]
> Antes de comenzar, **asegúrate** de haber completado la [Configuración de la Base de Datos](#configuración-de-la-base-de-datos-️). Si ya realizaste estos pasos y tienes la estructura del proyecto como se muestra arriba, puedes continuar con lo siguiente:

- Abrimos la terminal e inicializamos un nuevo proyecto con `npm init -y`. Esto nos creara el archivo `package.json`.
- Luego instalamos las dependencias necesarias: Express JS (entorno para desarrollar la API), Mongoose (biblioteca de modelado de objetos para MongoDB y Node.js) y Morgan (Middleware de registro de solicitudes HTTP) con el siguiente comando: `npm i express mongoose morgan`. Al haber instalado dichos paquetes se crea el archivo `package-lock.json` y la carpeta `node_modules`.

## Configuramos el archivo .env (Environment Variables) ⚙️:

1. **Renombra** el archivo llamado `.env_copia` a `.env`, y luego **modifica** su contenido según tu entorno:
   - MONGODB_URLSTRING: Copiamos la cadena de conexión desde la pagina de MongoDB o propiamente desde el MongoDB Compass.
   - PUERTO: Escribimos el puerto que se va a usar para conectar a la API.
   - NOMBRE_BASE_DE_DATOS: Escribimos el nombre de la base de datos en la cual vamos a acceder.
2. **Configura las colecciones** correspondientes a los rankings que se importarán en MongoDB:
   - NOMBRESRANKINGS_COLLECTION = Escribe el nombre de la colección que contendrá los rankings generales.
   - TRAILERAZOS_COLLECTION = Define el nombre de la colección que nos permitirá obtener los datos del ranking "TRAILERAZOS".
   - COMIDASDEGIRA_COLLECTION = Asigna el nombre de la colección correspondiente a "COMIDAS DE GIRA". <br>

Y así, de manera similar, configura todas las colecciones necesarias **para cada colección creada** en MongoDB.

## Estructura del proyecto 📂:

Así será la estructura que encontraremos en nuestro editor de código fuente, en mi caso, Visual Studio Code (puede variar la estructura en caso de haber instalado los archivos de forma individual).

```plaintext
/node_modules
  - (Contiene todos los módulos y bibliotecas necesarias para el proyecto)
/src
  /config
    - base_de_datos.js
  /controladores
    - controlador_principal.js
    - controlador_ranking.js
  /datos_json
    - 10_BALADAS_DEL_ROCK.json
    - 10_CANCIONES_CON_IRA.json
    ... (TODOS los otros archivos JSON restantes)
  /modelos
    - baladas_del_rock.js
    - canciones_con_ira.js
    ... (TODOS los otros modelos restantes)
    - modelos_de_ranking.js
  /rutas
    - ruta_principal.js
    - rutas_ranking.js
  /tests
    - api.http
    - Ranking_Garka_API.postman_collection.json
/.env
/.gitignore
/app.js
/LICENSE
/package-lock.json
/package.json
/README.md

```

## Descripción de archivos 📄:

- **/node_modules**: Carpeta generada automáticamente al instalar las dependencias del proyecto. Contiene todos los módulos y bibliotecas necesarias para el funcionamiento de la aplicación.

- **/src**: Carpeta principal que contiene el código fuente de la aplicación.

  - **/config**: Carpeta que contiene las configuraciones generales del proyecto.

    - **base_de_datos.js**: Archivo que crea y configura la conexión a la base de datos MongoDB usando Mongoose. 

  - **/controladores**: Carpeta que contiene la lógica de los controladores que manejan las diferentes rutas de la API.

    - **controlador_principal.js**: Controlador que maneja la ruta de bienvenida a la API, proporcionando información general sobre ella. 

    - **controlador_ranking.js**: Controlador que maneja todas las rutas relacionadas con los rankings, como obtener nombres de rankings y buscar el top de un ranking específico.

  - **/datos_json**: Carpeta que contiene los conjuntos de datos (datasets) en formato JSON.

    - **10_BALADAS_DEL_ROCK.json**: Archivo de formato JSON que contiene el ranking de "BALADAS DEL ROCK" que se utiliza en la base de datos.
    - **10_CANCIONES_CON_IRA.json**: Archivo de formato JSON que contiene el ranking de "CANCIONES CON IRA" que se utiliza en la base de datos.
    - **... y otros archivos JSON** que representan diferentes rankings utilizados por la API.

  - **/modelos**: Carpeta que contiene los modelos Mongoose para cada ranking y el archivo "modelos_de_ranking.js".

    - **baladas_del_rock.js**: Archivo que define el esquema (schema) y el modelo (model) para las baladas de rock.
    - **canciones_con_ira.js**: Archivo que define el esquema (schema) y el modelo (model) para las canciones con ira.
    - **y otros modelos** que representan distintos rankings en la API.
    - **modelos_de_ranking.js**: Archivo que contiene el mapeo dinámico de todos los modelos de los rankings utilizados por la API.

  - **/rutas**: Carpeta que contiene los archivos relacionados con las rutas de la API.

    - **ruta_principal.js**: Archivo que contiene la ruta de bienvenida a la API, proporcionando un mensaje informativo.
    - **rutas_ranking.js**: Archivo que contiene todas las rutas relacionadas con los rankings, definiendo los endpoints para consultar, buscar y obtener el top de los rankings.

  - **/tests**: Carpeta que contiene archivos para pruebas de rutas. 
    - **api.http**: Archivo de la extensión de VS Code "REST Client" para probar la API.
    - **Ranking_Garka_API.postman_collection.json**: Colección de Postman que contiene ejemplos de las solicitudes a la API para facilitar pruebas y desarrollo.

- **.env**: Archivo que almacena las variables de entorno utilizadas en la configuración del proyecto, como la conexión a la base de datos y las colecciones de los rankings.

- **.gitignore**: Archivo que le indica a Git qué archivos o carpetas deben ser ignorados por el sistema de control de versiones.

- **app.js**: Archivo principal de la aplicación donde se inicializa el servidor y se configuran las rutas y los middlewares.

- **LICENSE**: Archivo que especifica los términos y condiciones bajo los cuales el software de este repositorio puede ser utilizado, copiado, modificado o distribuido por otras personas.

- **package-lock.json**: Archivo que asegura la reproducibilidad y consistencia de las instalaciones de paquetes en el proyecto con Node.js.

- **package.json**: Archivo de configuración de npm que describe el proyecto, incluyendo metadatos como nombre, versión, descripción, scripts, dependencias y más.

- **README.md**: Archivo guía para entender y comenzar a trabajar con este proyecto.

## Rutas de la API

Para poder comprobar la funcionalidad de cada ruta de la API vamos a utilizar la extensión `REST Client` del marketplace de Visual Studio Code o cualquier otra herramienta que tenga como finalidad el testeo de una API, como puede ser `Postman`.

> [!TIP]
> Los links de descarga se encuentran en [Recursos](#recursos-).

Dentro del archivo `api.http` (archivo funcional si utilizamos `REST Client`) se van a encontrar rutas con las siguientes finalidades:

| PETICIÓN | URL | DESCRIPCIÓN |
|:--------:|-----|-------------|
| **GET** | `/` | Ruta principal (Devuelve un mensaje de bienvenida y un poco de información sobre la API). |
| **GET** | `/nombres-rankings` | Ruta para devolver todos los nombres de los rankings disponibles. |
| **GET** | `/ranking` | Ruta para buscar un ranking completo por su nombre (se debe incluir el parámetro `nombre` en la query string). |
| **GET** | `/ranking/:nombre/top` | Ruta para devolver el "top" de un ranking (No devuelve menciones honorificas). Se puede especificar un límite de resultados mediante un parámetro opcional `limite` en la query string (por defecto, se devuelve el top 5). |

## Ejemplos de uso 🧪:
!!! ! ! ! ACTUALIZARLO COMO HICE EN EL PROYECTO MYSQL !!!
! ! !         ! !   ! !        !       !      !
 !            !      !        !      !          !      !
  !         !          !         !      !          !



> [!NOTE]
> Estas acciones se realizan en el archivo `api.http`. Cabe aclarar que el puerto puede variar según su configuración; en este caso, se está utilizando el 3000.

**GET**: Entramos a la ruta principal.

```json

GET http://localhost:3000/

```

_Respuesta esperada: Mensaje de bienvenida y descripción de la API._

**GET**: Devolvemos todos los nombres de los rankings disponibles.

```json

GET http://localhost:3000/nombres-rankings
```

_Respuesta esperada: Lista de nombres de rankings en formato JSON._

**GET**: Buscamos un ranking completo por su nombre.

Acá algunos ejemplos con los rankings "10 TRAILERAZOS", "10 COMIDAS DE GIRA" y "10 COMEDIAS +18":

```json

GET http://localhost:3000/ranking/?nombre=10%20TRAILERAZOS

```

```json

GET http://localhost:3000/ranking/?nombre=10%20COMIDAS%20DE%20GIRA

```

```json

GET http://localhost:3000/ranking?nombre=10%20COMEDIAS%20%2B18

```

_Como podemos observar los espacios en una URL se codifican como "%20" y el signo "+" se codifica como "%2B"._

**GET**: Devolvemos el "top" de un ranking. El usuario puede establecer el limite de registros a devolver que desee. <br>

Para obtener el Top 5 (por defecto):

```json

GET http://localhost:3000/ranking/10 TRAILERAZOS/top

```

```json

GET http://localhost:3000/ranking/10 COMIDAS DE GIRA/top

```

```json

GET http://localhost:3000/ranking/10 COMEDIAS +18/top

```

_En esta ruta no es necesario utilizar el "%20" para los espacios ni el "%2B" para el "+", simplemente escribimos correctamente el nombre del ranking._

Para obtener el Top 3:

```json

GET http://localhost:3000/ranking/10 TRAILERAZOS/top?limite=3

```

```json

GET http://localhost:3000/ranking/10 COMIDAS DE GIRA/top?limite=3

```

```json

GET http://localhost:3000/ranking/10 COMEDIAS +18/top?limite=3

```

_Respuesta esperada: Lista de los elementos del top especificado en formato JSON._

## Recursos 🧰
!!! ACA TENDRE QUE AGREGAR SWAGGER Y TODA LA WEAAA DE ESA TECNOLOGIA!!
1! ! ! ! !  !! fIJARSE EN EL PROYECTO N2 MYSQL
 ! ! !              !        ! ! !!       !!  ! !           !  ! ! !
  ! ! ! ! !  
Aquí encontrarás enlaces útiles para aprender más sobre las tecnologías utilizadas en este proyecto:

### Entorno de Desarrollo

- **Visual Studio Code**: [Visual Studio Code](https://code.visualstudio.com/) - Un editor de código fuente popular que ofrece extensiones útiles para desarrollo web.

### Tecnologías de Backend

- **Node.js**: [Node.js](https://nodejs.org/) - Un entorno de ejecución para JavaScript en el lado del servidor.
- **Express**: [Express](https://expressjs.com/) - Un marco de aplicación web para Node.js, diseñado para construir aplicaciones y APIs web.
- **Morgan**: [Morgan](https://www.npmjs.com/package/morgan) - Middleware para registrar solicitudes HTTP en Node.js.

### Bases de Datos

- **MongoDB**: [MongoDB](https://www.mongodb.com/es) - Base de datos NoSQL orientada a documentos.
- **MongoDB Compass**: [MongoDB Compass](https://www.mongodb.com/products/tools/compass) - Herramienta de GUI para interactuar con bases de datos MongoDB.

### Modelado de Datos

- **Mongoose**: [Mongoose](https://mongoosejs.com/) - Biblioteca de modelado de objetos para MongoDB y Node.js.

### Herramientas de Prueba

- **REST Client**: [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) - Extensión de VS Code para probar APIs directamente desde el editor.
- **Postman**: [Postman](https://www.postman.com/) - Herramienta para realizar pruebas y desarrollo de APIs.
