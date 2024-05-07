# Projeto API de Tarefas com Spring Framework 3

Este projeto é uma API RESTful simples para gerenciar uma lista de tarefas (to-do list). Ele demonstra o uso do Spring Framework 3 para criar uma aplicação back-end que permite operações CRUD básicas sobre tarefas.

## Tecnologias Utilizadas

- Java
- Spring Framework 3.x
- Hibernate 4.x
- Maven
- H2 Database

## Configuração Inicial

### Pré-Requisitos

- JDK 1.8 ou superior
- Maven configurado em sua máquina

### Dependências

Adicione as seguintes dependências no seu `pom.xml` para configurar o projeto:

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-web</artifactId>
        <version>3.x.x</version>
    </dependency>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-jpa</artifactId>
        <version>3.x.x</version>
    </dependency>
    <dependency>
        <groupId>org.hibernate</groupId>
        <artifactId>hibernate-core</artifactId>
        <version>4.x.x</version>
    </dependency>
    <dependency>
        <groupId>com.h2database</groupId>
        <artifactId>h2</artifactId>
        <version>1.4.200</version>
        <scope>runtime</scope>
    </dependency>
</dependencies>
