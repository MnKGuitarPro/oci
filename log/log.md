# *Log*

## Utilidad

- Cuando creamos una infraestructura *cloud*, debemos tener presente conceptos como gobierno y monitoreo. Esto se logra implementando procesos Corporativos de segregación funcional, de forma que se tenga claridad sobre los roles y perfiles que interactúan con los recursos de la nube
- En esta guía nos enfocaremos en la creación y revisión de *logs* para efectos de auditoría, de manera tal que podamos tener acceso a reportes en caso de ser necesario

## Configuración

1. En el menú de la esquina superior izquierda, ir a `Identidad` y luego a `Grupos`, como indica la *Fig. 01*
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo (como se muestra en la <i>Fig. 02</i>), seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>

<p align="center"><img width="450" src=""></p>
<p align="center"><em>Fig. 00 - desc</em></p>

<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/log-01.png"></p>
<p align="center"><em>Fig. 01 - Menú para la creación de un grupo</em></p>

<p align="center"><img width="300" src="https://s3.amazonaws.com/dpavezs.image/oci/github/language-01.png"></p>
<p align="center"><em>Fig. 02 - Cambiando idioma de la interfaz</em></p>

2. Daremos clic en el botón azul que indica `Crear Grupo`, como se muestra en la *Fig. 03*

<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/log-02.png"></p>
<p align="center"><em>Fig. 03 - Creación de grupo</em></p>

3. Se abrirá un formulario que solicitará dos datos básicos, como muestra la *Fig. 04*:
    - **Nombre**: Debemos poner un nombre descriptivo al grupo, de manera que represente el objetivo de la creación del mismo. En nuestro caso, el grupo puede llamarse: `Auditor`
    - **Descripción**: Un texto que describa al grupo. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos uno o dos grupos, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchos grupos, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo. Para este ejemplo, el grupo llevará la descripción: `Grupo que mantiene al conjunto de usuarios auditores de la infraestructura`
4. Además, el formulario nos permite agregar [etiquetas](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md#creaci%C3%B3n-de-etiquetas) que pertenezcan, o no, a un [espacio de nombres para etiquetas](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md). Para nuestro ejemplo, utilizaremos etiquetas creadas previamente y pertenecientes a un espacio de nombres creado y descrito en la siguiente guía:
    - [Cómo crear un espacio de etiquetas con etiquetas](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md#creaci%C3%B3n-de-etiquetas)

<p align="center"><img width="700" src="https://s3.amazonaws.com/dpavezs.image/oci/github/log-03.png"></p>
<p align="center"><em>Fig. 04 - Formulario de creación de grupo</em></p>

5. Con el grupo ya creado, lo siguiente es crear una política de IAM. Para ello, vamos a menú de la esquina superior izquierda, luego a `Identidad` y luego a `Políticas`, como muestra la *Fig. 05*

<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/log-04.png"></p>
<p align="center"><em>Fig. 05 - Ir al menú de creación de políticas</em></p>

6. Luego, dar clic en el botón azul que indica `Crear política`, como se muestra en la *Fig. 06*

<p align="center"><img width="600" src="https://s3.amazonaws.com/dpavezs.image/oci/github/log-05.png"></p>
<p align="center"><em>Fig. 06 - Creación de política</em></p>

7. Se abrirá un formulario que solicitará cinco datos básicos:
    - **Nombre**: Debemos poner un nombre descriptivo a la política, de manera que represente el objetivo de la creación de la misma. En nuestro caso, la política puede llamarse: `Visualizar_Log_de_Eventos`
    - **Descripción**: Un texto que describa a la política. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos una o dos políticas, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchas políticas, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo. Para este ejemplo, la política llevará la descripción: `Política que permite la visualización del log de eventos para efectos de auditoría`
    - **Versionamiento**: Nos ofrece dos opciones, las cuales son `MANTENER POLÍTICA ACTUALIZADA` y `USAR FECHA DE VERSIÓN`. Si seleccionamos la mantención de la política actualizada, el nombre se conservará en caso de que en el futuro decidamos modificar las características de la política. Si seleccionamos usar fecha de versión, cada vez que hagamos una modificación a la política un atributo de la misma llamado `Fecha de versión` se actualizará con el valor correspondiente. Para mantener un orden, recomiendo la opción de uso de fecha de versión, pues agrega mayor información a nuestro recurso
    - **Compartimento**: Debemos seleccionar el compartimento dentro del cual se podrá utilizar la política. Para este ejemplo se utilizará el compartimento `raíz`, pero es importante destacar que se puede seleccionar cualquiera de los existentes, y que la política sólo se podrá utilizar dentro de ese compartimento, y en los compartimentos "hijos" del compartimento seleccionado. Como en este caso seleccioné el `raíz`, podré utilizar esta política en **todos** mis compartimentos y sub-compartimentos del `Arrendamiento` (se recomienda esta alternativa para la creación de políticas genéricas o que podrían necesitarse en cualquiera de nuestros recursos)
    - **Sentencia de política**: La sentencia de la política, corresponde a la regla que estamos definiendo que afecta directamente uno o más recursos. Su sintaxis suele tener la siguiente forma: `Allow group [group_name] to [verb] [resource-type] in compartment [compartment_name] where [condition]`. Para mayor información sobre la sintaxis, recomiendo revisar la documentación oficial [en el siguiente enlace](https://docs.cloud.oracle.com/en-us/iaas/Content/Identity/Concepts/policysyntax.htm#three). Para nuestro ejercicio, necesitamos crear la siguiente sentencia (cambiando adecuadamente a `<nuestroGrupo>` por el nombre del grupo que hemos creado previamente con este objetivo):
        ```bash
        Allow group <nuestroGrupo> to read audit-events in tenancy
        ```

8. Además, si damos clic al texto que indica `Mostrar opciones avanzadas` nos permite agregar etiquetas que pertenezcan, o no, a un [`espacio de nombres` para `etiquetas`](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md), lo cual recomiendo para mantener descritos de forma completa nuestros recursos.

9. Una vez que tengamos toda la información ya disponible, daremos clic en el botón azul que indica `Crear`

<p align="center"><img width="450" src=""></p>
<p align="center"><em>Fig. 00 - desc</em></p>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/log-06.png alt="drawing" width="700"/></span>

## Resultado

- Una vez se ha realizado la configuración, se puede ir al menú de la esquina superior izquierda, ir a `Identidad` y luego a `Auditoría`. En la interfaz se puede ver el detalle de eventos correspondiente a su: hora de realización, usuario relacionado al evento, origen, nombre, recurso asociado, tipo de acción y respuesta. Además, se puede filtrar por fecha de inicio y término de los eventos ocurridos, palabras clave y tipo de acción. De utilizar algún filtro, debemos luego presionar el botón azul que indica `Buscar`.

<p align="center"><img width="450" src=""></p>
<p align="center"><em>Fig. 00 - desc</em></p>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/log-07.png alt="drawing" width="500"/></span>
<p align="center"><img width="450" src=""></p>
<p align="center"><em>Fig. 00 - desc</em></p>
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/log-08.png alt="drawing" width="800"/></span>