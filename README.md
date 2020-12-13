# Gatling framework

A ideia desse repositorio é apresentar como utlizar o framework Gatling e fazer ele funcionar dentro de um container no Docker.

### pre-requisitos

1. Java 1.8 
2. Maven 3.5
3. Intelij com ScalaPlugin ou VSCode

### criando o projeto maven

Na pasta onde quer guardar o projeto, abrir o terminal e digitar:
 `mvn archetype:generate -DarchetypeGroupId=io.gatling.highcharts -DarchetypeArtifactId=gatling-highcharts-maven-archetype`


### rodando a simulação
 * no intelj 

  Basta dar um "run" na classe Engine.scala localizada dentro do src/test/scala

* no vs code

No terminal digite: 
 `mvn gatling:test -Dgatling.simulationClass=simulations.MyFirstTest`


- O MyFirstTest seria o nome da simulação que você escreveu em Scala.
- Ele vai executar toda a simulação e no final irá gerar um link para o relatório.

### criando uma imagem do projeto no docker
    

### referencias


 
