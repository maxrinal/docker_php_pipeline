
```bash
# Build image
docker build -t pepe  ./app_files

# Run detach
# docker run --detach     --name alpine-apache-php     --publish 80:80     --publish 443:443     --restart unless-stopped pepe
docker run --detach     --name alpine-apache-php     --publish 80:80     --publish 443:443 --rm     pepe

# Validamos contenido de 
docker exec -it alpine-apache-php cat /htdocs/index.php
curl --silent localhost

# rm 
docker rm -f alpine-apache-php