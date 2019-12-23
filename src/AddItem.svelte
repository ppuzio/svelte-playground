<script>
  import { itemStore } from "./store";
  let value = "";
  function addTodo() {
    value = value.trim();
    if (!value) return;

    const todo = {
      text: value,
      checked: false,
      id: Date.now()
    };
    itemStore.addItem(todo);
    value = "";
  }
</script>

<div class="empty-state">
  <svg class="checklist-icon">
    <use href="#checklist-icon" />
  </svg>
  <h2 class="empty-state__title">Add your first todo</h2>
  <p class="empty-state__description">What do you want to get done today?</p>
</div>
<form on:submit|preventDefault={addTodo}>
  <input
    class="js-todo-input"
    type="text"
    aria-label="Enter a new todo item"
    placeholder="E.g. Build a web app"
    bind:value />
  <button on:click={addTodo} disabled={!value} class:disabled={!value}>
    Add Item
  </button>
</form>
