<script>
</script>

<header class="container">
    <div class="row">
        <span class="chi">快速抗原測試認證名單</span><br>
        <span class="eng">List of Approved RAT Test Kits</span>
    </div>
    <article class="toggle"><slot></slot></article>
</header>

<style>
    header {
        background-color: var(--cds-ui-01);
        box-shadow: 0 4px 5px 0 rgba(0,0,0,0.14), 0 1px 10px 0 rgba(0,0,0,0.12), 0 2px 4px -1px rgba(0,0,0,0.20);
    }

    .row {
        padding-left: 50px;
        padding-top: 20px;
        padding-bottom: 20px;
        max-width: 780px;
        margin: 0 auto;
    }

    .chi {
        font-size: 1.8rem;
        line-height: 120%;
    }

    .eng {
        font-size: var(--cds-body-long-01-font-size, 0.875rem);
    }

    .toggle {
        display: none
    }
</style>
