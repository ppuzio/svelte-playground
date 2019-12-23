<script>
  import { afterUpdate } from "svelte";
  import { itemStore } from "./store";
  import ListItem from "./ListItem.svelte";
</script>

<ul class="todo-list">
  <!-- the param in parentheses is a key -->
  {#if !!$itemStore.length}
    {#each $itemStore as todo (todo.id)}
      <ListItem {todo} />
    {/each}
  {:else}
    <div>no items, add one</div>
  {/if}
</ul>
