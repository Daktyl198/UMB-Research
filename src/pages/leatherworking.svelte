<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;

    const leatherResearch = get("Advanced Leather Research") + get("Advanced Codex");

    const t5refinedleatherpackage = get("Refined Exquisite Leather Package") * 10;

    const t1leatherpackage = get("Rough Leather Package") * 10;
    const t2leatherpackage = get("Simple Leather Package") * 10;
    const t3leatherpackage = get("Sturdy Leather Package") * 10;
    const t4leatherpackage = get("Fine Leather Package") * 10;
    const t5leatherpackage = get("Exquisite Leather Package") * 10;

    const t5refinedleather = get("Refined Exquisite Leather") + t5refinedleatherpackage;

    const t1leather = get("Rough Leather") + t1leatherpackage;
    const t2leather = get("Simple Leather") + t2leatherpackage;
    const t3leather = get("Sturdy Leather") + t3leatherpackage;
    const t4leather = get("Fine Leather") + t4leatherpackage;
    const t5leather = get("Exquisite Leather") + t5leatherpackage;

    const t1berry = get("Basic Citric Berry");
    const t2berry = get("Simple Citric Berry");
    const t3berry = get("Infused Citric Berry");
    const t4berry = get("Fine Citric Berry");
    const t5berry = get("Exquisite Citric Berry");

    const t1fishoil = get("Basic Fish Oil");
    const t2fishoil = get("Simple Fish Oil");
    const t3fishoil = get("Infused Fish Oil");
    const t4fishoil = get("Fine Fish Oil");
    const t5fishoil = get("Exquisite Fish Oil");

    const t1treatment = get("Basic Leather Treatment");
    const t2treatment = get("Simple Leather Treatment");
    const t3treatment = get("Infused Leather Treatment");
    const t4treatment = get("Fine Leather Treatment");
    const t5treatment = get("Exquisite Leather Treatment");

    const needt5refinedleather = (amount - leatherResearch) - t5refinedleather;

    const needt5leather = needt5refinedleather - t5leather;
    const needt4leather = (needt5leather) - t4leather;
    const needt3leather = (needt4leather) - t3leather;
    const needt2leather = (needt3leather) - t2leather;
    const needt1leather = needt2leather - t1leather;

    const needt5treatment = needt5refinedleather - t5treatment;
    const needt4treatment = (needt5treatment *2) - t4treatment;
    const needt3treatment = (needt4treatment *2) - t3treatment;
    const needt2treatment = (needt3treatment *2) - t2treatment;
    const needt1treatment = needt2treatment - t1treatment;

    const needt5berry = (needt5treatment) - t5berry;
    const needt4berry = (needt4treatment) - t4berry;
    const needt3berry = (needt3treatment) - t3berry;
    const needt2berry = (needt2treatment) - t2berry;
    const needt1berry = (needt1treatment) - t1berry;

    const needt5fishoil = (needt5treatment *2) - t5fishoil;
    const needt4fishoil = (needt4treatment *2) - t4fishoil;
    const needt3fishoil = (needt3treatment *2) - t3fishoil;
    const needt2fishoil = (needt2treatment *2) - t2fishoil;
    const needt1fishoil = (needt1treatment *2) - t1fishoil;

    const tabledata = [
        {
            name: "Refined Leather",
            tier: [
                {tier: "T1", have: 0, need: 0},
                {tier: "T2", have: 0, need: 0},
                {tier: "T3", have: 0, need: 0},
                {tier: "T4", have: 0, need: 0},
                {tier: "T5", have: `${t5refinedleather} (${t5refinedleatherpackage})`, need: needt5refinedleather},
            ]
        },
        {
            name: "Leather",
            tier: [
                {tier: "T1", have: `${t1leather} (${t1leatherpackage})`, need: needt1leather},
                {tier: "T2", have: `${t2leather} (${t2leatherpackage})`, need: needt2leather},
                {tier: "T3", have: `${t3leather} (${t3leatherpackage})`, need: needt3leather},
                {tier: "T4", have: `${t4leather} (${t4leatherpackage})`, need: needt4leather},
                {tier: "T5", have: `${t5leather} (${t5leatherpackage})`, need: needt5leather},
            ]
        },
        {
            name: "Treatment",
            tier: [
                {tier: "T1", have: t1treatment, need: needt1treatment},
                {tier: "T2", have: t2treatment, need: needt2treatment},
                {tier: "T3", have: t3treatment, need: needt3treatment},
                {tier: "T4", have: t4treatment, need: needt4treatment},
                {tier: "T5", have: t5treatment, need: needt5treatment},
            ]
        },
        {
            name: "Fish Oil",
            tier: [
                {tier: "T1", have: t1fishoil, need: needt1fishoil},
                {tier: "T2", have: t2fishoil, need: needt2fishoil},
                {tier: "T3", have: t3fishoil, need: needt3fishoil},
                {tier: "T4", have: t4fishoil, need: needt4fishoil},
                {tier: "T5", have: t5fishoil, need: needt5fishoil},
            ]
        },
        {
            name: "Berry",
            tier: [
                {tier: "T1", have: t1berry, need: needt1berry},
                {tier: "T2", have: t2berry, need: needt2berry},
                {tier: "T3", have: t3berry, need: needt3berry},
                {tier: "T4", have: t4berry, need: needt4berry},
                {tier: "T5", have: t5berry, need: needt5berry},
            ]
        },
    ]
</script>

{#each tabledata as insert}
    <Table data={insert} />
{/each}