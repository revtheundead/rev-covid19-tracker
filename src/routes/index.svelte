<script context="module">
    import requests from '../data/requests.js'

    export async function preload() {
        try {
            const usStats = await requests.usStats();
            return { usStats }
        } catch (e) {
            console.log(e);
        }
    }
</script>

<script>
    import CovidStat from '../components/CovidStat.svelte';
    import CovidChart from '../components/CovidChart.svelte';
    import TableContainer from '../components/TableContainer.svelte';
import Error from './_error.svelte';

    export let usStats;
</script>

<style>
    .section {
        padding: 1.5rem
    }

    h1 {
        font-size: 2.3rem;
        margin: 0;
    }

    .section.header {
        padding: 0.25rem 1.5rem;
    }
</style>

<svelte:head>
    <title>Covid-19 US Tracking</title>
</svelte:head>

<div class="section header">
    <div class="container">
        <h1>Covid-19 - US</h1>
    </div>
</div>

<CovidStat {...usStats}/>
<CovidChart />
<TableContainer />