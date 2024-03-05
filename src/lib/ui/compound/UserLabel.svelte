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
      name: 'John Smith',
      role: 'CEO',
      icon: 'bi-person-circle'
    },
    style: {
      width: '100%',
      height: 'fit-content',
      color: 'var(--font-color-dark)',
      outline: 0
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
<div class="container" {style}>  
  <i class={mergedProps.component.icon}></i>
  <div>
    <h4>{mergedProps.component.name}</h4>
    <h5>{mergedProps.component.role}</h5>
  </div>
</div>
<!-- #endregion -->

<!-- #region style -->
<style>
  .container {
    display: grid;
    grid-template-columns: 1.25rem 1fr;
    column-gap: 1rem;
    align-items: center;
    padding-top: var(--padding-top-large);
    padding-bottom: var(--padding-bottom-large);
    margin-bottom: var(--margin-bottom-large);
    font-size: 0.75rem;
    border-top: 2px solid silver;
    border-bottom: 2px solid silver;
  }

  i {
    font-size: 1.5rem;
  }

  h5 {
    font-weight: 300;
    margin-top: 0.25rem;
    font-size: calc(var(--font-size-small) * 0.75)
  }
</style>
<!-- #endregion -->