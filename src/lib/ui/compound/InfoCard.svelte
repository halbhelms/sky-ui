<script>
  export let props = {}
  let {component, style} = props
  let {title, number, delta, direction, comparedTo} = component
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
      title: 'Profits',
      number: '4.5M',
      delta: '10%',
      direction: 'up',
      comparedTo: 'Last Year'
    },
    style: {
      width: '100%',
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

  // #endregion`
</script>

<!-- #region HTML markup -->
<div class="info-card">  
  <h3>{title}</h3>
  <div class="numbers">
    <h1>{number}</h1>
    <div class="delta">
      <div class="top">
        <img src="images/_{direction}-arrow.png" alt="">
        <h3>{delta}</h3>
      </div>
      <div class="compared-to">{comparedTo} </div>
    </div>
  </div>
</div>
<!-- #endregion -->

<!-- #region style -->
<style>
  .info-card {
    height: 200px;
    width: 300px;
    display: grid;
    grid-template-rows: 3rem 1fr;
    background-color: var(--background-color-light);
    border: 1px solid silver;
    border-radius: 12px;
    padding: 1rem;
  }

  .numbers {
    display: grid;
    grid-template-columns: 3fr 2fr;
    align-items: center;
  }

  .numbers h1 {
    font-weight: 600;
    font-size: 2rem;
    color: var(--font-color-dark);
  }

  .delta .top {
    display: flex;
    align-items: center;
  }

  .delta img {
    height: 2rem;
  }

  .delta h3 {
    display: inline-block;
    color: #88B69C;
    font-size: 1.5rem;
    font-weight: 600;
  }

  .compared-to {
    font-size: 0.5rem;
    color: #66625B;
    text-align: center;
  }
</style>
<!-- #endregion -->