<script>
  export let text = "Sidebar"
  // #region styling props
  export let width = "fit-content";
  export let height = "fit-content";
  export let xPadding = "10px";
  export let yPadding = "10px";
  export let baseBgColor = "white";
  export let baseTextColor = "#202020";
  export let baseTextSize = "1rem";
  export let borderRadius = "none";
  export let borderColor = baseTextColor;
  export let borderThickness = "0px";
  export let borderStyle = "solid";
  export let xMargin = "1rem"
  export let yMargin = "2rem"
  // #endregion
  // #region inline styling
  let style = `
    width: ${width}; 
    height: ${height}; 
    padding: ${yPadding} ${xPadding}; 
    color: ${baseTextColor}; 
    font-size: ${baseTextSize};
    background-color: ${baseBgColor}; 
    border: ${borderThickness} ${borderStyle} ${borderColor};
    border-radius: ${borderRadius}; 
    cursor: default; 
    margin: ${yMargin} ${xMargin} ${yMargin} ${xMargin}
    `;
  // #endregion
</script>

<div class="sidebar-heading">
  <h2 {style}>{text}</h2>
</div>
