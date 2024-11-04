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

