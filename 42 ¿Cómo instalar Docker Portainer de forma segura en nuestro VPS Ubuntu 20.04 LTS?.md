42 ¿Cómo instalar Docker Portainer de forma segura en nuestro VPS Ubuntu 20.04 LTS?

Instalamos docker si no lo tenemos

    sudo apt install docker.io -y

Nos aseguramos de que docker está abierto y abrimos por ejemplo NGINX con puerto 80 con docker one click install

    docker run -itd -p 80:80 nginx

Creamos el volumen portainer_disk

    docker volume create portainer_disk

Instalamos docker portainer

    docker run -d -p 9443:9443 -p 8000:8000 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:latest
    
    
    
    
    
Source:
https://youtu.be/iX0HbrfRyvc
you’ve been using Docker WRONG!!
Network Chuck video
Thanks Chuck! Follow him now!
