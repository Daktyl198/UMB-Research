<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;
    const woodResearch = get("Advanced Wood Research") + get("Advanced Codex");

    const t5refinedplankpackage = get("Refined Exquisite Wood Plank Package") * 10;

    const t1plankpackage = get("Rough Wood Plank Package") * 10;
    const t2plankpackage = get("Simple Wood Plank Package") * 10;
    const t3plankpackage = get("Sturdy Wood Plank Package") * 10;
    const t4plankpackage = get("Fine Wood Plank Package") * 10;
    const t5plankpackage = get("Exquisite Wood Plank Package") * 10;

    const t5refinedplank = get("Refined Exquisite Plank") + t5refinedplankpackage;

    const t1plank = get("Rough Plank") + t1plankpackage;
    const t2plank = get("Simple Plank") + t2plankpackage;
    const t3plank = get("Sturdy Plank") + t3plankpackage;
    const t4plank = get("Fine Plank") + t4plankpackage;
    const t5plank = get("Exquisite Plank") + t5plankpackage;

    const t1resin = get("Basic Amber Resin");
    const t2resin = get("Simple Amber Resin");
    const t3resin = get("Infused Amber Resin");
    const t4resin = get("Fine Amber Resin");
    const t5resin = get("Exquisite Amber Resin");

    const t1polish = get("Basic Wood Polish");
    const t2polish = get("Simple Wood Polish");
    const t3polish = get("Infused Wood Polish");
    const t4polish = get("Fine Wood Polish");
    const t5polish = get("Exquisite Wood Polish");

    const t1cropoil = get("Basic Crop Oil");
    const t2cropoil = get("Simple Crop Oil");
    const t3cropoil = get("Infused Crop Oil");
    const t4cropoil = get("Fine Crop Oil");
    const t5cropoil = get("Exquisite Crop Oil");

    const needt5refinedplank = (amount - woodResearch) - t5refinedplank;

    const needt5plank = needt5refinedplank - t5plank;
    const needt4plank = (needt5plank) - t4plank;
    const needt3plank = (needt4plank) - t3plank;
    const needt2plank = (needt3plank) - t2plank;
    const needt1plank = (needt2plank) - t1plank;

    const needt5polish = needt5refinedplank - t5polish;
    const needt4polish = (needt5polish *2) - t4polish;
    const needt3polish = (needt4polish *2) - t3polish;
    const needt2polish = (needt3polish *2) - t2polish;
    const needt1polish = (needt2polish) - t1polish;

    const needt5cropoil = (needt5polish) - t5cropoil;
    const needt4cropoil = (needt4polish) - t4cropoil;
    const needt3cropoil = (needt3polish) - t3cropoil;
    const needt2cropoil = (needt2polish) - t2cropoil;
    const needt1cropoil = (needt1polish) - t1cropoil;

    const needt5resin = (needt5polish) - t5resin;
    const needt4resin = (needt4polish) - t4resin;
    const needt3resin = (needt3polish) - t3resin;
    const needt2resin = (needt2polish) - t2resin;
    const needt1resin = (needt1polish) - t1resin;

    const tabledata = [
        {
            name: "Refined Wood",
            tier: [
                {
                    tier: "T1",
                    have: 0,
                    need: 0
                },
                {
                    tier: "T2",
                    have: 0,
                    need: 0
                },
                {
                    tier: "T3",
                    have: 0,
                    need: 0
                },
                {
                    tier: "T4",
                    have: 0,
                    need: 0
                },
                {
                    tier: "T5",
                    have: `${t5refinedplank} (${t5refinedplankpackage})`,
                    need: needt5refinedplank
                }
            ]
        },
            
            {
                name: "Planks",
                tier: [
                    {
                        tier: "T1",
                        have: t1plank,
                        need: needt1plank
                    },
                    {
                        tier: "T2",
                        have: t2plank,
                        need: needt2plank
                    },
                    {
                        tier: "T3",
                        have: t3plank,
                        need: needt3plank
                    },
                    {
                        tier: "T4",
                        have: t4plank,
                        need: needt4plank
                    },
                    {
                        tier: "T5",
                        have: t5plank,
                        need: needt5plank
                    }
                ]
            },
        {
            name: "Resin",
            tier: [
                {
                    tier: "T1",
                    have: t1resin,
                    need: needt1resin
                },
                {
                    tier: "T2",
                    have: t2resin,
                    need: needt2resin
                },
                {
                    tier: "T3",
                    have: t3resin,
                    need: needt3resin
                },
                {
                    tier: "T4",
                    have: t4resin,
                    need: needt4resin
                },
                {
                    tier: "T5",
                    have: t5resin,
                    need: needt5resin
                }
            ]
        },

        {
            name: "Wood Polish",
            tier: [
                {
                    tier: "T1",
                    have: t1polish,
                    need: needt1polish
                },
                {
                    tier: "T2",
                    have: t2polish,
                    need: needt2polish
                },
                {
                    tier: "T3",
                    have: t3polish,
                    need: needt3polish
                },
                {
                    tier: "T4",
                    have: t4polish,
                    need: needt4polish
                },
                {
                    tier: "T5",
                    have: t5polish,
                    need: needt5polish
                }
            ]
        },

        {
            name: "Crop Oil",
            tier: [
                {
                    tier: "T1",
                    have: t1cropoil,
                    need: needt1cropoil
                },
                {
                    tier: "T2",
                    have: t2cropoil,
                    need: needt2cropoil
                },
                {
                    tier: "T3",
                    have: t3cropoil,
                    need: needt3cropoil
                },
                {
                    tier: "T4",
                    have: t4cropoil,
                    need: needt4cropoil
                },
                {
                    tier: "T5",
                    have: t5cropoil,
                    need: needt5cropoil
                }
            ]
        }
    ]
</script>

{#each tabledata as insert}
<Table data={insert} />
{/each}