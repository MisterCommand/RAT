<script>
    import { DataTable, Pagination } from "carbon-components-svelte";
    import rat from './rat.csv';

    let data = rat;
    let page = 1;
    export let search;
    export let doh;
    export let nmpa;
    export let fda;
    export let eu;

    // Search and Filter
    function filter() {
        search = search.toLowerCase();
        data = rat.filter((value) => {
            return value.manufacturer.toLowerCase().match(`${search}.*`) || value.product.toLowerCase().match(`${search}.*`) || value.approval.toLowerCase().match(`${search}.*`)
        })
        let approved = [];
        if (doh) {
            approved.push("衛生署 DOH");
        }
        if (nmpa) {
            approved.push("藥監局 NMPA");
        }
        if (fda) {
            approved.push("美國FDA");
        }
        if (eu) {
            approved.push("歐盟 EU");
        }
        data = data.filter((value) => {
            // False -> If Any Match -> True
            let output = false;
            approved.forEach(v => {
                if (value.approval == v) {
                    output = true
                }
            });
            return output;
        })
    }

    $: filter(search, doh, nmpa, fda, eu)

</script>
<DataTable
    sortable
    headers={[
      { key: "manufacturer", value: "品牌 Brand" },
      { key: "product", value: "產品 Product" },
      { key: "approval", value: "認證機構 Approved by" }
    ]}
    pageSize={15}
    bind:page={page}
    bind:rows={data}
  />
  <Pagination
    pageSize={15}
    bind:page={page}
    bind:totalItems={data.length}
    pageSizeInputDisabled
    pageInputDisabled
  />
  