<script>
	import Header from './Header.svelte';
	import Body from './Body.svelte';
	import Table from './Table.svelte';
    import { Search, Checkbox, Row, Grid } from "carbon-components-svelte";

    let search = "";
    let doh = true;
    let nmpa = true;
    let fda = true;
    let eu = true;

</script>

<Header class="header" />
<Body>
    <Search placeholder="搜索 Search" bind:value={search} />
    <Grid>
        <Row>
            <Checkbox labelText="衛生署 DOH" bind:checked={doh} />
            <Checkbox labelText="藥監局 NMPA" bind:checked={nmpa} />
            <Checkbox labelText="美國FDA" bind:checked={fda} />
            <Checkbox labelText="歐盟 EU"  bind:checked={eu} />
        </Row>
    </Grid>
    <Table bind:search={search} bind:doh={doh} bind:nmpa={nmpa} bind:fda={fda} bind:eu={eu}/>
</Body>

<style>
    .header {
        box-shadow: 0 8px 10px 1px rgba(0,0,0,0.14), 0 3px 14px 2px rgba(0,0,0,0.12), 0 5px 5px -3px rgba(0,0,0,0.20);
    }
</style>
