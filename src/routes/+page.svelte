<script>
  import Button from '$lib/ui/individual/Button.svelte'
  import Heading from '$lib/ui/individual/Heading.svelte'
  import Paragraph from '$lib/ui/individual/Paragraph.svelte'
  import UITemplate from '$lib/ui/individual/UI-template.svelte'
  import Table from '$lib/ui/individual/Table.svelte'
  function buttonClicked() {
    alert('Clicked')
  }

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

<Table {columns} {tableContents} width="732px"/>

<Button 
  text="Save" 
  baseBgColor = "green" 
  baseTextColor="white" 
  hoverBgColor="red" 
  width="4rem" 
  borderRadius="8px" 
  onClick={buttonClicked}/>

<Heading text="Section Header" color="var(--highlightTextColor)" headingLevel="1" />

<Paragraph text="Why must you incessantly change me?!"/>

<UITemplate />