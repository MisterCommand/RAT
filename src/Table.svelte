<script>
    import { DataTable, Pagination } from "carbon-components-svelte";
    
  </script>
  
  <DataTable
    sortable
    headers={[
      { key: "name", value: "Name" },
      { key: "protocol", value: "Protocol" },
      { key: "port", value: "Port" },
      { key: "cost", value: "Cost", display: (cost) => cost + " €" },
      {
        key: "expireDate",
        value: "Expire date",
        display: (date) => new Date(date).toLocaleString(),
        sort: (a, b) => new Date(a) - new Date(b),
      },
    ]}
    pageSize={10}
    page={1}
    rows={[]}
  />
  <Pagination
    pageSize={20}
    totalItems={6}
    pageSizeInputDisabled
    pageInputDisabled
  />
  