<script>
  import UserLabel from '$lib/ui/compound/UserLabel.svelte'
  import Sidebar from '$lib/ui/compound/Sidebar.svelte'
  import SidebarItem from '$lib/ui/compound/SidebarItem.svelte'

  import Breadcrumbs from '$lib/ui/compound/Breadcrumbs.svelte'
  import PageTitle from '$lib/ui/compound/PageTitle.svelte'
  import Filter from '$lib/ui/compound/Filter.svelte'
  import Table from '$lib/ui/individual/Table.svelte'
  import TableCell from '$lib/ui/individual/TableCell.svelte'
  import Pagination from '$lib/ui/compound/Pagination.svelte'
  import InfoCard from '$lib/ui/compound/InfoCard.svelte'

</script>

<section>
  <div class="left">
    <UserLabel props={{component:{name: 'Mikelle Dotson', role:'Web Programmer'}, style:{}}}/>
    <Sidebar>
      <SidebarItem props={{component:{text: 'Dashboard', icon: 'bi-columns-gap'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'Analytics', icon: 'bi-bar-chart'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'Locations', icon: 'bi-globe-asia-australia'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'Team Members', icon: 'bi-people'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'SkyFi', icon: 'bi-bank'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'Settings', icon: 'bi-gear'}, style:{}}}/>
      <SidebarItem props={{component:{text: 'Log Out', icon: 'bi-box-arrow-right'}, style:{}}}/>
    </Sidebar>
  </div>
  
  <div class="right">
    <Breadcrumbs props={{component:{text: 'Reports > Transactions > Sales'}, style:{}}}/>
    <PageTitle props={{component:{text: 'Sales Report'}, style:{}}}/>
    <div class="top">
      <div class="left">
        <div class="filters">
          <Filter props={{component:{icon: 'bi-globe-americas', filterTitle:'Region', filterSelection: 'All Regions', options:['All Regions', 'Northeast', 'Midwest', 'South']}, style:{}}}/>
          <Filter props={{component:{icon: 'bi-geo', filterTitle:'Location', filterSelection: 'All Locations', options:['Coastal Point', 'Cityscape Corner', 'Lakeside Lodge', 'Riverside View', 'Summit Plaza', 'Harbor Haven', 'Central Hub', 'Central Park']}, style:{}}}/>
          <Filter props={{component:{icon: 'bi-wallet', filterTitle:'Payment Type', filterSelection: 'SkyFi ACH', options:['SkyFi Debit','Credit Card', 'ACH']}, style:{}}}/>
          <Filter props={{component:{icon: 'bi-box2', filterTitle:'Products', filterSelection: 'All Products', options:['All Products']}, style:{}}}/>
          <Filter props={{component:{icon: 'bi-person-vcard', filterTitle:'Employees', filterSelection: 'All Employees', options:['Anne Baxter', 'Bob Charles', 'Carol Davies', 'Davis Eggers', 'Ellen Franck', 'Fred Grant', 'Gloria Haber', 'Helen Iterson', 'Iona Jones']}, style:{}}}/>
          <Filter props={{component:{icon: 'bi-person-vcard', filterTitle:'Employees', filterSelection: 'All Employees', options:['Anne Baxter', 'Bob Charles', 'Carol Davies', 'Davis Eggers', 'Ellen Franck', 'Fred Grant', 'Gloria Haber', 'Helen Iterson', 'Iona Jones']}, style:{}}}/>
        </div>
      </div>
      <div class="right">
        right
      </div>
    </div>

  <div class="transactions-table">
    <Table props={{table:{columns:{Date: {size: '1fr', align: 'left'}, Region: {size: '1fr', align: 'left'}, Location:{size: '1fr', align: 'left'}, Type: {size: '1fr', align: 'left'}, Gross: {size: '1fr', align: 'right'}} }, cells:{}, headings:{}}}>
      <TableCell text="2023-02-27" /> 
      <TableCell text="Central" /> 
      <TableCell text="Summit Plaza" /> 
      <TableCell text="Credit Card" /> 
      <TableCell text="1102" align="right" end={true} />

      <TableCell text="2023-04-06" zebra={true}/> 
      <TableCell text="North East" zebra={true}/> 
      <TableCell text="Harbor Haven" zebra={true} /> 
      <TableCell text="Credit Card" zebra={true} /> 
      <TableCell text="1227.40" align="right" zebra={true} end={true} />

      <TableCell text="2023-09-06" /> 
      <TableCell text="Central" /> 
      <TableCell text="Riverside View" /> 
      <TableCell text="Credit Card" /> 
      <TableCell text="1831.94" align="right" end={true} />

      <TableCell text="2023-02-02" zebra={true} /> 
      <TableCell text="North East" zebra={true} /> 
      <TableCell text="Lakeside Lodge" zebra={true} /> 
      <TableCell text="Credit Card" zebra={true} /> 
      <TableCell text="1292.5" align="right" zebra={true} end={true} />

      <TableCell text="2023-09-05" /> 
      <TableCell text="Central" /> 
      <TableCell text="Central Park" /> 
      <TableCell text="Credit Card" /> 
      <TableCell text="658.69999" align="right" end={true} />

      <TableCell text="2023-07-30" zebra={true} /> 
      <TableCell text="Mid West" zebra={true} /> 
      <TableCell text="Cityscape Corner" zebra={true} /> 
      <TableCell text="Credit Card" zebra={true} /> 
      <TableCell text="753.92" align="right" zebra={true} end={true} />
      
      <TableCell text="2023-01-16" /> 
      <TableCell text="Central" /> 
      <TableCell text="Riverside View" /> 
      <TableCell text="Credit Card" /> 
      <TableCell text="2524.06" align="right" end={true} />

      <TableCell text="2023-07-31" zebra={true}/> 
      <TableCell text="Central" zebra={true}/> 
      <TableCell text="Central Park" zebra={true}/> 
      <TableCell text="Credit Card" zebra={true}/> 
      <TableCell text="2069.1" align="right" zebra={true} end={true} />
      
      <TableCell text="2023-01-25"  bottom={true}/> 
      <TableCell text="North East"  bottom={true}/> 
      <TableCell text="Harbor Haven"  bottom={true}/> 
      <TableCell text="Credit Card"  bottom={true}/> 
      <TableCell text="589.7554" align="right" end={true}  bottom={true}/>

    </Table>
  </div>

  <InfoCard props={{component:{title: 'Profits', comparedTo: 'v. Last Year', direction: 'up', delta: '12%', number:'$4.5M'}}}/>
  <Pagination pageQty="9"/>
</section>

<style>
  section {
    display: grid;
    grid-template-columns: 250px 1fr;
    background-color: var(--background-color-medium);
  }

  section > div.left {
    background-color: var(--background-color-light);
    border-right: 1px solid silver;
    padding-left: 0.75rem;
    padding-right: 0.75rem;
    padding-top: 3.5rem;
    display: flex;
    flex-direction: column;
    flex: 1;
  }

  div.right {
    padding-left: 0.75rem;
  }

  div.right > .top {
    display: grid;
    grid-template-columns: 3fr 2fr;
  }

  div.filters{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    column-gap: 1rem;
  }
</style>