## Casos practicos

Algunos comando o configuraciones que deberias saber:

a) Versión de Nginx instalado.

![image](/img/version.png)

b) Ficheros de configuración.

- /etc/nginx
  
![imagen](/img/instalacion1.png)
  
- /etc/nginx/nginx.conf
  
![imagen](/img/instalacion2.png)
  
- /etc/nginx/sites-available
  
![imagen](/img/instalacion3.png)


c) Página web modificada:

![image](/img/instalacion4.png)

![image](/img/pagina.png)

# Configuracion de Servidor de Balanceo de Cargas de Nginx
Para realizar este ejercicio necesitaremos 3 maquinas, dos que hospedaran nuestras paginas webs y otra que ejercera la funcion de servidor de Balanceo De Cargas

Primero configuraremos las dos maquinas donde estara nuestra pagina web:

```
 # Instalar nginx 
 apt install nginx 
 systemctl start nginx
 systemctl enable nginx
 systemctl status nginx

 # Configuracion de los servidores clientes: 
rm /var/www/html/index*
nano /var/www/html/index.html
	<html>
	<title>Nginx</title>
	<body>
	Soy la pagina del servidor 1 de Nginx de Hugo
	</body>
	</html>
```
Una vez hecho esto pasaremos al siguiente paso, configurar el servidor de balanceo:
```
# Instalar nginx 
 apt install nginx 
 systemctl start nginx
 systemctl enable nginx
 systemctl status nginx

# Configurar servidor de balance
rm -rf /etc/nginx/sites-available/default
nano /etc/nginx/conf.d/balancing.conf
	upstream backend {
    		server 192.168.1.101; # Ip del servidor primario
    		server 192.168.1.102;  # Ip del servidor secundario
	}

	server {
    		listen      80;
    		server_name hugogs.ddns.net; # Dominio registrado con la IP del servidor de balanceo de carga

    	location / {
        	proxy_redirect      off;
        	proxy_set_header    X-Real-IP $remote_addr;
        	proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
        	proxy_set_header    Host $http_host;
        	proxy_pass http://backend;
    		}
	}

# Instalar certbot
apt install certbot python3-certbot-nginx -y
apt install ufw -y
ufw allow 'Nginx Full'
ufw delete allow 'Nginx HTTP'

# Certificado SSL
sudo certbot --nginx -d hugogs.ddns.net
```
