<script>
  import { afterUpdate } from "svelte";
  import { itemStore } from "./store";
  import AddItem from "./AddItem.svelte";
  import List from "./List.svelte";
  // based on this tutorial https://freshman.tech/svelte-todo/
  // then updated to use components using this one https://medium.com/javascript-in-plain-english/svelte-vs-react-first-impression-1ce5d3ee6889
  afterUpdate(() => {
    document.querySelector(".js-todo-input").focus();
  });
</script>

<main>
  <div class="container">
    <h1 class="app-title">Items: {$itemStore.length}</h1>
    <List />
    <AddItem />
  </div>
</main>
