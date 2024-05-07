## 6. Testes Unitários:
* Adicione testes usando bibliotecas disponíveis no Spring 3. Pode usar o JUnit ou o TestNG.
    * Adicione testes unitários para garantir o funcionamento correto dos componentes:
    
```java
@SpringBootTest
@AutoConfigureMockMvc
public class TaskControllerTests {
    @Autowired
    private MockMvc mockMvc;

    @Test
    public void shouldReturnAllTasks() throws Exception {
        mockMvc.perform(get("/tasks"))
                .andExpect(status().isOk());
    }

    // Outros testes para criação, atualização e exclusão de tarefas
}
    
```