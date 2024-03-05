<script>
  export let pageQty = 7
  
  let pageArray = []
  for (let i=0; i<pageQty; i++) {
    pageArray.push(i)
  }
  let activeId = 0

  function setActive(num) {
    activeId = num
  }
</script>

<div class="pagination">
  {#each pageArray as num}
    <div 
      class="page-number" 
      class:active={activeId === num}
      on:click={() => setActive(num)} 
      id={num}>
        {num + 1}
    </div>
  {/each}
</div>

<style>
  .pagination {
    display: flex;
    justify-content: end;
    align-items: center;
    column-gap: 1.5rem;
    padding-right: 1.5rem;
    padding-top: 0.75rem;
  }

  .page-number {
    width: 1.5rem;
    height: 1.5rem;
    border-radius: 0.875rem;
    color: var(--accent-color-5);
    cursor: pointer;
    border: 1px solid grey;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .active {
    font-weight: 800;
    color: white;
    background-color: var(--accent-color-5);
  }
</style>