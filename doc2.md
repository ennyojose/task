
## 2. Estruturação de Entidade (Model):
* Crie a entidade Task usando as anotações do JPA:

```java
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
```