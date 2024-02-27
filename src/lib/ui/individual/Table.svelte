<script>
  // #region component props
  export let tableContents = [];
  export let columns = {};
  export let zebraStriping = false;

  let labels = Object.values(columns)
  // #endregion

  let gridTemplateColumns = labels.map((item) => item.size).join(" ");
  
  function commaFormatted(num) {
    console.log(typeof num)
    if (typeof num == 'number') {
      num = num.toLocaleString();
    } 
    return num
  }

  // #region style props
  export let width = "fit-content";
  export let height = "fit-content";
  export let xPadding = "10px";
  export let yPadding = "10px";
  export let baseBgColor = "white";
  export let baseTextColor = "#202020";
  export let borderRadius = "none";
  export let borderColor = baseTextColor;
  export let borderThickness = "0px";
  export let borderStyle = "solid";
  // #endregion

  // #region inline styling
  let style = `
    width: ${width}; 
    height: ${height}; 
    padding ${yPadding} ${xPadding}; 
    color: ${baseTextColor}; 
    background-color: ${baseBgColor}; 
    border: ${borderThickness} ${borderStyle} ${borderColor};
    border-radius: ${borderRadius}; 
    cursor: default; 
    display: grid;
    grid-template-columns: ${gridTemplateColumns};
    `;
  // #endregion
</script>

<div class="table-grid" {style}>
  {#each labels as label}
  <div class="{label.align} table-header">{label.label}</div>
  {/each}
  
  {#each tableContents as tableContent, i}
    {#each Object.keys(tableContent) as key}
      <div class="table-content {columns[key].align}">{commaFormatted(tableContent[key])}</div>
    {/each}
  {/each}
</div>

<style>
  .table-header,
  .table-content {
    padding: 12px 1.5rem;
  }

  .left {
    text-align: left;
  }
  .right {
    text-align: right;
  }
  .center {
    text-align: center;
  }

  .table-header {
    font-size: 1.5rem;
    font-weight: 600;
  }
</style>
