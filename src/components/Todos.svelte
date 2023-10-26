<script lang="ts">
  type TTodo = {
    id: number;
    text: string;
    completed: boolean;
  };

  function retrieveTodos() {
    const retr = localStorage.getItem("todos");
    if (retr === null) return [];
    return JSON.parse(retr);
  }

  let todos: TTodo[] = retrieveTodos();
  let text = "";
  $: incrementor = todos.length;

  function addTodo() {
    todos = [...todos, { id: incrementor, text, completed: false }];
    text = "";
    incrementor++;
    localStorage.setItem("todos", JSON.stringify(todos));
  }

  function checkTodo(id: number) {
    todos = todos.map((todo) => {
      if (todo.id === id) {
        return {
          ...todo,
          completed: !todo.completed,
        };
      }
      return todo;
    });
    localStorage.setItem("todos", JSON.stringify(todos));
  }

  function deleteTodo(id: number) {
    todos = todos.filter((todo) => todo.id !== id);
    localStorage.setItem("todos", JSON.stringify(todos));
  }
</script>

<form
  action=""
  on:submit|preventDefault={addTodo}
>
  <input
    type="text"
    bind:value={text}
  />
  <button>Add</button>
</form>

<ul class="todo-list">
  {#each todos as todo (todo.id)}
    <div class="todo">
      <input
        type="checkbox"
        checked={todo.completed ? true : false}
        on:click={() => {
          checkTodo(todo.id);
        }}
      />
      <li>{todo.text}</li>
      <button
        on:click={() => {
          deleteTodo(todo.id);
        }}>Del</button
      >
    </div>
  {/each}
</ul>

<style lang="scss">
  .todo-list {
    list-style: none;
    padding: 0;

    .todo {
      display: flex;
      gap: 1rem;
    }
  }
</style>
