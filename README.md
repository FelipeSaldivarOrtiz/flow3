# Flow3 Panel de control con nodos Dashboard
Repositorio para el tercer flow con NodeRed del Diplomado


# Descripcion
En este ejerciocio aprenderás a instalar nodos nuevos y a desplegar la información procesada por Node-Red en un portal web. El ejercicio parte de dónde termina el Ejercicio – Nodo Function. Si no lo tienes lo puedes descargar de nuestro GitHub: https://github.com/codigo-iot/Flow2-NodeRed


El punto de partida será el flow de la siguiente imagen:
![](flow3/figura1.png)

# Preparacion

Inicia el contenedor de docker que contiene a Node-Red con el comando:
docker start [id_del_contenedor_de_node_red]

Reemplaza la id_del_contenedor con la del contenedor correspondiente a Node-Red. Si no recuerdas cuál es puedes usar el siguiente comando para ver todos los contenedores.

docker ps -a

Nota: Si instalaste el contenedor de acurdo con el ejercicio Creación de una Aplicación Multi-Contenedor con Docker la Id será algo como: dockercompose-nodered-1

Una vez arrancado Node-Red abre un navegador y entra a la URL localhost:1880

# Instalacion de los nodos Dashboard
## Abrir el gestor de paletas

Da click en el menú que se encuentrá junto al botón deploy para abrir las opciones de configuración y escoge la opción Manage Palette.

![](flow3/figura3.png)

### Instalar Dashboard

Una vez abierto el gestor de paletas selecciona la pestaña __Install (1)__ y en la barra de __búsqueda (2)__ escribe la palabra dashboard . De las opciones disponibles busca __node-red-dashboard (3)__ y da click en el botón __Install (4)__. 

![](flow3/figura4.png)

Si te aparece una advertencia da click en _Install_.

Una vez instalados los nodos cierra el gestor de paletas dando click en el botón Close.

Si navegas hasta la parte inferior de la biblioteca de paletas verás los nodos Dashboard.

# Pestañas

 Los nodos Dahboard necesitan una página web donde mostrarse. Para lograr esto es necesario definir una pestaña y un grupo. La pestaña es la página donde se mostrará la información y el grupo es la sección dentro de la página donde se mostrará.

Para definir pestañas y grupos es necesario entrar a la configuración del Dashboard. Da click en el menú junto al botón deploy y slecciona view→Dashboard.

![](flow3/figura5.png)

Verás que en el panel de información de la derecha ahora aparece el menú __dashboard__ con la pestaña __Layout__ seleccionada. Da click en el botón + tab para añadir una pestaña nueva. 

![](flow3/figura6.png)

Da click en el botón edit junto a la pestaña nueva (Tab 1) para abrir su configuración. Verás las siguientes opciones:

- __Name:__ El nombre de la pestaña como aparecerá en el menú

- __Icon__: El tipo de ícono que mostrara

- __State__: Activa o desactiva la pestaña

- __Nav. Menu__: Muestra o esconde la pestaña en el menú de navegación.

Camia el campo de Name para que diga *Fecha* y cierra la configuración dando click en _*Update*_.

![](flow3/figura7.png)

# Grupos

 Ya que tenemos una página (o pestaña) creada necesitamos agregar un grupo o sección. En este ejercicio sólo necesitamos un contenedor para el elemento que mostrará la fecha.

Ubica la configuración de dashboard en el panel de información de la derecha y coloca el cursor sobre la pestaña fecha. Verás que aparecen tres opciones: + __group__, __edit__ y __layout__. Selecciona __+group__. 
![](flow3/figura8.png)

Verás que se crea el grupo Group 1. Coloca el cursor sobre esta opción y da click en el botón edit. Se abrirá la configuración del grupo y verás las siguientes opciones:

- __Name__: El nombre del grupo.

- __Tab__: En que pestaña debe de aparecer el grupo

- __Class__: La clase CSS que debe darle estilo al grupo

- __Width__: El ancho del grupo en la pantalla.

- __Display group name__: Mostrar o esconder el nombre del grupo en la interfaz

- __Allow group to be collapsed__: Permite colapsar y expandir los elementos del grupo.

Cambia el nombre del grupo a Fecha y hora.
![](flow3/figura9.png)

# Nodo Texto

Ya que tenemos configurados la pestaña y el grupo podemos agregar componentes a nuestro grupo. De la sección dashboard de la biblioteca de paletas arrastra un nodo _text_ (no confundir con __text input__) y conecta su entrada a la salida del nodo __function__.
![](flow3/figura10.png)

Verás que el nodo tiene un triángulo anaranjado encima, esto indica que está incompleta su configuración. Da dobel click sobre el nodo para abrir sus opciones. Verás lo siguiente:

- Group: Permite seleccionar el grupo al que pertenece este objeto. La pestaña a la que pertenece el grupo se muestra entre paréntesis cuadrados con el formato [Pestaña] Grupo.

- __Size__: Tamaño del elemento dentro del grupo.

- __Label__: Encabezado que se mostrará acompañando a los datos

- __Value format__: Permite definir qué datos mostrar

- __Layout__: Controla como se acomodarán el encabezado y los datos recibidos.

- __-Class__: La clase CSS que debe darle estilo al grupo

- __Name__: Nombre del nodo que se mostrará en el editor visual

Cambia el valor de Label para que diga Actual: y el valor de Layout a la opción que tiene el label arriba de value. Da click en el botón Done al terminar.
![](flow3/figura11.png)

# Deploy y resultados

Es hora de dar click en el botón __deploy__. Si revisas la consola de depuración (ícono de insecto) verás que se sigue mostrando la fecha y hora en formato legible. Para ver el tablero que creamos navega a [](localhost:1880/ui). Verás la interfaz que configuramos con el nombre de la pestaña arriba a la izquierda y el grupo en el centro de la pantalla.

![](flow3/resultado.png)