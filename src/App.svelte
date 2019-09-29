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
  body {
    font-size: 1.8em;
    font-weight: 400;
  }
  .container {
    border: 1px solid #ddd;
    padding: 10px;
    border-radius: 4px;
    transition: 0.15s all;
    margin-bottom: 0.5em;
    display: flex;
    justify-content: center;
  }
  .inner-container {
    max-width: 300px;
  }

  #name {
    width: 100%;
  }
  ul {
    padding-left: 0;
  }
  li {
    list-style: none;
    padding: 6px 10px;
    border-bottom: 1px solid #ddd;
    margin-bottom: 1rem;
  }
  input[type="text"] {
    outline: none;
    margin: 0;
  }
  input[type="checkbox"] {
    margin: 0 10px 0 0;
  }
  label {
    display: block;
    text-transform: uppercase;
    font-size: 0.8em;
    color: #777;
  }
  li button {
    float: right;
    border: none;
    background: transparent;
    padding: 0;
    margin: 0;
    color: #dc4f21;
    font-size: 18px;
    cursor: pointer;
  }

  .done span {
    opacity: 0.4;
  }
</style>

<div class="container">
  <div class="inner-container">
    <h1>Grocery List</h1>
    <form on:submit|preventDefault={addItem}>
      <label for="name">Add an item</label>
      <input id="name" type="text" bind:value={name} />
    </form>
    <ul>
      {#each items as item}
        <li class={item.done ? 'done' : ''}>
          <input type="checkbox" bind:checked={item.done} />
          <span>{item.name}</span>
          <button on:click={() => remove(item)}>X</button>
        </li>
      {/each}
    </ul>
  </div>

</div>
