<script>
  import { afterUpdate } from "svelte";
  import { itemStore } from "./store";
  // based on this tutorial https://freshman.tech/svelte-todo/
  // then updated to use components using this one https://medium.com/javascript-in-plain-english/svelte-vs-react-first-impression-1ce5d3ee6889

  function toggleDone(id) {
    const index = itemStore.findIndex(item => item.id === Number(id));
    itemStore[index].checked = !itemStore[index].checked;
  }

  const deleteTodo = item => {
    itemStore.removeItem(item);
  };
</script>

<ul class="todo-list">
  {#each $itemStore as todo (todo.id)}
    <!-- the thing in parentheses is a key -->
    <li class="todo-item {todo.checked ? 'done' : ''}">
      <input id={todo.id} type="checkbox" />
      <label for={todo.id} class="tick" on:click={() => toggleDone(todo.id)} />
      <span>{todo.text}</span>
      <button class="delete-todo" on:click={() => deleteTodo(todo)}>
        <svg>
          <use href="#delete-icon" />
        </svg>
      </button>
    </li>
  {/each}
  {#if !$itemStore.length}
    <div>no items, add one</div>
  {/if}
</ul>
