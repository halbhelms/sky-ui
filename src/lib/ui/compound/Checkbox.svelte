<script>
  export let optionTitle
  export let optionValue
  export let supportText = ''
  export let borders = true

  let selected = false; // Assuming a boolean, adjust as needed
</script>



<div class="checkbox" class:borders={borders}>
  <input type="checkbox" value={optionValue} on:change={onCheckboxChange} />
  <p class="option-title">{optionTitle}</p>
  <p class="support-text">{supportText}</p>
</div>

<style>
  .checkbox {
    padding: 0.75rem;
  }

  .option-title {
    display: inline-block;
  }
  
  .support-text {
    font-weight: 200;
    font-size: 0.75rem;
  }
  
  .borders {
    border: 1px solid silver;
  }
</style>


