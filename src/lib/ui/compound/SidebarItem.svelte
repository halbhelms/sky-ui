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
      text: 'Sidebar Item',
      icon: 'bi-diagram-2',
      link: '#'
    },
    style: {
      width: '100%',
      height: 'auto',
      'font-size': 'var(--font-size-medium)',
      'margin-bottom': 'var(--margin-bottom-large)',
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
<a href={mergedProps.component.link} class="container">  
  <i class={mergedProps.component.icon}></i>
  <h4>{mergedProps.component.text}</h4>
</a>
<!-- #endregion -->

<!-- #region style -->
<style>
  .container {
    display: grid;
    grid-template-columns: 1rem 1fr;
    column-gap: 0.5rem;
  }

  a {
    color: inherit;
    text-decoration: none; 
    border: none;
    margin-bottom: var(--margin-bottom-large);
  }

  a:hover {
    color: var(--accent-color-5);
    font-weight: 600;
  }

  a:hover i {
    color: var(--accent-color-5);
    transform: scale(1.1);
  }
</style>
<!-- #endregion -->