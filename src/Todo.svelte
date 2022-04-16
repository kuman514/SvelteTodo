<script>
  // Props
  export let todo;
  export let todos;

  let isEdit = false;
  let editTitle = todo.title;

  function onEdit() {
    isEdit = true;
  }

  function offEdit() {
    isEdit = false;
  }

  function confirmEdit() {
    todo.title = editTitle;
    //todo = todo;
    offEdit();
  }

  function cancelEdit() {
    offEdit();
    editTitle = todo.title;
  }

  function deleteTodo() {
    $todos = $todos.filter(t => (t.id !== todo.id));
  }
</script>

{#if isEdit}
  <div>
    <input
      type="text"
      bind:value={editTitle}
    />
    <button on:click={confirmEdit}>
      OK
    </button>
    <button on:click={cancelEdit}>
      Cancel
    </button>
  </div>
{:else}
  <div>
    {todo.title}
    <button on:click={onEdit}>
      Edit
    </button>
    <button on:click={deleteTodo}>
      Delete
    </button>
  </div>
{/if}

