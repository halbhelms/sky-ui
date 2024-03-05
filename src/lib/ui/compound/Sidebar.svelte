<script>
  export let props = {}
  // #region default empty objects for props.component and props.style
  if (!props.component) {
    props.component = {}
  }
  if (!props.style) {
    props.style = {}
  }
  // #endregion
  
  // #region allowedProps
  const allowedProps = {
    component: {
      text: 'Sales',
      icon: null
    },
    style: {
      width: '100%',
      height: '100%',
      'font-size': 'var(--font-size-medium)',
      color: 'var(--font-color-dark)',
      'background-color': 'inherit'
    }
  };
  // #endregion

  // #region mergedProps
  let mergedProps = allowedProps
  // Function to only allow overrides without adding new properties, applied to both component and style props
  if (props) {
    const mergeSectionProps = (defaultProps, overrideProps) => {
      let filteredProps = {};
      Object.keys(defaultProps).forEach(key => {
        filteredProps[key] = overrideProps.hasOwnProperty(key) ? overrideProps[key] : defaultProps[key];
      });
      return filteredProps;
    };
  

    mergedProps = {
      component: mergeSectionProps(allowedProps.component, props.component),
      style: mergeSectionProps(allowedProps.style, props.style),
    };
  }
  // #endregion
  
  // #region inline style
  let style =""

  Object.entries(mergedProps.style).forEach(([key, value]) => {
    style += `${key}: ${value};`
  });
  // #endregion

</script>

<!-- #region HTML markup -->
<div>  
  <div class="sidebar" {style}>     
    <slot />
  </div>
</div>
<!-- #endregion -->

<!-- #region style -->
<style>
  .sidebar {
    display: flex;
    flex-direction: column;
    flex: 1;
  }
</style>
<!-- #endregion -->