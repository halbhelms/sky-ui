<script>
  export let text = 'cell'
  export let align = 'left'
  export let zebra = false
  export let bottom = false
  export let end = false
  
  let alignment = align == 'right' ? 'justify-content:end;' : 'justify-content:start;'
  
function commaFormatted(input) {
  let number = Number(input); // This will convert strings to numbers if possible, otherwise NaN
  if (!isNaN(number)) {
    // It's now a valid number (or was one already), so format it
    return number.toLocaleString('en-US', {
      minimumFractionDigits: 2,
      maximumFractionDigits: 2
    })
  } 
  // It wasn't a number or couldn't be converted to one, return as is
  return input;
}

let bottomBorderStyle = ''
if (bottom) {
  bottomBorderStyle = 'border-bottom: 2px solid silver;'
}

let endBorderStyle = ''
if (end) {
  endBorderStyle = 'border-right: 2px solid silver;'
}

let zebraStyle = ''
if (zebra) {
  zebraStyle = 'background-color: #DDDDDD; color: var(--font-color-dark);'
}

</script>

<!-- #region HTML markup -->
<div>  
  <div class="table-cell" style="{alignment} {bottomBorderStyle} {endBorderStyle} {zebraStyle}">{commaFormatted(text)}</div>
</div>
<!-- #endregion -->

<!-- #region style -->
<style>
  .table-cell {
    font-size: var(--font-size-small);
    color: var(--font-color-medium);
    height: 1.5rem;
    border: 2px solid silver;
    border-right: 0;
    border-bottom: 0;
    display: flex;
    align-items: center;
    padding-left: 0.25rem;
    padding-right: 0.25rem;
  }
</style>
<!-- #endregion -->