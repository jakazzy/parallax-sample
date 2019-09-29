<script>
  export let items = [
    { id: 1, name: "milk", done: false },
    { id: 2, name: "bread", done: true },
    { id: 3, name: "sugar", done: false }
  ];

  let name = "";
  const addItem = () => {
    items = [...items, { id: Math.random, name, done: false }];
    name = "";
  };
  const remove = item => {
    items = items.filter(i => i !== item);
  };
</script>

<style>
  li button {
    border: 1px solid black;
    background: transparent;
    padding: 2px;
    margin: 2px;
    color: purple;
  }

  .done span {
    opacity: 0.4;
  }
</style>

<div>
  <h1>Things to buy</h1>

  <ul>
    {#each items as item}
      <li class={item.done ? 'done' : ''}>
        <span>{item.name}</span>
        <input type="checkbox" bind:checked={item.done} />
        <button on:click={() => remove(item)}>X</button>
      </li>
    {/each}
  </ul>

  <form on:submit|preventDefault={addItem}>
    <label for="name">Add an item</label>
    <input type="text" bind:value={name} />
  </form>
</div>
