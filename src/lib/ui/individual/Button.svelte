<!-- <svelte:options customElement="ui-button" /> -->
<script>
  export let text = "OK"
  export let width = "fit-content"
  export let height = "fit-content"
  export let xPadding = "10px"
  export let yPadding = "10px"
  export let baseBgColor
  export let hoverBgColor = baseBgColor
  export let baseTextColor
  export let hoverTextColor = baseTextColor
  export let borderRadius = "12px"
  export let onClick = ""

  let regularStyle = `
    cursor: default; 
    color: ${baseTextColor}; 
    background-color: ${baseBgColor}; 
    border: 1px solid ${baseBgColor};
    border-radius: ${borderRadius}; 
    width: ${width}; 
    height: ${height}; 
    padding-left: ${xPadding}; 
    padding-right: ${xPadding}; 
    padding-top: ${yPadding}; 
    padding-bottom: ${yPadding};`

  let hoverStyle = `
    cursor: pointer; 
    color: ${hoverTextColor}; 
    background-color: ${hoverBgColor}; 
    border: 1px solid ${hoverBgColor};
    border-radius: ${borderRadius}; 
    width: ${width}; 
    height: ${height}; 
    padding-left: ${xPadding}; 
    padding-right: ${xPadding}; 
    padding-top: ${yPadding}; 
    padding-bottom: ${yPadding};`

  let style = regularStyle;
  
  function onMouseEnter() {
    style = hoverStyle;
  }

  function onMouseLeave() {
    style = regularStyle;
  }
</script>


<button 
  on:mouseenter={onMouseEnter}
  on:mouseleave={onMouseLeave}
  on:click={onClick}
  style={style}
>  
  {text}
</button>