<script>
  import { afterUpdate } from "svelte";
  import { itemStore } from "../store";
  import ListItem from "./ListItem.svelte";
  import { Firestore } from "../firebase/firebase.js";
  let items = [];
  
  const query = Firestore.collection("listItems")
    .get()
    .then(snapshot =>
      snapshot.forEach(doc => {
        items.push(doc.data());
      })
    );
  console.log("TCL: query", query);
</script>

<ul class="todo-list">
  {#await query} 
  <p> waiting </p>
  {:then something}
   <div>it's something</div>
  <!-- the param in parentheses is a key -->
  {#if !!$itemStore.length}
    {#each $itemStore as todo (todo.id)}
      <ListItem {todo} />
    {/each}
  {:else}
    <div>no items, add one</div>
  {/if}
</ul>
