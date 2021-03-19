# Gatling framework

A ideia desse repositorio é apresentar como utlizar o framework Gatling e fazer ele funcionar dentro de um container no Docker.

## Pre-requisitos

1. Java 1.8 
2. Maven 3.5
3. Intelij com ScalaPlugin ou VSCode

### Criando o projeto maven

Na pasta onde quer guardar o projeto, abrir o terminal e digitar

`mvn archetype:generate -DarchetypeGroupId=io.gatling.highcharts -DarchetypeArtifactId=gatling-highcharts-maven-archetype`

### Rodando a simulação

* no intelj 

  Basta dar um "run" na classe Engine.scala localizada dentro do src/test/scala

* no vs code

No terminal digite

`mvn gatling:test -Dgatling.simulationClass=simulations.MyFirstTest`


O MyFirstTest seria o nome da simulação que você escreveu em Scala.
Ele vai executar toda a simulação e no final irá gerar um link para o relatório.

### Criando uma imagem do projeto no docker

Criar o Dockerfile 

Para facilitar a criação de uma imagem docker será usado o Dockerfile com as seguintes configurações:

```
FROM maven:3-alpine
COPY . /user/src/myimage
WORKDIR /user/src/myimage

RUN apk update \
    && apk add python3
    
EXPOSE 8080
```

Criar a imagem

No DOckerfile é possível especificar como será essa imagem e de qual arquivo ele fará essa copia. Nesse caso foi copiado o "gatling-framework" criado no topico de criação de projeto com o maven. Nessa pasta contem todas as simulações necessarias. Para a criação da imagem será executado o seguinte comando:

`docker build -t gatling/mvngtl:v1 .`

Não esquecer de colocar o ponto final. Para visualizar a imagem criada é só fazer a listagem:

`docker images`

Rodando um container na imagem criada  

Para rodar um container com a imagem criada será utilizado:

`docker container run -d -p 8080:8080 --name MyContainer -v gtl-volm:/user/src/myimage -it gatling/mvngtl:v1`

--name MyContainer: nome para o container.

Para executar o teste entre no diretorio do projeto e execute normalmente o mvn gatling:test:

```
cd gatling-framework
mvn gatling:test -Dgatling.simulationClass=simulations.MyFirstTest
```

### Referencias

- [Load Testing with Gatling - The Complete Guide](https://www.james-willett.com/gatling-load-testing-complete-guide/)

- [Comandos mais utilizados no Docker](https://woliveiras.com.br/posts/comandos-mais-utilizados-no-docker/)

- [Um repo que tomei como base o arquivo do Dockerfile](https://github.com/rwcosta/ScalaLearning)