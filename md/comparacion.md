## Comparacion entre Ginx y Apache

Algunas de sus principales diferencias son:

- Apache necesita abrir múltiples hilos para atender múltiples peticiones de clientes, mientras que Nginx con un hilo puede atender múltiples peticiones de clientes. Como resultado, consume menos recursos y es capaz de responder más rápidamente.

- Mientras que en alta carga Apache no es capaz de atender múltiples peticiones de forma concurrente y asíncrona, Nginx es todo lo contrario. Está diseñado para atender muchas peticiones de forma asíncrona y siendo lo más eficiente posible al consumir recursos de RAM y CPU.
- 
- Mientras que Apache permite ejecutar PHP dentro del propio servidor web, en Nginx debemos externalizarlo, lo que es mucho más eficiente. Actualmente, usar mod_php en lugar de PHP-FPM es una locura.
- 
- Nginx es muy eficiente al servir contenido estático (imágenes, PDF, CSS, Javascript, etc.), mientras que Apache es más lento y consume más recursos.
- 
- Nginx puede funcionar como servidor HTTP y como proxy inverso, mientras que Apache solo puede funcionar como servidor web.

Como has podido ver en el listado anterior, TODOS los puntos expuestos están relacionados con el rendimiento y con la forma de procesar la carga de trabajo (peticiones entrantes).
