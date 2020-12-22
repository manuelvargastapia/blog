---
title: 'Primera app Flutter: Libgen Mobile'
description: Revisión del proceso de desarrollo de una primera experiencia con Flutter.
featured: primera_app_flutter.png
---

# Primera app Flutter: LibGen Mobile

He desarrollado mi primera aplicación móvil completa (como proyecto propio al menos) y quisiera compartir aquí algunos pensamientos al respecto. Concretamente, en cuanto a mis motivaciones, la planificación del proyecto, las dificultades y aprendizajes obtenidos. La aplicación en cuestión es un cliente móvil para Library Genesis, el conocido y nunca bien ponderado servicio de descarga gratuita de libros, artículos científicos y otros tipos de contenidos bibliográfico. La herramienta escogida para su construcción es Flutter, el nunca bien ponderado SDK multiplataforma para desarrollo nativo.

Aclaro desde ya que no poseo vínculo alguno con Library Genesis. Este es un proyecto completamente independiente. La única función de la app es proveer un acceso sencillo a los datos obtenidos desde LibGen. El proyecto es Open Source (no puede ser de otra forma, pienso). Dejo el link al repositorio de GitHub:

[https://github.com/manuelvargastapia/libgen_mobile_app](https://github.com/manuelvargastapia/libgen_mobile_app)

Adicionalmente, y como explicaré a lo largo del artículo, tuve que desarrollar también una API con ExpressJS. Dejo también el link al repo:

[https://github.com/manuelvargastapia/libgen_api](https://github.com/manuelvargastapia/libgen_api)

No pretendo crear un tutorial detallado, sino más bien describir brevemente el proceso de desarrollo, aunque ocasionalmente mostaré un poco del código con fines explicativos (y estéticos, por qué no, aunque no sea particularmente bonito).

Finalmente, aclarar también que la app sólo está disponible en Android. Aún no se ha publicado oficialmente, pero es cuestión de tiempo para que se agregue a FDroid y quizá también a Play Store. Sin embargo, esto podría no ser posible o conveniente debido a la naturaleza del proyecto. La API, por su parte, se ejecuta en [Heroku](https://dashboard.heroku.com).

<article-img src="/primera-app-fluter/images/home_light.png" alt="Home Light"></article-img>

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608426982.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608426982.png)

![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427039.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427039.png)

![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427049.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427049.png)

![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427057.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427057.png)

![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427060.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608427060.png) -->

MOTIVACIONES

La principal motiviación para desarrollar una app era aumentar mi portafolio personal. O mejor dicho, comenzar uno. Si bien ya cuento con algo de experiencia laboral en el área, no me sentía cómodo al no tener proyectos propios que mostrar. Además, considero que la auto-formación y continuo aprendizaje son fundamentales para casi cualquier área de conocimiento.

Por otro lado, quería profundizar en Flutter, ya que es una solución que me gusta mucho y en la que me gustaría desempeñarme profesionalmente en el corto o mediano plazo. Por este motivo, era la elección obvia para la construcción de la app.

Finalmente, queda la difícil elección de qué tipo de aplicación fabricar. Podría haber sido una TODO list, o alguna de las ideas ofrecidas desinteresadamente por [FireShip](https://www.youtube.com/watch?v=JTOJsU3FSD8). La realidad era que no tenía idea. De algún modo, en algún momento vino a mí la idea de crear Library Genesis móvil, puesto que su interfaz en web siempre me había parecido un poco incómoda, y hasta donde sabía, no contaban con una solución más portatil.

Por supuesto, antes de ahondar en la idea, me aseguré de que no existiera ya una app de LibGen o que al menos no hubiesen demasiadas. Para mi buena o mala suerte, [ya existía una](https://play.google.com/store/apps/details?id=com.kuchro.ebooks.library&hl=es_CL&gl=US), y había varias más en GitHub, aunque sólo esa publicada oficialmente. Eso fue desalentador, pero de todas formas decidí que era buena idea continuar. Después de todo, mi intención era aprender y crear algo completo de principio a fin, y que funcione. Además, no tiene nada de malo que existan múltiples soluciones disponibles al mismo problema.

Finalmente, cabe señalar que aprendí de esos otros intentos, lo cual me permitió prevenir ciertas complicaciones y planificar una solución óptima para la creación de la app. Y así, tocaba resolver el primer problema: cómo obtener libros de Library Genesis, considerando que no ofrecen una API pública.

BACKEND

Después de mucha investigación, me quedaba una [https://garbage.world/posts/libgen/](https://garbage.world/posts/libgen/) para entender cómo obtener datos desde LibGen (además del web scrapping, que de todas formó después parte de la solución, aunque para un objetivo específico). El post explica que LibGen provee un endpoint para el consumo de datos pero no precisamente para realizar búsquedas de modo convencional. Estaba pensado más bien para algún proceso interno. No obstante, la autora del post creó también una [librería NPM](https://www.npmjs.com/package/libgen) para usar dicho endpoint para realizar búsquedas. Esta fue la solución que adopté, no sin antes darle mil y una vueltas a todas las demás alternativas relevantes.

Considerando que se trataba de una librería JS y que mi objetivo era aprender Flutter a toda costa, la opción que consideré interesante y útil para el caso fue construir una API para mi app, que expusiera las funcionalidades de dicha librería. Y eso fue lo que hice, con Node y [ExpressJS](http://expressjs.com).

No estaba en mis planes aprender ExpressJS, pero tampoco es que me molestara, y tampoco parecía demasiado complejo de utilizar. Además, ya conocía y me gustaba Typescript, así que también era una buena oportunidad para practicarlo.

Sin entrar en mayor detalle, esta es la apariencia general del proyecto, después de unas dos o tres semanas de desarrollo:

Los _scripts_ del _package.json_ quedaron así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled.png) -->

- `npm start` ejecutará el archivo _src/app/api.ts_ sin compilar, y usando [nodemon](https://www.npmjs.com/package/nodemon), es posible hacer _live reload_, para editar sin tener que reiniciar la ejecución
- `npm run serve` realiza la misma acción, pero compilando previamente el proyecto (sin el _live reload_)
- `postinstall` es ejecutado por Heroku al momento de realizar el _deploy_. De este modo, el _Procfile_ respectivo contiene la siguiente linea:

  `web: node --optimize_for_size --max_old_space_size=920 --gc_interval=100 dist/src/app/api.js`

Es decir, una vez Heroku compile el proyecto con `postinstall` , se generará una carpeta _dist_, la cual será ejecutada en producción. Para más información sobre el _deploy_ de Node en Heroku, visitar el siguiente [link.](https://devcenter.heroku.com/articles/getting-started-with-nodejs)

Una cosa más respecto a Heroku. Como nada sale bien al primer intento (o al segundo o al décimo), después de un tiempo me di cuenta de que era mala idea seguir actualizando la rama _master_ ([o _main_ de ahora en adelante](https://platzi.com/blog/cambios-en-github-master-main/)) para liberar pequeños cambios para resolver problemas durante la liberación (por ejemplo, un 503 por problemas con CORS que tuve). Fue así que encontré el pplugin [heroku-builds](https://github.com/heroku/heroku-builds), lo que hizo mi vida un poco menos difícil.

Siguiendo con los scripts, aún queda explicar el comando `DEBUG=express,libgen,scrapping`. Se trata de un argumento que utiliza la librería [debug](https://www.npmjs.com/package/debug). Como [buena práctica recomendada por ExpressJS](https://expressjs.com/es/advanced/best-practice-performance.html), decidí usar la librería debug en lugar del clásico `console.log()` para la depuración.

Siguiendo con el _package.json_, estas son algunas de las dependencias que utilicé:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%201.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%201.png) -->

- [@hapi/joi](https://www.npmjs.com/package/joi) es una librería muy interesante que facilita enormemente el trabajo de validar los _query params_ de los endpoints. Usarlo con Typescript resultó en un arma de doble filo, ya que si bien refuerza la estabilidad del código gracias al tipado, también trajo inconvenientes al no tener documentación sobre cómo implementar ciertas funcionalidades, tales como el manejo de errores con la función que dispone ExpressJS. No obstante, al final son más los beneficios, ya que las validaciones funcionan estupendamente y son muy flexibles. Se usa en conjunto con [express-joi-validation](https://www.npmjs.com/package/express-joi-validation).
- [jsdom](https://www.npmjs.com/package/jsdom) y [node-fetch](https://www.npmjs.com/package/node-fetch) son usadas para el web scrapping y así obtener un link de descarga directo de los libros. Si bien la librería base que utilicé puede generar un link de descarga, mi intención era que esta se realizará con un click en la app. Por eso, necesitaba obtener el link asociado al botón de descarga en LibGen.

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%202.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%202.png) -->

En un inicio, obtenía sólo el link en el botón "GET". Pero después me percaté de que habían agregado algunas otras opciones. Gracias a ello, las descargas desde la app toman uno o dos segundos, ya que el servidor de Cloudflare, por ejemplo, es muy rápido.

Para terminar, cabe destacar que, tal como se en la lista de dependencias, no estoy usando la librería base como tal, sino más bien un _fork_ que tuve que hacer para implementar el filtrado por campos (y así filtrar adecuadamente la información obtenida). Dejo el [link](https://github.com/manuelvargastapia/libgen.js) al repo.

Consumir datos de LibGen fue complejo. Más que nada porque no había suficiente información, y en gran medida, dependí mucho del ensayo y error para obtener una visión clara de qué datos realmente me estaba entregando, su estructura, o si faltaba alguno. Por ejemplo, no lograba entender de dónde obtenían las descripciones y las tablas de contenido de los libros para mostrarlos en su página. Se me había ocurrido obtener esos datos con la API de GoogleBooks, por ejemplo, a través del ISBN. Por suerte, había dos campos en la respuesta de la API que no estaban documentados en la librería base o en el post original del endpoint de LibGen antes mencionado, a saber, _desc_ y _toc_. Con eso ya pude obtener todo y sentirme más confiado (aún con algunas precauciones) respecto a qué estoy consumiendo. Pero es momento de hablar de la app propiamente tal.

MÍNIMO PRODUCTO VIABLE

Para evitar caer en el pozo sin fondo de proyectos no terminados, me propuse definir lo más claro posible una lista mínima de requerimientos que cumplir para realizar una primera liberación (o al menos, considerar la app "completa", cerrrar un iteración, por así decirlo). Para ello, utilicé un tablero _Kanban_ para mantener un orden. La herramienta que escogí fue [Notion](https://www.notion.so), y en general fue el sitio donde registré todo mi progreso y los recursos que iba recolectando.

Mi lista de tareas era la siguiente:

- Buscar por texto
- Cargar más resultados (paginación)
- Filtrar y ordenar resultados
- Ver detalles de elementos
- Descargar elemento

Para cada una de estas tareas hubo un pequeño ciclo de desarrollo, de subtareas que debía completar. A veces claras y otras veces definidas sobre la marcha. Recordar que en ese punto sabía muy poco de Flutter y sus capacidades.

En el mismo tablero agrewgaba también tareas en el _backend._ Tratando de mantener un orden de prioridades y etiquetando cada tarea de acuerdo a qué dominio pertenecían. Tratando de no agregar demasiado, ni siendo demasiado amplias. El objetivo era mantener una guía relativamente clara de lo que debía hacer, ya que de lo contrario, el desarrollo se extiende, no hay objetivos claros, y comienza a desagradar.

En general, logré llevar un muy buen ritmo, pero hacia el final de la "iteración", cuando tocaba realizar los toques finales para tener algo digno que mostrar (o algo así, claramente la app la UI no es la mejor, se nota que no consideré un diseño previo antes de programar, lo cual es lo que peor que alguien sin sentido estético puede hacer), ocurrió lo que me temía, y me pasé al menos dos semanas sólo resolviendo pequeños bugs y corriendo la UI, a veces estancado por días. Mi lista de tareas sólo para ese proceso se ve así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%203.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%203.png) -->

Este era sólo un punto en el backlog. Faltan además todos los TODOs en el código como tal, que creció como una lista independiente de mi Kanban en Notion, dentro de un archivo en el proyecto (lamento el zoom):

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%204.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%204.png) -->

Pese a todo, logré retomar las riendas y llevar la app a su estado final, lista para pasar al _deploy_ en FDroid (el proceso de liberación como tal merece un artículo aparte, en formato de tutorial, debido a su complejidad y a que hay poca información en general, sobre todo para Flutter).

BLoC

Si bien no tenía experiencia con Flutter, sí había oído de las múltiples maneras que existen (y contando) para el manejo del estado. Y por supuesto, sin valoración previa, opté por la más famosa, BLoC. Por suerte, fue adecuado para mis casos de uso.

En ese entonces, estaba terminando de leer _[Flutter in Action](https://www.manning.com/books/flutter-in-action)_, un muy buen punto de partida para cualquier novato, o quien quiera conocer Flutter un poco más a fondo. Contiene una sección dedicada al manejo del estado con el patrón BLoC, y está brillantemente explicado por medio de una implementación bruta (_from scratch_, por así decirlo), es decir, sin librerías de por medio. Lo cual me parece perfecto.

Tratando de seguir el ejemplo del libro y guiándome por tutoriales, traté de implementar un buscador (usando mi endpoint recién creado) usando la función _[showSearch()](https://api.flutter.dev/flutter/material/showSearch.html)_ incorporada en Flutter. Resultó bien para comenzar, y usé esa base para posteriormente reemplazar la implementación inicial por una a partir de la librería _[flutter_bloc](https://pub.dev/packages/flutter_bloc)._ Esto facilitó mucho el desarrollo y ayudó a organizar mejor el código. Si bien no tenía una arquitectura como tal, puesto que estamos hablando sólo del manejo de estado, al menos podía separar cómodamente los procesos o aspectos de la app y evitar cocinar fideos.

Los blocs de la aplicación son bastante genéricos. Uno de ellos se encarga de las búsquedas. Su método `mapEventToState()` luce así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%205.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%205.png) -->

Maneja un único evento (buscar), emite un estado de carga con una _flag_ para indicar si se requiere limpiar la búsqueda, y valida si hay más resultados que mostrar. En caso de que no, usa el repositorio para obtener los libros de acuerdo al texto y los filtros definidos en el flujo de _showSearch()_ en la UI.

El bloc de descargas es un poco más complejo, ya que alberga todo el _boilerplate_ requerido por _flutter_downloader_. Pero su `mapEventToState()` se ve así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%206.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%206.png) -->

También considera un único evento (descargar) y tiene un repositorio asociado (que no es más que un contenedor para los métodos de la instancia de flutter_downloader). Notar el estado `DownloadPermissionsPermanentlyDenied`. Su rol es indicar a la UI que el usuario ha negado los permisos y se requiere acceder a los Ajustes del dispositivo para volver a activarlos. Curiosamente, en algunos casos (en mi caso particular, con un Android 9), puede ocurrir que los permisos al momento de abrir la app ya estén denegados.

Si los permisos fueron entregados, la descarga inicia. Primero, se obtiene el link de descarga (_scrappeado_ desde la página de descargas de LibGen, con suerte, será de Cloudflare), luego, se obtiene la ruta a la carpeta de descargas, y finalmente se ejecuta la descarga como tal. Notar que se realiza antes una última validación, para determinar si el archivo pesa más de 200 MB (el tamaño del archivo desde la API viene en bytes). Aunque en general los archivos deberían ser mucho más ligeros, puede ocurrir que el libro sea enorme y el gestor de descargas de la app demore demasiado o caiga en _timeout_. Por eso, decidí que era buena idea dejar la tarea al navegador en esos casos. Así, me aseguro de que el usuario obtendrá su archivo de todas maneras.

El 3er bloc que hay es el de [Hive](https://pub.dev/packages/hive). Hive es una base de datos local NoSQL, ultrarápida y de fácil manejo. En la app, la utilicé para gestionar las sugerencias de búsqueda. Nuevamente, su `mapEventToState()` luce así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%207.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%207.png) -->

En este caso, maneja múltiples eventos, para guardar un nuevo elemento, cargarlos todos o eliminar uno. Notar el tipo `Either` para los resultados del repositorio. Este tipo proviene de la librería _[dartz](https://pub.dev/packages/dartz)_, que permite usar aspectos de programación funcional en Dart. Una técnica muy útil es usar el tipo `Either` para el manejo de errores. En este caso, el repositorio retorna un tipo `Either` cuyo valor izquierdo (`left`) corresponde a un error (sí, debería haber creado una clase específica para los distintos errores y no sólo un `String`) y un lado derecho (`right`) para el resultado esperado.

El último bloc, o mejor dicho _cubit_ (proveniente también de la librería _flutter_bloc_. Más detalles en su [página oficial](https://bloclibrary.dev/#/)), es `ThemeCubit`, que gestiona el cambio entre el tema claro y oscuro de la app.

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%208.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%208.png) -->

Como funcionalidad adicional, utilicé _[hydrated_bloc](https://pub.dev/packages/hydrated_bloc)_ para preservar el estado de la aplicación, en concreto, de este cubit, para que el tema seleccionado por el usuario se mantenga aún después de cerrar y volver a abrir la app. Para este tipo de casos, me parece que esta solución es mejor que un cacheo convencional, por ejemplo, con Hive.

Este es el estado actual de los blocs de la aplicación. Recordar que comencé con una implementación bruta, para tantear terreno. Poco a poco fui mejorando y aún pueden aplicarse muchas mejoras en el código. Por ejemplo, en los blocs bien podría haber usar algo como _[super_enum](https://pub.dev/packages/super_enum)_ o, incluso mejor, _[freezed](https://pub.dev/packages/freezed)._ Pero quería evitar sobre-ingenierizar (?) la app y evitar estancarme. No obstante, todas esas auto-recomendaciones tendrán lugar en futuros proyectos.

DESCARGAS

Luego de demostrarme a mí mismo que se puede hacer lo que imaginaba, toca simplemente ("simplemente") avanzar con los demás casos de uso, de manera minimalista, para luego ir mejorando y agregando cosas necesarias o que mejoren consideramente la aplicación, sobre todo su UX. Comencé por la descarga. Para ello, utilicé el paquete [\*flutter_downloader](https://pub.dev/packages/flutter_downloader)._ En conjunto, necesitaba manejar los permisos proporcionados por el usuario, para lo cual usé _[permissions_handler](https://pub.dev/packages/permission_handler)_, y además obtener la ruta al directorio de descargas, para lo cual usé _[download_path_provider](https://pub.dev/packages/downloads_path_provider)*. El proceso llevó algún tiempo y mucha depuración. Por un problema de *timeout*, tuve que hacer un *fork\* de flutter_downloader para aumentar de 15s a 60s, ya que a veces la descarga demoraba en iniciar (con el descubrimiento de Cloudflare en LibGen este problema desaparece; no obstante, prefiero ser precavido).

En una etapa posterior del desarrollo, me encontré con otro inconveniente. En Android 11 (API 30 del SDK de Android), empieza a regir estrictamente el nuevo modelo de manejo del almacenamiento, lo que limita el acceso que tienen las apps al almacenamiento general del dispositivo. Esto será un problema para el Manuel del futuro, ya que si esto se cumple, seguramente la aplicación no podrá acceder al directorio de descargas. Sin embargo, por ahora, prefiero no apresurarme. Algunos links de referencia: [link](https://developer.android.com/about/versions/11/privacy/storage), [link](https://medium.com/androiddevelopers/android-11-storage-faq-78cefea52b7c).

Durante un tiempo estuve experimentando también con soluciones alternativas. Un muy buen paquete que puede servir para casos de uso similares es _[dio](https://pub.dev/packages/dio)_ (en conjunto con _[flutter_local_notifications](https://pub.dev/packages/flutter_local_notifications)_). Permite una mayor flexibilidad sobre el proceso de descarga y hay buenos ejemplos para tomar como referencia. No obstante, finalmente determiné que flutter_downloader seguía siendo la mejor opción. Quise ponerme un poco más ambicioso y crear una pantalla de gestión de descargas, tal como la del ejemplo de la librería. Pero no resultó bien y preferí seguir con su funcionalidad básica.

DETALLES DEL LIBRO

Una de las partes entretenidas del desarrollo fue mostrar los detalles del libro una vez realizada la búsqueda y seleccionado el ítem de interés para una potencial descarga. Para ello, quise mostrar toda la información disponible, en un formato similar al de Goodreads, donde se muestra en primer lugar la postada, en un fondo llamativo, luego el título, autor(es), descripción y tabla de contenidos. Y al final, una especie de tabla con información adicional relevante, tal como la cantidad de página, el ISBN, el tamaño del archivo, etc.

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608424177.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608424177.png) -->

Por supuesto, no fue menos trabajoso que cualquier otro aspecto del desarrollo. Pero el resultado fue satisfactorio, o algo así. Este es parte del código:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%209.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%209.png) -->

La portada y su fondo son creados con un widget custom llamado `ImageWidgetWithPlaceholder`, que permite mostrar datos por defecto mientras carga la imagen con `NetworkImage`, o seguir mostrándolo si falla la carga. El código de `ImageWidgetWithPlaceholder` es el siguiente:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2010.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2010.png) -->

El resultado es la imagen de la portada con un fondo, que es la misma imagen aumentada y con un filtro, que carga de manera suave.

Otro aspecto relevante de la información son la descripción y la tabla de contenidos. En ambos casos, el dato podría no existir o estar en un formato que no es texto puro... De hecho, en general, las descripciones y tablas de contenido son HTML, no siempre bien formado. Por eso, decidí usar una librería para renderizar HTML en Flutter, _[fluter_html](https://pub.dev/packages/flutter_html)._ Funciona bastante bien. No obstante, me encontré con un problama a la hora de querer implementar un pequeño efecto de expansión y colapso del texto al clickear en un botón "ver más/ver menos" (similar a Goodreads). Si bien me fue posible dar con un efecto similar al esperado, no me terminaba de gustar.

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608425650.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608425650.png) -->

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608425654.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Screenshot_1608425654.png) -->

Finalmente, encontré otra librería que me pareció más útil para el caso: _[simple_html_css](https://pub.dev/packages/simple_html_css)_. Con ella, y en conjunto con _[expandable](https://pub.dev/packages/expandable)_, logré el efecto deseado. La simbiosis se consiguió gracias a que simple_html_css genera un widget `TextSpan`, que está ideado para ser utilizado dentro del widget `RichText` de Flutter, lo cual es muy conveniente en general y en particular para mi idea.

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2011.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2011.png) -->

Debido a peculiaridades de la librería, fue necesario envolver el dato entre dos etiquetas `<div>`. `ExpandableText`, por su parte, se ve así:

<!-- ![LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2012.png](LibGen%20Mobile%2080b8f837d3df4a2a9d7404891b3cea28/Untitled%2012.png) -->

Aquí ocurren muchas cosas, pero lo relevante es lo siguiente. La combinación de `ExpandableTheme`, `ExpandableThemeData`, `ExpandableNotifier` y `Expandable` (todos provenientes de _expandable_) permite crear un widget expansibl/colapsable custom. En mi caso, quería un párrafo que al exceder las 10 líneas se le aplique un _overflow_ con ellipsis, y apareciera un botón de "ver mas", el cual al clickearlo, muestra el texto completo con una animación fluída. Así, y aunque la librería es bastante flexible al respecto, necesitaba una manera de controlar de validar el máximo de líneas, ya que de lo contrario siempre se mostraría el botón de expansión. Por eso, la función `_didExceedMaxLines()` utiliza un `TextPainter` para emular el renderizado del contenido y detectar si excede el número de líneas definido.

INTERNATIONALIZATION

Una de las cosas importantes que, obviamente, dejé para el final fue la internacionalización, vale decir, traducciones. La app está disponible en inglés y español, de acuerdo al sistema (no se puede cambiar desde la app, aunque sería una buena actualización).

En un inicio, intenté seguir la [documentación oficial](https://flutter.dev/docs/development/accessibility-and-localization/internationalization), pero parecía tener problemas, ya que no lograba generar los archivos automáticamente. Por lo tanto, decidí seguir otro ejemplo donjde se usaba el plugin [Fluter Intl](https://plugins.jetbrains.com/plugin/13666-flutter-intl) para VSCode, junto con el paquete [intl](https://pub.dev/packages/intl). El resto fue ir una a una agregando las traducciones. Bastante boilerplate para mi gusto, y asumo que debe haber soluciones mejores, pero funcionó para mí.

MISCELANEOS

Otras librerías que usé durante el desarrollo son las siguientes:

- [http](https://pub.dev/packages/http) para las peticiones a la API (también podría usarse para descargas, aunque quizá es más conveniente dio, dependiendo del caso)
- [url_launcher](https://pub.dev/packages/url_launcher) para abrir el link de descarga en el navegador, cuando el archivo es demasiado grande para manejarlo con flutter_downloader
- [package_info](https://pub.dev/packages/package_info) para obtener información de la app, por ejemplo, su nombre o versión. Esto fue útil para mostrar el diálogo de "about" en la pantalla de inicio
- [equatable](https://pub.dev/packages/equatable), [json_serializable](https://pub.dev/packages/json_serializable), [json_annotations](https://pub.dev/packages/json_annotation) y [build_runner](https://pub.dev/packages/build_runner) fueron usadas como librerías de desarrollo (_dev_dependencies_) para la generación automática de código, principalmente en las _data classes_, o modelos.

Para finalizar, quisiera recordar que este es un proyecto completamente independiente, vale decir, no poseo ningún vínculo con Library Genesis. No pretendo monetizarlo y seguramente no lo liberaré en Play Store. Lo más seguro es que se quede en FDroid, una vez termine el proceso de inclusión. El proyecto, y todos los repos asociados (API, librerías, etc) son Open Source y se agradce cualquier tipo de colaboración.
