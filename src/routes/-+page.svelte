<script>
  // import Button from '$lib/ui/individual/Button.svelte'
  import Heading from '$lib/ui/individual/Heading.svelte'
  // import Paragraph from '$lib/ui/individual/Paragraph.svelte'
  // import UITemplate from '$lib/ui/individual/UI-template.svelte'
  // import Table from '$lib/ui/individual/Table.svelte'
  import Sidebar from '$lib/ui/compound/Sidebar.svelte'
  import SidebarHeading from '$lib/ui/compound/SidebarHeading.svelte'
  import UserProfile from '$lib/ui/compound/UserLabel.svelte'
  import SidebarUnit from '$lib/ui/compound/SidebarUnit.svelte'
  import Breadcrumbs from '$lib/ui/compound/Breadcrumbs.svelte'
  import PageTitle from '$lib/ui/compound/PageTitle.svelte'
  import Filter from '$lib/ui/compound/_Filter.svelte'
  import FilterTitle from '$lib/ui/compound/FilterTitle.svelte'
  import FilterOptions from '$lib/ui/compound/_FilterOptions.svelte'
  import FilterOption from '$lib/ui/compound/FilterOption.svelte'
  
  

  let columns = {
    name:           {label: 'Name',size: '1fr', align: 'left'},
    accountNumber:  {label: 'Acct No', size: 'auto', align: 'left'},
    sales:          {label: 'Sales', size: 'auto', align: 'right'}
  }

  let tableContents = [
    {name: 'ABC Company',           accountNumber:'12774',  sales: 3452174},
    {name: 'Davis & Sons',          accountNumber:'55426',  sales: 2956042},
    {name: 'Edward Swanson, Inc.',  accountNumber:'21548',  sales: 917548},
    {name: 'H & H',                 accountNumber:'54879',  sales: 24574},
    {name: 'DB Enterprises',        accountNumber:'92109',  sales: 7752148},
    {name: 'Edward Deming Assoc.',  accountNumber:'58669',  sales: 74201},
    {name: 'Pancake et al.',        accountNumber:'23505',  sales: 1548923},
    {name: 'Markham GBH',           accountNumber:'60254',  sales: 902901}
  ]
</script>

<div class="body">
  <div class="sidebar">
    <Sidebar width="100%" baseBgColor="#202020" baseTextColor="white" xPadding="0.5rem" xMargin="0" yMargin="0">
      <UserProfile text="M. Dotson" xMargin="0" baseTextColor="white" baseBgColor="#202020" baseTextSize="1rem" />
      <SidebarHeading text="SKY Sidebar" xMargin="1rem" yMargin="1rem" baseTextColor="white" baseBgColor="#202020" />
      <SidebarUnit props={{component:{text: 'Revenue', icon: 'bi-bar-chart-fill'}, style: {}}}/>
      <SidebarUnit props={{component:{text: 'Forms', icon: 'bi-ui-checks'}, style: {}}}/>
      <SidebarUnit props={{component:{text: 'Objects', icon: 'bi-box'}}}/>
    </Sidebar>
  </div>
  <div class="main">
    <Breadcrumbs props={{component: {text: 'Reports > Transactions > Sales'}}} />
    <PageTitle props={{component: {text: 'Sales Report'}}} />
    <Filter props={{component: {text: 'Region'}, style: {outline: '2px solid pink'}}}>
      <FilterTitle props={{component: {text:"Region", icon: "bi-globe-americas"}}} />
      <FilterOptions>
        <FilterOption props={{component:{text:"All Regions"}}} />
      </FilterOptions>
    </Filter>
  </div>
</div>


<style>
  .body {
    display: grid;
    grid-template-columns: 220px 1fr;
    column-gap: 2rem;
    background-color: var(--background-color-medium);
  }
</style>




