## 3. Implementação do Repositório:

* No Spring 3, ainda não há suporte nativo para `JpaRepository`, então você precisará criar seu próprio repositório:
```java
public interface TaskRepository {
    List<Task> findAll();
    Task save(Task task);
    Optional<Task> findById(Long id);
    void deleteById(Long id);
}

```

* Implemente a interface TaskRepository com métodos para realizar operações de banco de dados, usando o Hibernate:
```java
@Repository
public class TaskRepositoryImpl implements TaskRepository {
    @PersistenceContext
    private EntityManager entityManager;

    public List<Task> findAll() {
        return entityManager.createQuery("FROM Task", Task.class).getResultList();
    }

    public Task save(Task task) {
        if (task.getId() == null) {
            entityManager.persist(task);
            return task;
        } else {
            return entityManager.merge(task);
        }
    }

    public Optional<Task> findById(Long id) {
        return Optional.ofNullable(entityManager.find(Task.class, id));
    }

    public void deleteById(Long id) {
        Task task = entityManager.find(Task.class, id);
        if (task != null) {
            entityManager.remove(task);
        }
    }
}

```