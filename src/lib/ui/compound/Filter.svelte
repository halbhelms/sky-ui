<script>
  export let props = {}
  let showOptions = false
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
      filterTitle: 'Filter Title',
      icon: 'bi-list',
      filterSelection: 'Filter Selection',
      options: ['Option 1', 'Option 2', 'Option 3']
    },
    style: {
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

  
  function toggleOptions(event) {
    showOptions = !showOptions
  }

    // Optional: Function to close the dropdown if clicking outside of it
  function handleClickOutside(event) {
    if (!event.target.closest('.filter-selection')) {
      showOptions = false;
    }
  }
</script>

<!-- #region HTML markup -->
  <div class="filter" {style} >
    <div class="filter-title">
      <i class={mergedProps.component.icon}></i>
      <h4>{mergedProps.component.filterTitle}</h4>
    </div>     
    <div class="filter-selection" on:click|stopPropagation={toggleOptions}>{mergedProps.component.filterSelection}</div>
    <div class="options" class:visible={showOptions}>
      {#each mergedProps.component.options as option, i}
        <div class="option">
          <input type="checkbox" id="id_{i}">
          <label for="id_{i}">{option}</label>
        </div>
      {/each}
    </div>
  </div>
<!-- #endregion -->

<!-- #region style -->
<style>
  .filter {
    font-size: var(--font-size-small);
    position: relative;
    
  }

  .filter-title {
    display: flex;
    align-items: center;
    column-gap: 10px;
  }

  .filter-selection {
    background-color: var(--background-color-light);
    height: 1.25rem;
    border-radius: 6px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 0.25rem;
    margin-bottom: 0.25rem;
    cursor: pointer;
    border: 1px solid silver;
  }

  .options {
    position: absolute;
    text-align: left;
    color: var(--font-color-light);
    background-color: var(--background-color-dark);
    width: 75%;
    z-index: 1;
    display: none;
  }

  .option {
    margin-bottom: 0.125rem;
  }

  .visible {
    display: block;
  }
</style>
<!-- #endregion -->