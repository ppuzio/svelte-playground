<script>
  import { itemStore } from "../store";
  export const todo; // props syntax

  const deleteTodo = () => {
    itemStore.removeItem(todo);
  };

  const toggleDone = () => {
    const index = itemStore.findIndex(item => item.id === todo.id);
    itemStore[index].checked = !itemStore[index].checked;
  };
</script>

<li class="todo-item {todo.checked ? 'done' : ''}">
  <input id={todo.id} type="checkbox" />
  <label for={todo.id} class="tick" on:click={toggleDone} />
  <span>{todo.text}</span>
  <button class="delete-todo" on:click={deleteTodo}>
    <svg>
      <use href="#delete-icon" />
    </svg>
  </button>
</li>
