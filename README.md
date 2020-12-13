# Gatling framework
A ideia desse repositorio é apresentar como utlizar o framework Gatling e fazer ele funcionar dentro de um container no Docker.

### pre-requisitos


### criando o projeto maven

Na pasta onde quer guardar o projeto, abrir o terminal e digitar:
 `mvn archetype:generate -DarchetypeGroupId=io.gatling.highcharts -DarchetypeArtifactId=gatling-highcharts-maven-archetype`

### rodando a simulação no vs code

No terminal digite: 
 `mvn gatling:test -Dgatling.simulationClass=simulations.MyFirstTest`

### rodando a simulação no intelj

  Basta dar um "run" na classe Engine.scala localizada dentro do src/test/scala

### criando uma imagem do projeto no docker
    

### referencias
 
