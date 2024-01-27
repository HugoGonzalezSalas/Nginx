## Comparacion entre Nginx y Apache

Algunas de sus principales diferencias son:

- Apache necesita abrir múltiples hilos para atender múltiples peticiones de clientes, mientras que Nginx con un hilo puede atender múltiples peticiones de clientes. Como resultado, consume menos recursos y es capaz de responder más rápidamente.

- Mientras que en alta carga Apache no es capaz de atender múltiples peticiones de forma concurrente y asíncrona, Nginx es todo lo contrario. Está diseñado para atender muchas peticiones de forma asíncrona y siendo lo más eficiente posible al consumir recursos de RAM y CPU.

- Mientras que Apache permite ejecutar PHP dentro del propio servidor web, en Nginx debemos externalizarlo, lo que es mucho más eficiente. Actualmente, usar mod_php en lugar de PHP-FPM es una locura.

- Nginx es muy eficiente al servir contenido estático (imágenes, PDF, CSS, Javascript, etc.), mientras que Apache es más lento y consume más recursos.

- Nginx puede funcionar como servidor HTTP y como proxy inverso, mientras que Apache solo puede funcionar como servidor web.

Como has podido ver en el listado anterior, TODOS los puntos expuestos están relacionados con el rendimiento y con la forma de procesar la carga de trabajo (peticiones entrantes).

Existen algunas diferencias más que no tienen nada que ver con el rendimiento:

- Apache está disponible para cualquier sistema operativo; sin embargo, Nginx funciona bien en todos menos en Windows, donde tiene la compatibilidad algo limitada. Aunque debo aclarar que normalmente estos servicios se instalan en servidores Linux.
- En Apache podemos cargar y descargar módulos fácilmente, mientras que en Nginx el software debe ser compilado con los módulos que le queramos meter.
- Apache está desarrollado por la comunidad directamente, mientras que Nginx es desarrollado por una empresa privada que vende una versión Enterprise de Nginx y varios módulos añadidos.

Y, por último, la diferencia más importante para el usuario final:

- Apache es compatible con los archivos .htaccess para modificar el comportamiento de las webs, mientras que Nginx tiene sus propios archivos de configuración. Precisamente aquí es donde entra en juego LiteSpeed, que es eficiente como Nginx, pero conserva la compatibilidad con los archivos .htaccess.

![image](/img/comparacion.jpg)
