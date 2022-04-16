<script>
  // Props
  export let todo;

  function onEdit() {

  }

  function deleteTodo() {

  }
</script>

<div>
  {todo.title}
  <button on:click={onEdit}>
    Edit
  </button>
  <button on:click={deleteTodo}>
    Delete
  </button>
</div>
