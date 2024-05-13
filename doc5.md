## 5. Controlador REST:

* Crie um controlador REST usando as anotações fornecidas pelo Spring MVC 3:
```java
@Controller
@RequestMapping("/tasks")
public class TaskController {
    @Autowired
    private TaskService taskService;

    @RequestMapping(method = RequestMethod.GET)
    @ResponseBody
    public List<Task> getAllTasks() {
        return taskService.findAll();
    }

    @RequestMapping(method = RequestMethod.POST)
    @ResponseBody
    public Task createTask(@RequestBody Task task) {
        return taskService.save(task);
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.GET)
    @ResponseBody
    public ResponseEntity<Task> getTaskById(@PathVariable Long id) {
        return taskService.findById(id)
                .map(task -> ResponseEntity.ok(task))
                .orElse(ResponseEntity.notFound().build());
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.PUT)
    @ResponseBody
    public ResponseEntity<Task> updateTask(@PathVariable Long id, @RequestBody Task updatedTask) {
        return taskService.findById(id)
                .map(existingTask -> {
                    existingTask.setTitle(updatedTask.getTitle());
                    existingTask.setDescription(updatedTask.getDescription());
                    existingTask.setCompleted(updatedTask.isCompleted());
                    return ResponseEntity.ok(taskService.save(existingTask));
                })
                .orElse(ResponseEntity.notFound().build());
    }

    @RequestMapping(value = "/{id}", method = RequestMethod.DELETE)
    @ResponseBody
    public ResponseEntity<Void> deleteTask(@PathVariable Long id) {
        if (taskService.findById(id).isPresent()) {
            taskService.deleteById(id);
            return ResponseEntity.noContent().build();
        } else {
            return ResponseEntity.notFound().build();
        }
    }
}

```


