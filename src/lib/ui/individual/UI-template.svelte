<script>
  // #region styling props
  export let width = "fit-content"
  export let height = "fit-content"
  export let xPadding = "10px"
  export let yPadding = "10px"
  export let baseBgColor = "white"
  export let baseTextColor = "#202020"
  export let baseTextSize = "1rem"
  export let borderRadius = "none"
  export let borderColor = baseTextColor
  export let borderThickness = "0px"
  export let borderStyle = "solid"
  // #endregion
  // #region inline styling
  let style = `
    width: ${width}; 
    height: ${height}; 
    padding ${yPadding} ${xPadding}; 
    color: ${baseTextColor}; 
    font-size: ${baseTextSize};
    background-color: ${baseBgColor}; 
    border: ${borderThickness} ${borderStyle} ${borderColor};
    border-radius: ${borderRadius}; 
    cursor: default; 
    `
// #endregion 
</script>

<p {style}>UI-template</p>