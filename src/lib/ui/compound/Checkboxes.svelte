<script>
  export let borders = false

  let selectedCheckboxes = ['hello']

    
</script>

<div class="checkboxes" class:borders={borders}>
  <slot />
</div>

<style>
  .borders {
    border: 2px solid silver;
  }
</style>