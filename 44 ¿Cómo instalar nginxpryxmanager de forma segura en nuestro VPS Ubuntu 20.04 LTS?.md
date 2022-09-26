44 ¿Cómo instalar nginxpryxmanager de forma segura en nuestro VPS Ubuntu 20.04 LTS?

Paso 1, creamos carpetas y vamos a ellas desde root:

Paso 1 Primer comando

    cd /home

Paso 1 Segundo comando

    mkdir docker && cd docker

Paso 1 Tercer comando

    mkdir nginxproxymanager && cd nginxproxymanager

Paso 2, creamos el archivo docker-compose.yml

    nano docker-compose.yml
    
Paso 3 Tipo A (si los puertos 80 y 443 están libres, sino dará error!) Si los tienes ocupados, ve al Paso 3 Tipo B.

    version: '3'
    services:
      app:
        image: 'jc21/nginx-proxy-manager:latest'
        restart: unless-stopped
        ports:
          - '80:80'
          - '81:81'
          - '443:443'
        volumes:
          - ./data:/data
          - ./letsencrypt:/etc/letsencrypt

Paso 3 Tipo B (usaremos los puertos 81, 82, 444) y listo

    version: '3'
    services:
      app:
        image: 'jc21/nginx-proxy-manager:latest'
        restart: unless-stopped
        ports:
          - '81:81'
          - '82:82'
          - '444:444'
        volumes:
          - ./data:/data
          - ./letsencrypt:/etc/letsencrypt

Paso 4, levantar docker composer

    docker-compose up -d

Paso 5, esperar a que salga "done" de color verde.

![docker compose up -d nginxproxymanager done](https://user-images.githubusercontent.com/5947268/192280472-199b1ae5-7339-42a3-a809-d119b46dc8fd.png)

Paso 6, ir al link

Ir a la dirección, e ingresar en el puerto correspondiente.

![nginxproxymanager](https://user-images.githubusercontent.com/5947268/192281435-0509b96a-1759-4f60-9568-7d14022f3582.png)
