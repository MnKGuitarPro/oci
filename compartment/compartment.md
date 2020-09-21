# [Compartimentos](https://docs.cloud.oracle.com/en-us/iaas/Content/GSG/Concepts/settinguptenancy.htm#Setting_Up_Your_Tenancy)

## Utilidad

- Cuando se levanta una infraestructura en la nube, siempre hay que tener en mente los conceptos de gobierno, orden, control y monitoreo. Una forma de fomentar el orden y el gobierno, es la separación de los recursos utilizando diferentes `Compartimentos`, de manera tal que se generen grupos lógicos aislados de recursos, los cuales se pueden ordenar jerárquicamente
- En esta guía, veremos cómo crear un `Compartimento`, para que a partir de él podamos crear una infraestructura compuesta de diferentes servicios según nuestra necesidad específica

## Creación

1. En el menú de la esquina superior izquierda, ir a `Identidad` y luego a `Compartimentos`, como se indica en la *Fig. 01*
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo (como se muestra en la <i>Fig. 02</i>), seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>

<p align="center"><img width="450" src="https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-01.png"></p>
<p align="center"><em>Fig. 01 - Acceso a la creación de compartimentos</em></p>

<p align="center"><img width="300" src="https://s3.amazonaws.com/dpavezs.image/oci/github/language-01.png"></p>
<p align="center"><em>Fig. 02 - Cambiando idioma de la interfaz</em></p>

2. Daremos clic en el botón azul que indica `Crear compartimento`, como se muestra en la *Fig. 03*

<p align="center"><img width="700" src="https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-02.png"></p>
<p align="center"><em>Fig. 03 - Creación de compartimento</em></p>

3. Se abrirá un formulario que solicitará tres datos básicos:
    - **Nombre**: Debemos poner un nombre descriptivo al compartimento que haga referencia a su objetivo. Puede ser orientado a un grupo de usuarios que harán uso de recursos específicos (como `DBA` o `SysAdmin`), o bien un compartimento para un proyecto específico de manera tal que todos los recursos asociados a dicho proyecto queden agrupados bajo un mismo grupo lógico (pudiendo tener el nombre de `Proyecto A`, por ejemplo)
    - **Descripción**: Un texto que describa al compartimento. Generalmente no se suele utilizar este tipo de campos, pero yo recomiendo su uso, ya que si tenemos uno o dos compartimentos, tal vez el nombre sea suficiente para identificar su función o contenido, pero cuando tenemos muchos compartimentos, se vuelve compleja su administración si no tenemos una descripción clara de cuál es su objetivo. Esto va de la mano con la unidad mínima, o especificidad con la cual se necesite segregar los recursos en la nube (puede ser a nivel de área, de jefatura, de proyectos u otra)
    - **Compartimento principal**: Debemos seleccionar el compartimento al cual se anidará el que estamos creando (será "hijo" del compartimento que seleccionemos). Todos los recursos pertenecen a un compartimento, incluídos los compartimentos, los cuales pertenecen como mínimo al compartimento raíz. Hay que pensar en los compartimentos como una estructura de carpetas del Sistema Operativo de nuestro computador. Podemos tener todos nuestros archivos en una única carpeta, o bien podemos separalos por: imágenes, documentos, etc. Con la nube ocurre algo similar, pues podemos tener todos nuestros recursos en un único compartimento (el raíz) o bien podemos ordenarlos de forma que tenga sentido, en diversos compartimentos. Para este ejemplo, crearé un compartimento denominado `Pruebas` dentro de un compartimento existente llamado `SysAdmin`, de manera tal de que sirva para alojar en él todos los recursos que gestione esa área de la Organización y haga referencia a que dentro de él existirán recursos que servirán para fines exploratorios o de pruebas

4. Una vez completo el formulario, dar clic en el botón azul que dice `Crear compartimento`, como se indica en la *Fig. 04*

<p align="center"><img width="500" src="https://s3.amazonaws.com/dpavezs.image/oci/github/compartment-03.png"></p>
<p align="center"><em>Fig. 04 - Formulario de creación de compartimentos</em></p>