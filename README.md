# Docker_MongoDB_MongoExpress
Rodando MongoDB com Mongo Express no Docker


<h2> 1 - Definir imagens </h2>

    - Imagem MongoDB utilizada.
        https://hub.docker.com/_/mongo
    
    - Imagem Mongo Express Utilizada.
        https://hub.docker.com/_/mongo-express

<h2> 2 - Criar o volume </h2>

    - Esta etapa so se faz necessário se for armazenar a base
    de dados , caso esteja usando esse passo a passo apenas para
    estudo pode passaqr para o passo 3.

    - Comando
        docker volume create base_mongo
<img src=./img/DockerVolume.png>

<h2> 3 - Criar a rede para conectar os dois containers </h2>
    
    - Comando
        docker network create NetMongo
<img src=./img/DockerNetwork.png>

<h2> - Criando a Imagem Mongo </h2>

    docker container run --name mongoDB 
    -v "base_mongo:/dados" -d mongo:latest

<img src=./img/DockeContainerMongoDB.png>

<h2> - Colocando a base na rede </h2>

    docker network connect NetMongo "ID da imagem"

<img src=./img/DockerContainerMongo.png>

<h2> - Criando a Imagem Mongo-Express </h2>

    docker container run --network NetMongo \
    -e ME_CONFIG_MONGODB_SERVER=mongoDB \
    -p 8081:8081 mongo-express:0.54.0

<img src=./img/DockerContainerMongoExpress.png>

<h2> Mongo Express rodando no container </h2>

<img src=./img/>

    