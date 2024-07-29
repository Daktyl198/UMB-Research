<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;
    const clothResearch = get("Advanced Cloth Research") + get("Advanced Codex");

    const t5refinedclothpackage = get("Refined Exquisite Cloth Package") * 10;

    const t1clothpackage = get("Rough Cloth Package") * 10;
    const t2clothpackage = get("Simple Cloth Package") * 10;
    const t3clothpackage = get("Sturdy Cloth Package") * 10;
    const t4clothpackage = get("Fine Cloth Package") * 10;
    const t5clothpackage = get("Exquisite Cloth Package") * 10;

    const t5refinedcloth = get("Refined Exquisite Cloth") + t5refinedclothpackage;

    const t1cloth = get("Rough Cloth") + t1clothpackage;
    const t2cloth = get("Simple Cloth") + t2clothpackage;
    const t3cloth = get("Sturdy Cloth") + t3clothpackage;
    const t4cloth = get("Fine Cloth") + t4clothpackage;
    const t5cloth = get("Exquisite Cloth") + t5clothpackage;

    const t1hair = get("Rough Animal Hair");
    const t2hair = get("Simple Animal Hair");
    const t3hair = get("Sturdy Animal Hair");
    const t4hair = get("Fine Animal Hair");
    const t5hair = get("Exquisite Animal Hair");

    const t1straw = get("Rough Straw");
    const t2straw = get("Simple Straw");
    const t3straw = get("Sturdy Straw");
    const t4straw = get("Fine Straw");
    const t5straw = get("Exquisite Straw");

    const t1textile = get("Rough Textile");
    const t2textile = get("Simple Textile");
    const t3textile = get("Sturdy Textile");
    const t4textile = get("Fine Textile");
    const t5textile = get("Exquisite Textile");

    const t1fillament = get("Rough Wispweave Filament");
    const t2fillament = get("Simple Wispweave Filament");
    const t3fillament = get("Sturdy Wispweave Filament");
    const t4fillament = get("Fine Wispweave Filament");
    const t5fillament = get("Exquisite Wispweave Filament");

    const needt5refinedcloth = (amount - clothResearch) - t5refinedcloth;

    const needt5cloth = needt5refinedcloth - t5cloth;
    const needt4cloth = (needt5cloth) - t4cloth;
    const needt3cloth = (needt4cloth) - t3cloth;
    const needt2cloth = (needt3cloth) - t2cloth;
    const needt1cloth = needt2cloth - t1cloth;

    const needt5fillament = needt5cloth*40 - t5fillament;
    const needt4fillament = needt4cloth*20 - t4fillament;
    const needt3fillament = needt3cloth*10 - t3fillament;
    const needt2fillament = needt2cloth*5 - t2fillament;
    const needt1fillament = needt1cloth*5 - t1fillament;

    const needt5textile = needt5refinedcloth - t5textile;
    const needt4textile = (needt5textile *2) - t4textile;
    const needt3textile = (needt4textile *2) - t3textile;
    const needt2textile = (needt3textile *2) - t2textile;
    const needt1textile = needt2textile - t1textile;

    const needt5straw = needt5textile - t5straw;
    const needt4straw = needt4textile - t4straw;
    const needt3straw = needt3textile - t3straw;
    const needt2straw = needt2textile - t2straw;
    const needt1straw = needt1textile - t1straw;

    const needt5hair = needt5textile - t5hair;
    const needt4hair = needt4textile - t4hair;
    const needt3hair = needt3textile - t3hair;
    const needt2hair = needt2textile - t2hair;
    const needt1hair = needt1textile - t1hair;

    const tabledata = [
        {
            name: "Refined Cloth",
            tier: [
                {tier: "T1", have: 0, need: 0},
                {tier: "T2", have: 0, need: 0},
                {tier: "T3", have: 0, need: 0},
                {tier: "T4", have: 0, need: 0},
                {tier: "T5", have: `${t5refinedcloth} (${t5refinedclothpackage})`, need: needt5refinedcloth},
            ]
        },
        {
            name: "Cloth",
            tier: [
                {tier: "T1", have: `${t1cloth} (${t1clothpackage})`, need: needt1cloth},
                {tier: "T2", have: `${t2cloth} (${t2clothpackage})`, need: needt2cloth},
                {tier: "T3", have: `${t3cloth} (${t3clothpackage})`, need: needt3cloth},
                {tier: "T4", have: `${t4cloth} (${t4clothpackage})`, need: needt4cloth},
                {tier: "T5", have: `${t5cloth} (${t5clothpackage})`, need: needt5cloth},
            ]
        },
        {
            name: "Textile",
            tier: [
                {tier: "T1", have: t1textile, need: needt1textile},
                {tier: "T2", have: t2textile, need: needt2textile},
                {tier: "T3", have: t3textile, need: needt3textile},
                {tier: "T4", have: t4textile, need: needt4textile},
                {tier: "T5", have: t5textile, need: needt5textile},
            ]
        },
        {
            name: "Straw",
            tier: [
                {tier: "T1", have: t1straw, need: needt1straw},
                {tier: "T2", have: t2straw, need: needt2straw},
                {tier: "T3", have: t3straw, need: needt3straw},
                {tier: "T4", have: t4straw, need: needt4straw},
                {tier: "T5", have: t5straw, need: needt5straw},
            ]
        },
        {
            name: "Animal Hair",
            tier: [
                {tier: "T1", have: t1hair, need: needt1hair},
                {tier: "T2", have: t2hair, need: needt2hair},
                {tier: "T3", have: t3hair, need: needt3hair},
                {tier: "T4", have: t4hair, need: needt4hair},
                {tier: "T5", have: t5hair, need: needt5hair},
            ]
        },
        {
            name: "Fillament",
            tier: [
                {tier: "T1", have: t1fillament, need: needt1fillament},
                {tier: "T2", have: t2fillament, need: needt2fillament},
                {tier: "T3", have: t3fillament, need: needt3fillament},
                {tier: "T4", have: t4fillament, need: needt4fillament},
                {tier: "T5", have: t5fillament, need: needt5fillament},
            ]
        },
    ]
</script>

{#each tabledata as insert}
<Table data={insert} />
{/each}