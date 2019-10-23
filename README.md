# Docker commands

docker run -d -P dockersamples/static-site

docker port ID_CONTAINER

docker-machine ip if using virtualbox

docker run -d -P --name meu-site dockersamples/static-site


docker run -d -p 12345:80 dockersamples/static-site

docker run -d -P -e AUTHOR="Matheus Francisco" dockersamples/static-site


docker ps -q

docker stop $(docker ps -q)
docker stop -t 0 $(docker ps -q)


# Docker volumes

docker run -v "/var/www" ubuntu   -> link to path
docker inspect ID_CONTAINER
docker container purne


docker run  -it -v "/home/evohc/Files:/var/www" ubuntu
cd var/www/
touch test.txt
echo "tests" > novo-arquivo.txt


docker container purne -> rm all docker stops


docker run -p 8080:3000 -v "/home/evohc/Files/matheus-francisco/docker-study/volume-exemplo/:/var/www" -w "/var/www" node npm start
docker run -d -p 8080:3000 -v "$(pwd):/var/www" -w "/var/www" node npm start


# Dockerfile commands
docker build -f Dockerfile -t matheus/node .
docker run -d -p 8080:3000 matheus/node


docker build -f Dockerfile - cria uma imagem a partir de um Dockerfile.
docker build -f CAMINHO_DOCKERFILE/Dockerfile -t NOME_USUARIO/NOME_IMAGEM - constrói e nomeia uma imagem não-oficial informando o caminho para o Dockerfile.
docker login - inicia o processo de login no Docker Hub.
docker push NOME_USUARIO/NOME_IMAGEM - envia a imagem criada para o Docker Hub.
docker pull NOME_USUARIO/NOME_IMAGEM - baixa a imagem desejada do Docker Hub.


# Docker comunicação entre containers

docker network create --driver bridge minha-rede
docker network ls
docker run -it -name meu-container ubuntu --network minha-rede



## Docker network
docker pull douglasq/alura-books:cap05
docker pull mongo

docker run -d -p 8080:3000 douglasq/alura-books:cap05
docker run -d --name meu-mongo --network minha-rede mongo
docker run --network minha-rede -d -p 8080:3000 douglasq/alura-books:cap05


# Segue a lista com os principais comandos utilizados durante o curso:

## Comandos relacionados às informações
docker version - exibe a versão do docker que está instalada.

docker inspect ID_CONTAINER - retorna diversas informações sobre o container.

docker ps - exibe todos os containers em execução no momento.

docker ps -a - exibe todos os containers, independentemente de estarem em execução ou não.

## Comandos relacionados à execução
docker run NOME_DA_IMAGEM - cria um container com a respectiva imagem passada como parâmetro.

docker run -it NOME_DA_IMAGEM - conecta o terminal que estamos utilizando com o do container.

docker run -d -P --name NOME dockersamples/static-site - ao executar, dá um nome ao container.

docker run -d -p 12345:80 dockersamples/static-site - define uma porta específica para ser atribuída à porta 80 do container, neste caso 12345.

docker run -v "CAMINHO_VOLUME" NOME_DA_IMAGEM - cria um volume no respectivo caminho do container.

docker run -it --name NOME_CONTAINER --network NOME_DA_REDE NOME_IMAGEM - cria um container especificando seu nome e qual rede deverá ser usada.

## Comandos relacionados à inicialização/interrupção
docker start ID_CONTAINER - inicia o container com id em questão.

docker start -a -i ID_CONTAINER - inicia o container com id em questão e integra os terminais, além de permitir interação entre ambos.

docker stop ID_CONTAINER - interrompe o container com id em questão.

## Comandos relacionados à remoção
docker rm ID_CONTAINER - remove o container com id em questão.

docker container prune - remove todos os containers que estão parados.

docker rmi NOME_DA_IMAGEM - remove a imagem passada como parâmetro.

## Comandos relacionados à construção de Dockerfile
docker build -f Dockerfile - cria uma imagem a partir de um Dockerfile.

docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM - constrói e nomeia uma imagem não-oficial.

docker build -f Dockerfile -t NOME_USUARIO/NOME_IMAGEM CAMINHO_DOCKERFILE - constrói e nomeia uma imagem não-oficial informando o caminho para o Dockerfile.

## Comandos relacionados ao Docker Hub
docker login - inicia o processo de login no Docker Hub.

docker push NOME_USUARIO/NOME_IMAGEM - envia a imagem criada para o Docker Hub.

docker pull NOME_USUARIO/NOME_IMAGEM - baixa a imagem desejada do Docker Hub.

## Comandos relacionados à rede
hostname -i - mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container).

docker network create --driver bridge NOME_DA_REDE - cria uma rede especificando o driver desejado.

