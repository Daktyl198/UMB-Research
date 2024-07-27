<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;
    const metalResearch = get("Advanced Metal Research");

    const t1ingotpackage = get("Pyrelite Ingot Package") * 10;
    const t2ingotpackage = get("Aurumite Ingot Package") * 10;
    const t3ingotpackage = get("Ferralith Ingot Package") * 10;
    const t4ingotpackage = get("Elenvar Ingot Package") * 10;
    const t5ingotpackage = get("Lirium Ingot Package") * 10;

    const t5refinedingotpackage = get("Refined Lirium Ingot Package") * 10;

    const t5refinedingot = get("Refined Lirium Ingot") + t5refinedingotpackage;

    const t1ingot = get("Pyrelite Ingot") + t1ingotpackage;
    const t2ingot = get("Aurumite Ingot") + t2ingotpackage;
    const t3ingot = get("Ferralith Ingot") + t3ingotpackage;
    const t4ingot = get("Elenvar Ingot") + t4ingotpackage;
    const t5ingot = get("Lirium Ingot") + t5ingotpackage;

    const t1Braxite = get("Rough Braxite");
    const t2Braxite = get("Simple Braxite");
    const t3Braxite = get("Sturdy Braxite");
    const t4Braxite = get("Fine Braxite");
    const t5Braxite = get("Exquisite Braxite");

    const t1solvent = get("Basic Metal Solvent");
    const t2solvent = get("Simple Metal Solvent");
    const t3solvent = get("Infused Metal Solvent");
    const t4solvent = get("Fine Metal Solvent");
    const t5solvent = get("Exquisite Metal Solvent");

    const needt5refinedingot = (amount - metalResearch) - t5refinedingot;

    const needt5ingot = needt5refinedingot - t5ingot;
    const needt4ingot = (needt5ingot) - t4ingot;
    const needt3ingot = (needt4ingot) - t3ingot;
    const needt2ingot = (needt3ingot) - t2ingot;
    const needt1ingot = needt2ingot - t1ingot;

    const needt5solvent = needt5refinedingot - t5solvent;
    const needt4solvent = (needt5solvent *2) - t4solvent;
    const needt3solvent = (needt4solvent *2) - t3solvent;
    const needt2solvent = (needt3solvent *2) - t2solvent;
    const needt1solvent = needt2solvent - t1solvent;

    const needt5Braxite = (needt5solvent) - t5Braxite;
    const needt4Braxite = (needt4solvent) - t4Braxite;
    const needt3Braxite = (needt3solvent) - t3Braxite;
    const needt2Braxite = (needt2solvent) - t2Braxite;
    const needt1Braxite = (needt1solvent) - t1Braxite;

    const tabledata = [
        {
            name: "Refined ingot",
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
                    have: `${t5refinedingot} (${t5refinedingotpackage})`,
                    need: needt5refinedingot
                }
            ]
        },
        {
            name: "Ingots",
            tier: [
                {
                    tier: "T1",
                    have: `${t1ingot} (${t1ingotpackage})`,
                    need: needt1ingot
                },
                {
                    tier: "T2",
                    have: `${t2ingot} (${t2ingotpackage})`,
                    need: needt2ingot
                },
                {
                    tier: "T3",
                    have: `${t3ingot} (${t3ingotpackage})`,
                    need: needt3ingot
                },
                {
                    tier: "T4",
                    have: `${t4ingot} (${t4ingotpackage})`,
                    need: needt4ingot
                },
                {
                    tier: "T5",
                    have: `${t5ingot} (${t5ingotpackage})`,
                    need: needt5ingot
                }
            ]
        },
        {
            name: "Braxite",
            tier: [
                {
                    tier: "T1",
                    have: t1Braxite,
                    need: needt1Braxite
                },
                {
                    tier: "T2",
                    have: t2Braxite,
                    need: needt2Braxite
                },
                {
                    tier: "T3",
                    have: t3Braxite,
                    need: needt3Braxite
                },
                {
                    tier: "T4",
                    have: t4Braxite,
                    need: needt4Braxite
                },
                {
                    tier: "T5",
                    have: t5Braxite,
                    need: needt5Braxite
                }
            ]
        },
        {
            name: "Solvent",
            tier: [
                {
                    tier: "T1",
                    have: t1solvent,
                    need: needt1solvent
                },
                {    
                    tier: "T2",
                    have: t2solvent,
                    need: needt2solvent
                },
                {
                    tier: "T3",
                    have: t3solvent,
                    need: needt3solvent
                },
                {
                    tier: "T4",
                    have: t4solvent,
                    need: needt4solvent
                },
                {
                    tier: "T5",
                    have: t5solvent,
                    need: needt5solvent
                }
            ]
        }
    ]

</script>

{#each tabledata as insert}
<Table data={insert} />
{/each}