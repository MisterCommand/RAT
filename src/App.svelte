<script>
	import Header from './Header.svelte';
	import Body from './Body.svelte';
	import Table from './Table.svelte';
    import { Search, Checkbox, Row, Grid } from "carbon-components-svelte";
</script>

<Header class="header" />
<Body>
    <Search placeholder="搜索 Search" />
    <Grid>
        <Row>
            <Checkbox labelText="Label text" checked />
            <Checkbox labelText="Label text" checked />
            <Checkbox labelText="Label text" checked />
        </Row>
    </Grid>
    <Table />
</Body>

<style>
    .header {
        box-shadow: 0 8px 10px 1px rgba(0,0,0,0.14), 0 3px 14px 2px rgba(0,0,0,0.12), 0 5px 5px -3px rgba(0,0,0,0.20);
    }
</style>
