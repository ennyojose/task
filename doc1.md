# Passo a Passo do Projeto com Spring 3
## 1. Configuração do Projeto:
* Se ainda não tiver o Spring Framework 3 configurado, siga os seguintes passos:
    * Baixe a versão 3.x do Spring Framework.
    * Adicione os arquivos JAR às bibliotecas de seu projeto.
* Inclua as dependências necessárias no arquivo pom.xml (caso use Maven) ou manualmente nas bibliotecas:
```xml
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

´´´java
@Entity
public class Task {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String title;
    private String description;
    private boolean completed;

    // Getters e Setters
}
