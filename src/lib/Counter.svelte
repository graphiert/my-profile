<script>
  import { ButtonGroup, Button } from 'flowbite-svelte';
  let count = 0;
  const increment = () => count++;
  const decrement = () => count--;
</script>

<ButtonGroup>
  <Button on:click={decrement}>-1</Button>
  <Button disabled>Number is {count}</Button>
  <Button on:click={increment}>+1</Button>
</ButtonGroup>
