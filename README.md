# Tarea 3

## 1. Descarga la imagen 'httpd' y comprueba que está en tu equipo
```bash
//descarga la imagen
sudo docker pull httpd
//comprueba que está en tu equipo
sudo docker image ls
```

## 2. Crea un contenedor con el nombre 'dam_web1'
```bash
sudo docker run -d --name dam_web1 httpd
```

## 3. Si quieres poder acceder desde el navegador de tu equipo, ¿que debes hacer?
```bash
//Cambiamos el adaptador de la mv a puente
//Paramos el contenedor
sudo docker stop dam_web1
//Eliminamos el contenedor
sudo docker rm dam_web1
//Creamos un nuevo contenedor asignandole un puerto
sudo docker run -d --name dam_web1 -p 8080:80 httpd
//Comprobamos que está en ejecución: primero la ip
ip address
//y en el navegador
http://10.0.9.147:8000/
```

##  Utiliza bind mount para que el directorio del apache2 'htdocs' esté montado un directorio que tu elijas
```bash
//Creamos nuevo directorio
sudo mkdir /home/usuario/Apache
//Eliminamos el directorioç
sudo rm -r /home/usuario/Apache
//Lo volvemos a crear con un mount
sudo docker run -p 8080:80 -v /home/usuario/Apache:/usr/local/apache2/htdocs --name dam_web1 -d httpd
//Comprobamos que funcione en el navegador
```

## 4.Realiza un 'hola mundo' en html y comprueba que accedes desde el navegador 
```bash
//Creamos un archivo html en el mount
sudo nano /home/usuario/Apache/index.html
//Comprobamos que funcione en el navegador
```

## 5.Crea otro contenedor 'dam_web2' con el mismo bind mount y a otro puerto, por ejemplo 9080 
```bash
//Creamos un nuevo contenedor
sudo docker run -p 9080:80 -v /home/usuario/Apache:/usr/local/apache2/htdocs --name dam_web2 -d httpd
```

## 6. Comprueba que los dos servidores 'sirven' la misma página, es decir, cuando consultamos en el navegador
```bash
//Comprobamos que funcione en el navegador
//primero http://10.0.9.147:8000/
//segundo http://10.0.9.147:9080/
```

## 7. Realiza modificaciones de la página y comprueba que los dos servidores 'sirven' la misma página
```bash
//Modificamos el archivo html
sudo nano /home/usuario/Apache/index.html
//Comprobamos que funcione en el navegador
```