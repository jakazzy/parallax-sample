<script>
  export let items = [
    { id: 1, name: "milk", done: false },
    { id: 2, name: "bread", done: true },
    { id: 3, name: "sugar", done: false }
  ];
</script>

<style>
  h1 {
    color: purple;
  }
</style>

<div>
  <h1>Things to buy</h1>

  <ul>
    {#each items as item}
      <li>{item.name}</li>
    {/each}
  </ul>
</div>
