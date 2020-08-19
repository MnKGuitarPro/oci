# Espacio de Nombres de Etiquetas

## Utilidad

- Como bien se describe en la [documentación oficial](https://docs.cloud.oracle.com/es-ww/iaas/Content/Tagging/Concepts/taggingoverview.htm), las etiquetas corresponden a un par `clave - valor` muy útil a la hora de ordenar nuestros recursos en la nube, analizar los costos e incluso gestionar accesos
- Podemos utilizar etiquetas para identificar Proyectos entre sí, responsables y/o ambientes

## Creación

1. En el menú de la esquina superior izquierda, ir a `Control` y luego a `Espacios de nombres de etiquetas`
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo, y seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/language-01.png alt="drawing" width="300"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-01.png alt="drawing" width="700"/></span>

2. Daremos clic en el botón azul que indica `Crear definición de espacio de nombres`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-02.png alt="drawing" width="700"/></span>

3. Se abrirá un formulario solicitará tres datos básicos:
    - **Compartimento**: Debemos seleccionar el compartimento dentro del cual se podrá utilizar el espacio de nombres (y por ende, las etiquetas que en él se generen). Para este ejemplo se utilizará el compartimento `raíz`, pero es importante destacar que se puede seleccionar cualquiera de los existentes, y que el espacio de nombres sólo se podrá utilizar dentro de ese compartimento, y en los compartimentos "hijos" del compartimento seleccionado. Como en este caso seleccioné el `raíz`, podré utilizar este espacio de nombres en **todos** mis compartimentos y sub-compartimentos del `Arrendamiento` (se recomienda esta alternativa para la creación de etiquetas genéricas o que deben estar presentes en todos nuestros recursos)
    - **Nombre**: Debemos poner un nombre descriptivo al espacio de nombres, de las etiquetas que estarán en su interior. Por ejemplo, algunos nombres útiles pueden ser:
        - `mi_proyectoA`
        - `System_Administrators` o `SysAdmin`
        - `Database_Administrators` o `DBA`
    - **Descripción**: Un texto que describa al espacio de nombres. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos uno o dos espacios de nombres, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchos espacios de nombres, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-03.png alt="drawing" width="500"/></span>

4. Es importante destacar que un espacio de nombres puede llevar etiquetas que existan en otro espacio de nombres, o incluso en ninguno (ser etiquetas de libre formato). Sin embargo, mi recomendación para la gestión de servicios en la nube es siempre ser llevar un orden y documentación de **qué** estamos creando y **para qué**. De esta forma evitamos encontrarnos con recursos que no sabemos por qué están en nuestra arquitectura de nube

5. Si ya completamos el formulario, sólo debemos dar clic al botón azul que indica `Crear definición de espacio de nombres`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-04.png alt="drawing" width="500"/></span>
- Una vez tengamos creado nuestro espacio de nombres, sólo queda crear en él algunas etiquetas de utilidad

## Creación de etiquetas

1. Para crear etiquetas dentro de un espacio de nombres, primero debemos seleccionar el espacio de nombres dentro del cual crearemos las etiquetas. Para este ejemplo, utilizaré el espacio de nombres llamado `mi_espacio_de_nombres` creado anteriormente dando clic en él
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-05.png alt="drawing" width="600"/></span>

2. Veremos que se abre una ventana con los detalles del espacio de nombres, donde tenemos varias funcionalidades e información, como por ejemplo:
    - Un botón para `Agregar etiquetas`
    - Un botón para `Mover espacio de nombres de etiqueta` del compartimento al cual pertenece, a otro compartimento existente
    - Un botón para `Retirar espacio de nombres`, dejándolo así inválido
    - Una pestaña donde podemos revisar su `Descripción`, `OCID`, `Número de etiquetas de seguimiento de costos`, el `Compartimento` al cual pertenece y la fecha y hora de `Creación`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-06.png alt="drawing" width="800"/></span>
    Una pestaña donde podemos ver las `Etiquetas` que tiene el mismo espacio de nombres asociadas a él o que lo describen (no confundir con las etiquetas que el espacio de trabajo contiene)
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-07.png alt="drawing" width="800"/></span>
    - Abajo, una sección para la gestión de etiquetas que el espacio de nombres contendrá, donde contamos con:
        - Un botón para `Crear definición de clave de etiqueta` que nos permitirá crear las etiquetas
        - Una vez seleccionada una o varias etiquetas, un botón para que el usuario `Retire` o desactive dicho conjunto de etiquetas seleccionadas
        - Una vez seleccionada una o varias etiquetas desactivadas, un botón para `Reactivate` o reactivar dicho conjunto de etiquetas seleccionadas
        -  Una vez seleccionada una o varias etiquetas desactivadas, un botón para `Suprimir` o eliminar dicho conjunto de etiquetas seleccionadas
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-08.png alt="drawing" width="800"/></span>

3. Al dar clic al botón que indica `Crear definición de clave de etiqueta` se abre un formulario que solicita tres datos clave:
    - **Clave**: Nombre en minúsculas (sin espacios, ni puntuación) de la clave, la cual podrá tener uno o varios valores definidos posteriormente
    - **Descripción**: Un texto que describa a la etiqueta, el cual recomiendo utilizar para facilitar la gestión y uso de múltiples etiquetas pertenecientes a diversos espacios de nombres
    - **Seguimiento de costos**: Si se marca esta opción, se permitirá a los gestores de costos y del *billing* filtrar por los valores de esta etiqueta, facilitando la identifcación de determinados recursos creados en la nube. Se puede crear un total de **diez** etiquetas con esta característica por *tenancy* o arriendo, así que se deben utilizar correctamente
    - **Tipo de valor de etiqueta**: Acá debemos seleccionar entre dos tipos:
        - **Cualquier cadena**: Nos permite escribir libremente un texto que defina el valor para la etiqueta creada
        - **Lista de valores**: Si tenemos un conjunto de valores relativamente fijos para una misma etiqueta, podemos almacenarlos como una lista evitando así escribir valores de forma manual, manteniendo consistencia y orden. Los valores se deben escribir en líneas diferentes
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-09.png alt="drawing" width="600"/></span>
4. Una vez se ha descrito una etiqueta y sus valores (en caso de que sea una lista de valores), se debe dar clic al botón que indica `Crear definición de clave de etiqueta`. Para este ejercicio, crearé un conjunto de etiquetas a modo de ejemplo que pueden servir como guía:

|Clave|Descripción|Seguimiento de costos|Tipo de valor de etiqueta|Valores|
|:---:|:---:|:---:|:---:|:---:|
|CeCo|Centro de costos al cual se le cargará o cobrará por el uso del recurso (permite manejo de *budgets*)|☑|Lista de valores|CeCo01, CeCo02, CeCo03|
|Env|Ambiente sobre el cual opera el recurso creado|☑|Lista de valores|Desarrollo, QA, Producción, Todos|
|Gerente|Gerencia responsable del área o las áreas que hacen uso del recurso creado, y que ha autorizado la creación de dicho recurso|☑|Lista de valores|Juan Pérez, María González|
|Proyecto|Proyecto asociado al recurso específico, y que debe tener un budget específico para el costo|☑|Lista de valores|Proyecto A, Proyecto B|
|JP|Jefe de Proyectos asociado al Proyecto que utiliza el recurso, y el cual es responsable tanto por la autorización de creación como del correcto uso del recurso|⛝|Lista de valores|Camila Tapia, José Muñoz|
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-10.png alt="drawing" width="600"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-11.png alt="drawing" width="600"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-12.png alt="drawing" width="600"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-13.png alt="drawing" width="600"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-14.png alt="drawing" width="600"/></span>
Se pueden crear las etiquetas que se estimen convenientes, definiéndolas también como se crea adecuado. Por ejemplo, podemos definir una etiqueta `QA` donde listemos a los integrantes del equipo de QA, en caso de que se asocien a los Proyectos. Podemos crear etiquetas de `ScrumMaster` o `Responsable` u otras que nos sirvan para identificar nuestros recursos. Estas podrían no ser de seguimiento de costos, pero ayudan a describir en profundidad nuestros recursos. Recuerda, en principio etiquetar los recursos puede parecer trabajo extra innecesario, pero cuando tienes cientos de instancias virtuales, cientos de balanceadores, y de bases de datos, siempre es grato tener meta-datos adecuados que nos permitan saber qué, por qué y para qué existe determinado recurso

## Gestión de etiquetas

- Con las etiquetas ya creadas, podemos ver que se listan en el espacio de nombres al cual pertenecen. Además, podemos ver atributos como su `Nombre`, `Tipo de valor`, su `Estado` su `OCID`, si tienen o no `Seguimiento de costos` y la fecha y hora de su `Creación`
- Podemos marcar el *checkbox* (☐) de la grilla y poder utilizar las opciones de `Retire`, `Reactive` y `Suprimir`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-15.png alt="drawing" width="800"/></span>
- Podemos seleccionar una etiqueta dando clic en su nombre, lo que nos desplegará una ventana que indicará los valores para dicha etiqueta, y también nos permitirá realizar las funciones de `Editar definición de clave de etiqueta` (donde podemos modificar su nombre, descripción, si aplica o no para seguimiento de costos y sus valores, dando luego clic en el botón `Actualizar`), `Retirar definición de clave de etiqueta`, `Reactivar definición de clave de etiqueta` y `Suprimir definición de clave de etiqueta`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-16.png alt="drawing" width="800"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-17.png alt="drawing" width="500"/></span>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/tag-namespace-18.png alt="drawing" width="800"/></span>