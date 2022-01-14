<script>
  export let addTodo;
  let newTodo = '';

  function formSubmitted() {
    addTodo(newTodo);
    newTodo = '';
  }
</script>

<form on:submit|preventDefault={formSubmitted}>
  <label>
    New Todo
    <input bind:value={newTodo} placeholder="Enter a todo...">
  </label>
  <button>Add Todo</button>
</form>