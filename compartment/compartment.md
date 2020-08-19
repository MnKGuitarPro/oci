# [Compartimentos](https://docs.cloud.oracle.com/en-us/iaas/Content/GSG/Concepts/settinguptenancy.htm#Setting_Up_Your_Tenancy)

## Utilidad

- Cuando se levanta una infraestructura en la nube, siempre hay que tener en mente los conceptos de Gobierno, orden, control y monitoreo. Una forma de fomentar el orden y el Gobierno, es la separación de los recursos utilizando diferentes `Compartimentos`, de manera tal que se generen grupos lógicos aislados de recursos, los cuales se pueden ordenar jerárquicamente

## Creación

1. En el menú de la esquina superior izquierda, ir a `Identidad` y luego a `Compartimentos`
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo, y seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>
    <span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/language-01.png alt="drawing" width="300"/></span>
    <span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-01.png alt="drawing" width="300"/></span>
2. Daremos clic en el botón azul que indica `Crear compartimento`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-02.png alt="drawing" width="700"/></span>

3. Se abrirá un formulario solicitará tres datos básicos:
    - **Nombre**: Debemos poner un nombre descriptivo al compartimento que haga referencia a su objetivo. Puede ser orientado a un grupo de usuarios que harán uso de recursos específicos (como `DBA` o `SysAdmin`), o bien un compartimento para un proyecto específico de manera tal que todos los recursos asociados a dicho proyecto queden agrupados bajo un mismo grupo (pudiendo tener el nombre de `Proyecto A` por ejemplo)
    - **Descripción**: Un texto que describa al compartimento. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos uno o dos compartimentos, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchos compartimentos, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo
    - **Compartimento principal**: Debemos seleccionar el compartimento al cual se anidará el que estamos creando. Todos los recursos pertenecen a un compartimento, incluídos los compartimentos, los cuales pertenecen como mínimo al compartimento raíz. Hay que pensar en los compartimentos como una estructura de carpetas del Sistema Operativo de nuestro computador. Podemos tener todos nuestros archivos en una única carpeta, o bien podemos separalos por imágenes, documentos, etc. Con la nube ocurre algo similar, donde podemos tener todos nuestros recursos en un único compartimento (el raíz) o bien podemos ordenarlos de forma que tenga sentido, en diversos compartimentos. Para este ejemplo, crearé un compartimento denominado `Pruebas` dentro de un compartimento existente llamado `SysAdmin`, de manera tal que me sirve para alojar todos los recursos que gestione esa área de la organización y haga referencia a que dentro de él existirán recursos que servirán para fines exploratorios o de pruebas

4. Una vez completo el formulario, dar clic en el botón azul que dice `Crear compartimento`
<span style="display:block;text-align:center"><img src=https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-03.png alt="drawing" width="300"/></span>