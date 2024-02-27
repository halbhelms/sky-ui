<script>
  export let text = "Default Heading Text"
  export let headingLevel = 1
  
  export let fontSize = "1rem"
  export let width="fit-content"
  export let height="fit-content"
  export let xPadding = "10px"
  export let yPadding = "10px"
  export let baseBgColor = "white";
  export let color = "var(--regularTextColor)"
  export let borderRadius = "12px"
  export let onClick = ""

  let textSize = fontSize;

  

  $: style = `
  cursor: default; 
  color: ${color}; 
  background-color: ${baseBgColor}; 
  border: 1px solid ${baseBgColor};
  border-radius: ${borderRadius}; 
  width: ${width}; 
  height: ${height}; 
  font-size: ${textSize};
  padding-left: ${xPadding}; 
  padding-right: ${xPadding}; 
  padding-top: ${yPadding}; 
  padding-bottom: ${yPadding};`

  const Component = `h${headingLevel}`;
    
</script>

<svelte:element this={Component} {style}>{text}</svelte:element>