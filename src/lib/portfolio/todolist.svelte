<script>
  import { onMount } from 'svelte';

  import InputText from '../utils/input-text.svelte';

  let todos = [];

  onMount(() => {
    const todosStored = localStorage.getItem('todos');
    todos = JSON.parse(todosStored) || [];
  });

  function addTodo(input) {
    todos = [...todos, input];
    localStorage.setItem('todos', JSON.stringify(todos));
  }

  function removeTodo(i) {
    todos = todos.filter((_, index) => index != i);
    localStorage.setItem('todos', JSON.stringify(todos));
  }
</script>

<div class="container">
  <InputText title="Insert" on:submit={(e) => addTodo(e.detail.input)} />

  <ul class="list-disc">
    <p>Click the list to delete</p>
    {#each todos as todo, index (todo)}
      <li class="ml-6">
        <button on:click={() => removeTodo(index)}>{todo}</button>
      </li>
    {/each}
  </ul>
</div>
