<script lang="ts">
  let items = ["orange", "apple", "peach"];

  $: nicerItems = items.map((i) => `nice ${i}`);

  let newItem = "";

  const addItem = (e) => {
    e.preventDefault();
    if (newItem) {
      items = [...items, newItem];
      newItem = "";
    }
  };

  const removeItem = (index: number) => {
    items = items.filter((_, i) => i !== index);
  };
</script>

<h1>Yo showing items:</h1>
<ul>
  {#each nicerItems as item, i}
    <li on:click={() => removeItem(i)}>{item}</li>
  {/each}
</ul>

<form on:submit={addItem}>
  <input bind:value={newItem} />
  <button type="submit">Add item</button>
</form>
