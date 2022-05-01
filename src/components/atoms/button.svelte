<script>
  export let clickHandler
</script>

<button on:click={clickHandler}>
  <slot></slot>  
</button>

<style>
  button {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    margin: 1rem; 
    padding: 0.25rem 1rem;
    cursor: pointer;
  }
</style>