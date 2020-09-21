# Espacio de Nombres de Etiquetas

## Utilidad

- Como bien se describe en la [documentación oficial](https://docs.cloud.oracle.com/es-ww/iaas/Content/Tagging/Concepts/taggingoverview.htm), las etiquetas corresponden a un par `clave - valor` útil a la hora de describir y ordenar nuestros recursos en la nube, permitiéndonos además analizar los costos e incluso gestionar accesos
- Podemos utilizar etiquetas para identificar Proyectos entre sí, responsables y/o ambientes. En esta guía veremos cómo sacarle el mejor provecho a esta característica, que a veces es dejada de lado

## Creación del espacio de nombres

1. En el menú de la esquina superior izquierda, ir a `Control` y luego a `Espacios de nombres de etiquetas`, como se muestra en la *Fig. 01*
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo (como se muestra en la <i>Fig. 02</i>), seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-01.png"></p>
<p align="center"><em>Fig. 01 - Acceso al Espacio de nombres de etiquetas</em></p>

<p align="center"><img width="300" src="https://s3.amazonaws.com/dpavezs.image/oci/github/language-01.png"></p>
<p align="center"><em>Fig. 02 - Cambiando idioma de la interfaz</em></p>

2. Daremos clic en el botón azul que indica `Crear definición de espacio de nombres`, como se muestra en la *Fig. 03*

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-02.png"></p>
<p align="center"><em>Fig. 03 - Acceso a creación de definición de espacio de nombres</em></p>

3. Se abrirá un formulario que solicitará tres datos básicos:
    - **Compartimento**: Debemos seleccionar el compartimento dentro del cual se podrá utilizar el espacio de nombres (y por ende, las etiquetas que en él se generen). Para este ejemplo se utilizará el compartimento `raíz`, pero es importante destacar que se puede seleccionar cualquiera de los existentes, y que el espacio de nombres sólo se podrá utilizar dentro de ese compartimento, y en los compartimentos "hijos" del compartimento seleccionado. Como en este caso seleccioné el `raíz`, podré utilizar este espacio de nombres en **todos** mis compartimentos y sub-compartimentos del `Arrendamiento` (se recomienda esta alternativa para la creación de etiquetas globales o que deben estar presentes en todos nuestros recursos)
    - **Nombre**: Debemos poner un nombre descriptivo al espacio de nombres, de las etiquetas que estarán en su interior. Por ejemplo, algunos nombres útiles pueden ser:
        - `mi_proyectoA` (para hacer referencia a un Proyecto específico)
        - `System_Administrators` o `SysAdmin` (para hacer referencia a un grupo o área dentro de la Organización)
        - `Database_Administrators` o `DBA` (para hacer referencia a un rol o grupo de usuarios dentro de la Organización)
    - **Descripción**: Un texto que describa al espacio de nombres. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos uno o dos espacios de nombres, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchos espacios de nombres, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo. En la *Fig. 04* se visualiza el formulario con algunos datos de prueba para este ejercicio

<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-03.png"></p>
<p align="center"><em>Fig. 04 - Formulario de creación de espacio de nombres</em></p>

4. Es importante destacar que un espacio de nombres puede llevar etiquetas que existan en otro espacio de nombres, o incluso en ninguno (ser etiquetas de libre formato). Sin embargo, mi recomendación para la gestión de servicios en la nube es siempre llevar un orden y documentación de **qué** estamos creando y **para qué** lo estamos creando. De esta forma evitamos encontrarnos con recursos que no sabemos por qué están en nuestra arquitectura de nube, o quién fue el responsable de la aprobación de la creación de determinado recurso

5. Si ya completamos el formulario, sólo debemos dar clic al botón azul que indica `Crear definición de espacio de nombres`, como se ve en la *Fig. 05*
    - Una vez tengamos creado nuestro espacio de nombres, sólo queda crear en él algunas etiquetas de utilidad

<p align="center"><img width="400" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-04.png"></p>
<p align="center"><em>Fig. 05 - Creación del nuevo espacio de nombres</em></p>

## Creación de etiquetas

1. Para crear etiquetas dentro de un espacio de nombres, primero debemos seleccionar el espacio de nombres dentro del cual crearemos las etiquetas. Para este ejemplo, utilizaré el espacio de nombres llamado `mi_espacio_de_nombres` creado anteriormente dando clic en él como se ve en la *Fig. 06*

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-05.png"></p>
<p align="center"><em>Fig. 06 - Selección del espacio de nombres dentro del cual crearemos nuestras etiquetas</em></p>

2. Veremos que se abre una ventana con los detalles del espacio de nombres, donde tenemos varias funcionalidades e información, como por ejemplo:
    - Un botón para `Agregar etiquetas` (como se ve en la *Fig. 07*)
    - Un botón para `Mover espacio de nombres de etiqueta` del compartimento al cual pertenece, a otro compartimento existente  (como se ve en la *Fig. 07*)
    - Un botón para `Retirar espacio de nombres`, dejándolo así inválido  (como se ve en la *Fig. 07*)
    - Una pestaña donde podemos revisar su `Descripción`, `OCID`, `Número de etiquetas de seguimiento de costos`, el `Compartimento` al cual pertenece y la fecha y hora de `Creación` (como se ve en la *Fig. 07*)
    - Una pestaña donde podemos ver las `Etiquetas` (como se ve en la *Fig. 08*) que tiene el mismo espacio de nombres asociadas a él o que lo describen (no confundir con las etiquetas que el espacio de trabajo contiene)
    - Abajo, una sección para la gestión de etiquetas que el espacio de nombres contendrá (como se ve en la *Fig. 09*), donde contamos con:
        - Un botón para `Crear definición de clave de etiqueta` que nos permitirá crear las etiquetas
        - Una vez seleccionada una o varias etiquetas, un botón para que el usuario `Retire` o desactive dicho conjunto de etiquetas seleccionadas
        - Una vez seleccionada una o varias etiquetas desactivadas, un botón para `Reactivate` o reactivar dicho conjunto de etiquetas seleccionadas
        -  Una vez seleccionada una o varias etiquetas desactivadas, un botón para `Suprimir` o eliminar dicho conjunto de etiquetas seleccionadas

<p align="center"><img width="800" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-06.png"></p>
<p align="center"><em>Fig. 07 - Acciones posibles de ejecutar sobre el espacio de nombres</em></p>

<p align="center"><img width="800" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-07.png"></p>
<p align="center"><em>Fig. 08 - Etiquetas del espacio de nombres</em></p>

<p align="center"><img width="800" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-08.png"></p>
<p align="center"><em>Fig. 09 - Acciones sobre las etiquetas pertenecientes al espacio de nombres</em></p>

3. Al dar clic al botón que indica `Crear definición de clave de etiqueta` se abre un formulario que solicita tres datos clave, como se ve en la *Fig. 10*:
    - **Clave**: Nombre en minúsculas (sin espacios, ni puntuación) de la clave, la cual podrá tener uno o varios valores definidos posteriormente
    - **Descripción**: Un texto que describa a la etiqueta, el cual recomiendo utilizar para facilitar la gestión y uso de múltiples etiquetas pertenecientes a diversos espacios de nombres
    - **Seguimiento de costos**: Si se marca esta opción, se permitirá a los gestores de costos y del *billing* filtrar por los valores de esta etiqueta, facilitando la identifcación de determinados recursos creados en la nube. Se puede crear un total de **diez** etiquetas con esta característica por *tenancy* o arriendo, así que se deben utilizar correctamente
    - **Tipo de valor de etiqueta**: Acá debemos seleccionar entre dos tipos:
        - **Cualquier cadena**: Nos permite escribir libremente un texto que defina el valor para la etiqueta creada
        - **Lista de valores**: Si tenemos un conjunto de valores relativamente fijos para una misma etiqueta, podemos almacenarlos como una lista evitando así escribir valores de forma manual, manteniendo consistencia y orden. Los valores se deben escribir en líneas diferentes

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-09.png"></p>
<p align="center"><em>Fig. 10 - Formulario de creación de una etiqueta</em></p>

4. Una vez se ha descrito una etiqueta y sus valores (en caso de que sea una lista de valores), se debe dar clic al botón que indica `Crear definición de clave de etiqueta`. Para este ejercicio, crearé un conjunto de etiquetas a modo de ejemplo que pueden servir como guía para un escenario real. En las *Fig. 11* a la *Fig. 15* se expone la creación de cada una de las etiquetas mencionadas en la *Tabla 01* a continuación:

|Clave|Descripción|Seguimiento de costos|Tipo de valor de etiqueta|Valores|
|:---:|:---:|:---:|:---:|:---:|
|CeCo|Centro de costos al cual se le cargará o cobrará por el uso del recurso (permite manejo de *budgets*)|☑|Lista de valores|CeCo01, CeCo02, CeCo03|
|Env|Ambiente sobre el cual opera el recurso creado|☑|Lista de valores|Desarrollo, QA, Producción, Todos|
|Gerente|Gerencia responsable del área o las áreas que hacen uso del recurso creado, y que ha autorizado la creación de dicho recurso|☑|Lista de valores|Juan Pérez, María González|
|Proyecto|Proyecto asociado al recurso específico, y que debe tener un budget específico para el costo|☑|Lista de valores|Proyecto A, Proyecto B|
|JP|Jefe de Proyectos asociado al Proyecto que utiliza el recurso, y el cual es responsable tanto por la autorización de creación como del correcto uso del recurso|☐|Lista de valores|Camila Tapia, José Muñoz|
<p align="center"><em>Tabla 01 - Etiquetas propuestas a modo de ejemplo para ambientes reales</em></p>

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-10.png"></p>
<p align="center"><em>Fig. 11 - Creación de la etiqueta para describir al Centro de Costos</em></p>
<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-11.png"></p>
<p align="center"><em>Fig. 12 - Creación de la etiqueta para describir los ambientes</em></p>
<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-12.png"></p>
<p align="center"><em>Fig. 13 - Creación de la etiqueta para describir a Gerentes responsables</em></p>
<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-13.png"></p>
<p align="center"><em>Fig. 14 - Creación de la etiqueta para describir a Proyectos</em></p>
<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-14.png"></p>
<p align="center"><em>Fig. 15 - Creación de la etiqueta para describir a Jefes de Proyecto responsables</em></p>

Se pueden crear las etiquetas que se estimen convenientes, definiéndolas también como se crea adecuado. Por ejemplo, podemos definir una etiqueta `QA` donde listemos a los integrantes del equipo de QA, en caso de que se asocien a los Proyectos. Podemos crear etiquetas de `ScrumMaster` o `Responsable` u otras que nos sirvan para identificar nuestros recursos. Estas podrían no ser de seguimiento de costos, pero ayudan a describir en profundidad nuestros recursos. Recuerda, en principio etiquetar los recursos puede parecer trabajo extra innecesario, pero cuando tienes cientos de instancias virtuales, cientos de balanceadores, y de bases de datos, siempre es grato tener meta-datos adecuados que nos permitan saber qué, por qué y para qué existe determinado recurso

## Gestión de etiquetas

- Con las etiquetas ya creadas, podemos ver que se listan en el espacio de nombres al cual pertenecen. Además, podemos ver atributos como su `Nombre`, `Tipo de valor`, su `Estado` su `OCID`, si tienen o no `Seguimiento de costos` y la fecha y hora de su `Creación`, como se ve en la *Fig. 16*
- Podemos marcar el *checkbox* (☐) de la grilla y poder utilizar las opciones de `Retire`, `Reactive` y `Suprimir`

<p align="center"><img width="800" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-15.png"></p>
<p align="center"><em>Fig. 16 - Acciones y descripción de etiquetas pertenecientes a un espacio de nombres</em></p>

- Podemos seleccionar una etiqueta dando clic en su nombre, lo que nos desplegará una ventana que indicará los valores para dicha etiqueta, y también nos permitirá realizar las funciones de `Editar definición de clave de etiqueta` (donde podemos modificar su nombre, descripción, si aplica o no para seguimiento de costos y sus valores, dando luego clic en el botón `Actualizar`, como se ve en la *Fig. 18*), `Retirar definición de clave de etiqueta`, `Reactivar definición de clave de etiqueta` y `Suprimir definición de clave de etiqueta`, como se ve en las *Fig. 17* y *Fig. 19*

<p align="center"><img width="800" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-16.png"></p>
<p align="center"><em>Fig. 17 - Acciones de edición y retiro de clave de etiqueta</em></p>
<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-17.png"></p>
<p align="center"><em>Fig. 18 - Edición de una etiqueta existente</em></p>
<p align="center"><img width="700" src="https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-18.png"></p>
<p align="center"><em>Fig. 19 - Ejemplo de una etiqueta inactiva y acción de eliminación</em></p>

## [Volver al *home*](https://github.com/MnKGuitarPro/oci)