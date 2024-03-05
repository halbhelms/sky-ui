<script>
  export let props = {}
  // #region default empty objects for props.table, props.cells and props.headings
  if (!props.table) {
    props.table = {}
  }
  if (!props.cells) {
    props.cells = {}
  }
  if (!props.headings) {
    props.headings = {}
  }
  // #endregion

  // #region mergedProps
  const mergedProps = {
    table: {
      columns:          props.table.columns         ?? {},
      contents:         props.table.contents        ?? [],
      width:            props.table.width           ?? '100%',
      height:           props.table.height          ?? 'auto',
      backgroundColor:  props.table.backgroundColor ?? 'var(--background-color-light)'
    },
    cells: {
      color:            props.cells.color           ?? 'var(--font-color-dark)',
      zebraStriping:    props.cells.zebraStriping   ?? false,
      height:           props.cells.height          ?? '1.5rem',
      fullBorders:      props.cells.fullBorders     ?? true,
      borderWidth:      props.cells.borderWidth     ?? '2px',
      borderColor:      props.cells.borderColor     ?? '#E6EAEC',
      fontSize:         props.cells.fontSize        ?? '1rem',
    },
    headings: {
      color:            props.headings.color        ?? 'var(--accent-color-5)',
      fontSize:         props.headings.fontSize     ?? 'var(--font-size-small)',
    }
  };
  // #endregion

  let labels = Object.keys(mergedProps.table.columns)
  const gridTemplateColumns = Object.values(mergedProps.table.columns).map(col => col.size).join(' ');

  // table styling
  let gridStyle = `display: grid; grid-template-columns: ${gridTemplateColumns}; column-gap: 0;`
  
  function commaFormatted(num) {
    if (typeof +num == 'number') {
      num = +num.toLocaleString();
    } 
    return num
  }

</script>

<div class="table" style = "{gridStyle}">
  {#each labels as label}
  <div class="{mergedProps.table.columns[label].align} table-header">{label}</div>
  {/each}
  <slot />
  
</div>

<style>
  .table {
    width: calc(100% - var(--margin-right-large) * 2);
    background-color: var(--background-color-light);
    padding-left: var(--padding-left-medium);
    padding-right: var(--padding-right-medium);
    padding-top: var(--padding-top-medium);
    padding-bottom: var(--padding-bottom-medium);
    border-radius: 12px;
    border: 1px solid silver; 
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
    font-size: 1rem;
    color: var(--accent-color-5);
    font-weight: 600;
    margin-bottom: 0.25rem;
  }

  .striped {
    background-color: lightgrey;
  }
</style>
