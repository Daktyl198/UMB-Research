<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;

    const clothResearch = get("Advanced Cloth Research");
    const leatherResearch = get("Advanced Leather Research");
    const metalResearch = get("Advanced Metal Research");
    const woodResearch = get("Advanced Wood Research");
    const stoneResearch = get("Advanced Stone Research");

    const needClothResearch = amount - clothResearch;
    const needLeatherResearch = amount - leatherResearch;
    const needMetalResearch = amount - metalResearch;
    const needWoodResearch = amount - woodResearch;
    const needStoneResearch = amount - stoneResearch;

    const t1vial = get("Rough Glass Vial");
    const t2vial = get("Simple Glass Vial");
    const t3vial = get("Sturdy Glass Vial");
    const t4vial = get("Fine Glass Vial");
    const t5vial = get("Exquisite Glass Vial");

    const t1carving = get("Beginner's Stone Carvings");
    const t2carving = get("Novice Stone Carvings");
    const t3carving = get("Essential Stone Carvings");
    const t4carving = get("Proficient Stone Carvings");
    const t5carving = get("Advanced Stone Carvings");

    const t1journal = get("Beginner's Study Journal");
    const t2journal = get("Novice Study Journal");
    const t3journal = get("Essential Study Journal");
    const t4journal = get("Proficient Study Journal");
    const t5journal = get("Advanced Study Journal");

    const t1parchment = get("Rough Parchment");
    const t2parchment = get("Simple Parchment");
    const t3parchment = get("Sturdy Parchment");
    const t4parchment = get("Fine Parchment");
    const t5parchment = get("Exquisite Parchment");

    const t1bark = get("Rough Tree Bark");
    const t2bark = get("Simple Tree Bark");
    const t3bark = get("Sturdy Tree Bark");
    const t4bark = get("Fine Tree Bark");
    const t5bark = get("Exquisite Tree Bark");

    const t1ink = get("Basic Ink");
    const t2ink = get("Simple Ink");
    const t3ink = get("Infused Ink");
    const t4ink = get("Fine Ink");
    const t5ink = get("Exquisite Ink");

    const t1oil = get("Basic Fish Oil");
    const t2oil = get("Simple Fish Oil");
    const t3oil = get("Infused Fish Oil");
    const t4oil = get("Fine Fish Oil");
    const t5oil = get("Exquisite Fish Oil");

    const t1pigment = get("Basic Pigment");
    const t2pigment = get("Simple Pigment");
    const t3pigment = get("Infused Pigment");
    const t4pigment = get("Fine Pigment");
    const t5pigment = get("Exquisite Pigment");

    const t1flower = get("Basic Flower");
    const t2flower = get("Simple Flower");
    const t3flower = get("Infused Flower");
    const t4flower = get("Fine Flower");
    const t5flower = get("Exquisite Flower");

    //---------------------

    const t5plankpackage = get("Refined Exquisite Wood Plank Package") * 10;

    const t5plank = get("Refined Exquisite Plank") + t5plankpackage;

    const t1polish = get("Basic Wood Polish");
    const t2polish = get("Simple Wood Polish");
    const t3polish = get("Infused Wood Polish");
    const t4polish = get("Fine Wood Polish");
    const t5polish = get("Exquisite Wood Polish");

    const t5leatherpackage = get("Refined Exquisite Leather Package") * 10;

    const t5leather = get("Refined Exquisite Leather") + t5leatherpackage;

    const t1treatment = get("Basic Leather Treatment");
    const t2treatment = get("Simple Leather Treatment");
    const t3treatment = get("Infused Leather Treatment");
    const t4treatment = get("Fine Leather Treatment");
    const t5treatment = get("Exquisite Leather Treatment");

    const t5ingotpackage = get("Refined Lirium Ingot Package") * 10;

    const t5ingot = get("Refined Lirium Ingot") + t5ingotpackage;

    const t1solvent = get("Basic Metal Solvent");
    const t2solvent = get("Simple Metal Solvent");
    const t3solvent = get("Infused Metal Solvent");
    const t4solvent = get("Fine Metal Solvent");
    const t5solvent = get("Exquisite Metal Solvent");

    const needt5plank = (amount - woodResearch) - t5plank;

    const needt5polish = needt5plank - t5polish;
    const needt4polish = (needt5polish *2) - t4polish;
    const needt3polish = (needt4polish *2) - t3polish;
    const needt2polish = (needt3polish *2) - t2polish;
    const needt1polish = (needt2polish) - t1polish;

    const needt5leather = (amount - leatherResearch) - t5leather;

    const needt5treatment = needt5leather - t5treatment;
    const needt4treatment = (needt5treatment *2) - t4treatment;
    const needt3treatment = (needt4treatment *2) - t3treatment;
    const needt2treatment = (needt3treatment *2) - t2treatment;
    const needt1treatment = (needt2treatment) - t1treatment;

    const needt5ingot = (amount - metalResearch) - t5ingot;

    const needt5solvent = needt5ingot - t5solvent;
    const needt4solvent = (needt5solvent *2) - t4solvent;
    const needt3solvent = (needt4solvent *2) - t3solvent;
    const needt2solvent = (needt3solvent *2) - t2solvent;
    const needt1solvent = (needt2solvent) - t1solvent;
    //-----------------------

    const needt5vial = (needt5polish + needt5treatment + needt5solvent) - t5vial;
    const needt4vial = (needt4polish + needt4treatment + needt4solvent) - t4vial;
    const needt3vial = (needt3polish + needt3treatment + needt3solvent) - t3vial;
    const needt2vial = (needt2polish + needt2treatment + needt2solvent) - t2vial;
    const needt1vial = (needt1polish + needt1treatment + needt1solvent) - t1vial;

    const needt5journal = (needClothResearch + needLeatherResearch + needMetalResearch + needWoodResearch + needStoneResearch) - t5journal;
    const needt4journal = (needt5journal * 2) - t4journal;
    const needt3journal = needt4journal * 2 - t3journal;
    const needt2journal = needt3journal * 2 - t2journal;
    const needt1journal = needt2journal - t1journal;

    const needt5parchment = (needt5journal *2) - t5parchment;
    const needt4parchment = (needt4journal *2) - t4parchment;
    const needt3parchment = (needt3journal *2) - t3parchment;
    const needt2parchment = (needt2journal *2) - t2parchment;
    const needt1parchment = (needt1journal *2) - t1parchment;

    const needt5bark = (needt5parchment *2) - t5bark;
    const needt4bark = (needt4parchment *2) - t4bark;
    const needt3bark = (needt3parchment *2) - t3bark;
    const needt2bark = (needt2parchment *2) - t2bark;
    const needt1bark = (needt1parchment *2) - t1bark;

    const needt5carving = needt5journal - t5carving;
    const needt4carving = needt4journal - t4carving;
    const needt3carving = needt3journal - t3carving;
    const needt2carving = needt2journal - t2carving;
    const needt1carving = needt1journal - t1carving;

    const needt5ink = needt5journal*2 - t5ink;
    const needt4ink = needt4journal*2 - t4ink;
    const needt3ink = needt3journal*2 - t3ink;
    const needt2ink = needt2journal*2 - t2ink;
    const needt1ink = needt1journal*2 - t1ink;

    const needt5oil = needt5ink*2 - t5oil;
    const needt4oil = needt4ink*2 - t4oil;
    const needt3oil = needt3ink*2 - t3oil;
    const needt2oil = needt2ink*2 - t2oil;
    const needt1oil = needt1ink*2 - t1oil;

    const needt5pigment = needt5ink - t5pigment;
    const needt4pigment = needt4ink - t4pigment;
    const needt3pigment = needt3ink - t3pigment;
    const needt2pigment = needt2ink - t2pigment;
    const needt1pigment = needt1ink - t1pigment;

    const needt5flower = needt5pigment*5 - t5flower;
    const needt4flower = needt4pigment*5 - t4flower;
    const needt3flower = needt3pigment*5 - t3flower;
    const needt2flower = needt2pigment*5 - t2flower;
    const needt1flower = needt1pigment*5 - t1flower;

    const tabledata = [
        {
            name: "Research",
            tier: [
                {
                    tier: "Cloth",
                    have: clothResearch,
                    need: needClothResearch
                },
                {
                    tier: "Leather",
                    have: leatherResearch,
                    need: needLeatherResearch
                },
                {
                    tier: "Metal",
                    have: metalResearch,
                    need: needMetalResearch
                },
                {
                    tier: "Wood",
                    have: woodResearch,
                    need: needWoodResearch
                },
                {
                    tier: "Stone",
                    have: stoneResearch,
                    need: needStoneResearch
                }
            ]
        },
        {
            name: "Vials",
            tier: [
                {
                    tier: "T1",
                    have: t1vial,
                    need: needt1vial
                },
                {
                    tier: "T2",
                    have: t2vial,
                    need: needt2vial
                },
                {
                    tier: "T3",
                    have: t3vial,
                    need: needt3vial
                },
                {
                    tier: "T4",
                    have: t4vial,
                    need: needt4vial
                },
                {
                    tier: "T5",
                    have: t5vial,
                    need: needt5vial
                }
            ]
        },
        {
            name: "Journals",
            tier: [
                {
                    tier: "T1",
                    have: t1journal,
                    need: needt1journal
                },
                {
                    tier: "T2",
                    have: t2journal,
                    need: needt2journal
                },
                {
                    tier: "T3",
                    have: t3journal,
                    need: needt3journal
                },
                {
                    tier: "T4",
                    have: t4journal,
                    need: needt4journal
                },
                {
                    tier: "T5",
                    have: t5journal,
                    need: needt5journal
                }
            ]
        },
        {
            name: "Parchment",
            tier: [
                {
                    tier: "T1",
                    have: t1parchment,
                    need: needt1parchment
                },
                {
                    tier: "T2",
                    have: t2parchment,
                    need: needt2parchment
                },
                {
                    tier: "T3",
                    have: t3parchment,
                    need: needt3parchment
                },
                {
                    tier: "T4",
                    have: t4parchment,
                    need: needt4parchment
                },
                {
                    tier: "T5",
                    have: t5parchment,
                    need: needt5parchment
                }
            ]
        },
        {
            name: "Bark",
            tier: [
                {
                    tier: "T1",
                    have: t1bark,
                    need: needt1bark
                },
                {
                    tier: "T2",
                    have: t2bark,
                    need: needt2bark
                },
                {
                    tier: "T3",
                    have: t3bark,
                    need: needt3bark
                },
                {
                    tier: "T4",
                    have: t4bark,
                    need: needt4bark
                },
                {
                    tier: "T5",
                    have: t5bark,
                    need: needt5bark
                }
            ]
        },
        {
            name: "Carvings",
            tier: [
                {
                    tier: "T1",
                    have: t1carving,
                    need: needt1carving
                },
                {
                    tier: "T2",
                    have: t2carving,
                    need: needt2carving
                },
                {
                    tier: "T3",
                    have: t3carving,
                    need: needt3carving
                },
                {
                    tier: "T4",
                    have: t4carving,
                    need: needt4carving
                },
                {
                    tier: "T5",
                    have: t5carving,
                    need: needt5carving
                }
            ]
        },
        {
            name: "Ink",
            tier: [
                {
                    tier: "T1",
                    have: t1ink,
                    need: needt1ink
                },
                {
                    tier: "T2",
                    have: t2ink,
                    need: needt2ink
                },
                {
                    tier: "T3",
                    have: t3ink,
                    need: needt3ink
                },
                {
                    tier: "T4",
                    have: t4ink,
                    need: needt4ink
                },
                {
                    tier: "T5",
                    have: t5ink,
                    need: needt5ink
                }
            ]
        },
        {
            name: "Fish Oil",
            tier: [
                {
                    tier: "T1",
                    have: t1oil,
                    need: needt1oil
                },
                {
                    tier: "T2",
                    have: t2oil,
                    need: needt2oil
                },
                {
                    tier: "T3",
                    have: t3oil,
                    need: needt3oil
                },
                {
                    tier: "T4",
                    have: t4oil,
                    need: needt4oil
                },
                {
                    tier: "T5",
                    have: t5oil,
                    need: needt5oil
                }
            ]
        },
        {
            name: "Pigment",
            tier: [
                {
                    tier: "T1",
                    have: t1pigment,
                    need: needt1pigment
                },
                {
                    tier: "T2",
                    have: t2pigment,
                    need: needt2pigment
                },
                {
                    tier: "T3",
                    have: t3pigment,
                    need: needt3pigment
                },
                {
                    tier: "T4",
                    have: t4pigment,
                    need: needt4pigment
                },
                {
                    tier: "T5",
                    have: t5pigment,
                    need: needt5pigment
                }
            ]
        },
        {
            name: "Flowers",
            tier: [
                {
                    tier: "T1",
                    have: t1flower,
                    need: needt1flower
                },
                {
                    tier: "T2",
                    have: t2flower,
                    need: needt2flower
                },
                {
                    tier: "T3",
                    have: t3flower,
                    need: needt3flower
                },
                {
                    tier: "T4",
                    have: t4flower,
                    need: needt4flower
                },
                {
                    tier: "T5",
                    have: t5flower,
                    need: needt5flower
                }
            ]
        }
    ];

    console.log(tabledata);

</script>

{#each tabledata as insert}
    <Table data={insert} />
{/each}