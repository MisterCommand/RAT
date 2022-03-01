<script>
	import Header from './Header.svelte';
	import Footer from './Footer.svelte';
	import Body from './Body.svelte';
	import Table from './Table.svelte';
    import SvelteSeo from "svelte-seo";
    import { Theme, Toggle, Search, Checkbox, Row, Grid, Tile, Accordion, AccordionItem, OutboundLink } from "carbon-components-svelte";

    let search = "";
    let doh = true;
    let nmpa = true;
    let eu = true;
    let fda = true;

    let toggled = false;
    $: theme = toggled ? "g90" : "white"
</script>

<SvelteSeo
    title="政府快速抗原測試名單"
    description="香港特別行政區政府建議市民購買的快速抗原測試之名單"
    openGraph={{
        title: '政府快速抗原測試名單',
        description: '香港特別行政區政府建議市民購買的快速抗原測試之名單 A list of RAT kits recommended by the Government of HKSAR',
        url: 'https://rathk.com/',
        type: 'website',
        images: [
                {
                    url: 'https://rathk.com/image/rat.jpg',
                    width: 640,
                    height: 427,
                    alt: 'RAT Kit'
                }
            ]
    }}
    twitter={{
        card: "summary",
        title: "政府快速抗原測試名單",
        description: "香港特別行政區政府建議市民購買的快速抗原測試之名單 A list of RAT kits recommended by the Government of HKSAR",
        image: "https://www.example.com/images/cover.jpg",
        imageAlt: "RAT Kit",
    }}
/>

<Theme bind:theme persist persistKey="__theme" />
<Header><Toggle bind:toggled /></Header>
<Body>
    <article class="tile">
        <Tile>
            <p>
                本網頁集合香港特別行政區政府建議市民購買的快速抗原測試之名單，包括香港特別行政區衞生署（衛生署）、國家藥品監督管理局（藥監局）、歐盟、美國食品及藥物管理局（美國 FDA）的認證名單。購買快速抗原測試時，應確保產品爲正貨並已取得認受性高的第三方機構認證。
                This website contains a list of RAT (Rapid Antigen Test) kits recommended by the Government of the Hong Kong Special Administrative Region, including the Department of Health, Hong Kong SAR (DOH), National Medical Products Administration (NMPA), European Union (EU), and U.S. Food and Drug Administration (FDA).
            <OutboundLink href="https://www.coronavirus.gov.hk/rat/chi/rat.html">政府有關快速抗原測試的網頁 Official RAT Information</OutboundLink><br>
            </p>
        </Tile>
    </article>
    <Search placeholder="搜索 Search" bind:value={search} />
    <Grid>
        <Row>
            <Checkbox labelText="衛生署 DOH" bind:checked={doh} />
            <Checkbox labelText="藥監局 NMPA" bind:checked={nmpa} />
            <Checkbox labelText="歐盟 EU"  bind:checked={eu} />
            <Checkbox labelText="美國 FDA" bind:checked={fda} />
        </Row>
    </Grid>
    <article class="table">
        <Table bind:search={search} bind:doh={doh} bind:nmpa={nmpa} bind:fda={fda} bind:eu={eu}/>
    </article>
    
    <article class="accordion">
        <Accordion align="start">
            <AccordionItem title="機構 Organisations">
            <p>
                「衞生署」爲香港特別行政區衞生署之簡稱
                「藥監局」爲國家藥品監督管理局之簡稱
                「歐盟」爲歐盟2019冠狀病毒病快速抗原測試通用名單之簡稱
                「美國」爲美國食品及藥物管理局之簡稱
                "DOH" is the abbreviation for Department of Health, Hong Kong SAR
                "NMPA" is the abbreviation for National Medical Products Administration
                "EU" is the abbreviation for European Union
                "FDA" is the abbreviation for U.S. Food and Drug Administration
            </p>
            </AccordionItem>
            <AccordionItem title="資料來源 Sources">
            <p>
                <OutboundLink href="https://www.mdd.gov.hk/tc/whats-new/rapid-antigen-tests-covid-19/index.html">衞生署 DOH (最後更新 Last update: 1/3/2022)</OutboundLink><br>
                <OutboundLink href="https://www.nmpa.gov.cn/directory/web/nmpa/images/1643248396260012059.docx">藥監局 NMPA (最後更新 Last update: 1/3/2022)</OutboundLink><br>
                <OutboundLink href="https://ec.europa.eu/health/system/files/2022-02/covid-19_rat_common-list_en.pdf">歐盟 EU (最後更新 Last update: 1/3/2022)</OutboundLink><br>
                <OutboundLink href="https://www.fda.gov/medical-devices/coronavirus-disease-2019-covid-19-emergency-use-authorizations-medical-devices/in-vitro-diagnostics-euas-antigen-diagnostic-tests-sars-cov-2#IndividualEUAs">美國 FDA (最後更新 Last update: 1/3/2022)</OutboundLink>
            </p>
            </AccordionItem>
        </Accordion>
    </article>
</Body>
<article class="footer">
    <Footer />
</article>

<style>

    p {
        text-align: left;
        white-space: pre-line;
    }

    :global(.bx--accordion__content) {
        padding: 0;
    }

    .tile {
        position: relative;
        padding-bottom: 1rem;
    }

    .table {
        padding-top: 1rem;
    }
    .accordion {
        padding-top: 1rem;
    }

    .footer {
        width: 100%;
        position: absolute;
        margin-top: 5rem;
    }
</style>
