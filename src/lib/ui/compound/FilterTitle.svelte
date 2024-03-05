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
      text: 'Filter Title',
      icon: 'bi-file-text'
    },
    style: {
      width: '100%',
      height: 'auto',
      'font-size': 'var(--font-size-small)',
      color: 'var(--font-color-dark)',
      'margin-bottom': 'var(--margin-bottom-small)',
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
<div class="container">  
  <div class="filter-title">
    <i class={mergedProps.component.icon}></i>
    <h4>{mergedProps.component.text}</h4>
  </div>
  
  </div>
<!-- #endregion -->

<!-- #region style -->
<style>
  div.filter-title{
    display: grid;
    grid-template-columns: 1rem 1fr;
    align-items: center;
    column-gap: 0.5rem;
    position: relative;
  }

  .info-container {
    position: relative;
  }

  .info {
    display: inline-block;
    position: absolute;
    height: 0.5rem;
    width: 0.5rem;
    font-size: 0.55rem;
    color: white;
    border-radius: 0.3rem;
    background-color: green;
    z-index: 200;
    text-align: center;
    cursor: pointer;
    left: 0rem;
    top: -2.3rem;
  }
</style>
<!-- #endregion -->