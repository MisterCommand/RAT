<script>
    import { DataTable, Pagination } from "carbon-components-svelte";
    import rat from './rat.csv';
    import convert from 'chinese_convert';

    let data = rat;
    let page = 1;
    export let search;
    export let doh;
    export let nmpa;
    export let eu;
    export let fda;

    // Search and Filter
    function filter() {
        search = search.toLowerCase().trim();
        search = convert.cn2tw(search);
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
        if (eu) {
            approved.push("歐盟 EU");
        }
        if (fda) {
            approved.push("美國 FDA");
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
        forwardText="下一頁 Next Page"
        backwardText="上一頁 Previous Page"
        pageSizeInputDisabled
        pageInputDisabled
      />

<style>

</style>