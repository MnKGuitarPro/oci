# Instancias Virtuales

## Creación

1. En el menú de la esquina superior izquierda, ir a `Recursos Informáticos` y luego a `Instancias`
    <ol type="a">
        <li><b>Nota</b>: Para cambiar el idioma de la interfaz, se debe ir a la esquina superior derecha, al ícono del globo terráqueo, y seleccionando posteriormente el idioma Español de la lista. En esta documentación haré referencias a los nombres de los servicios en Español, así que puede ser una buena idea tener dicho idioma para poder ubicarnos tanto en la interfaz, como en los servicios referenciados</li>
    </ol>
2. Daremos clic en el botón azul que indica `Crear instancia`

Antes de crear la instancia, naveguemos por algunas de las opciones que hay disponibles. De esta forma, podemos ver posibles **requisitos** que debamos tener resueltos para poder llevar a cabo la creación de nuestra instancia. Entre los elementos a definir para la creación de una instancia, tenemos:

- Nombre
- Selección de `Compartimento`
- Selección de `Imagen o sistema operativo`
- Selección del `Dominio de disponibilidad`
- Selección de la `Unidad`
- Características de la `Red`
    - `Compartimento` de la `Red Virtual en la Nube`
    - La `Red Virtual en la Nube` en específico
    - El `Compartimento` de `Subred`
    - Posible selección de `Grupos de Seguridad`
    - Posible asignación de `IP Pública`
- Características del `Volumen de Inicio`
    - Posible tamaño del `Volumen de Inicio`
    - Posible `Cifrado` para los datos en `tránsito`
    - Posible `Cifrado` del volumen
- Uso de `Claves SSH`
- Definición de un conjunto de `Opciones Avanzadas`
    - Características de `Gestión`
        - Selección de un `Dominio de Errores`
        - Selección de un `Script de Inicialización`
        - Posible selección de `Supervisión` de `Oracle Cloud Agent`
        - Posible selección de `Gestión` de `Oracle Cloud Agent`
        - Posibles `Etiquetas` en un posible `Espacio de nombres`
    - Características de `Red`
        - Dirección `IP` Privada
        - Nombre de `Host`
        - Opciones de inicio
    - Características de la `Imagen`
        - Compilación de la Imagen
    Características del `Host`
        - Inicio en un Host Dedicado

Notamos que hay algunos elementos que hacen referencia a características propias de la instancia virtual (su sistema operativo, o el volumen de inicio) y otras características que hacen referencia a **otros servicios**, por lo que recomiendo tener primero resueltos y configurados dichos requisitos o dependencias, los cuales son:

- [Un `Espacio de nombres` para `Etiquetas`](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md)
    - [`Etiquetas`](https://github.com/MnKGuitarPro/oci/blob/master/tag-namespace/tag-namespace.md#creaci%C3%B3n-de-etiquetas)
- [Un `Compartimento`](https://github.com/MnKGuitarPro/oci/blob/master/compartment/compartment.md)
- Una `Red Virtual en la Nube`
    - Una `Subred`
    - Un `Grupo de Seguridad`