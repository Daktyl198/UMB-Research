<script>
    const {data, get} = $props();
    import Table from '../lib/table.svelte';

    const amount = 25;
    const stoneResearch = get("Advanced Stone Research");

    const t5refinedbrickpackage = get("Refined Exquisite Brick Package") * 10;

    const t1brickpackage = get("Rough Brick Package") * 10;
    const t2brickpackage = get("Simple Brick Package") * 10;
    const t3brickpackage = get("Sturdy Brick Package") * 10;
    const t4brickpackage = get("Fine Brick Package") * 10;
    const t5brickpackage = get("Exquisite Brick Package") * 10;

    const t5refinedbrick = get("Refined Exquisite Brick") + t5refinedbrickpackage;

    const t1brick = get("Rough Brick") + t1brickpackage;
    const t2brick = get("Simple Brick") + t2brickpackage;
    const t3brick = get("Sturdy Brick") + t3brickpackage;
    const t4brick = get("Fine Brick") + t4brickpackage;
    const t5brick = get("Exquisite Brick") + t5brickpackage;

    const t1gypsite = get("Rough Gypsite");
    const t2gypsite = get("Simple Gypsite");
    const t3gypsite = get("Sturdy Gypsite");
    const t4gypsite = get("Fine Gypsite");
    const t5gypsite = get("Exquisite Gypsite");

    const t1crushedshell = get("Crushed Rough Shells");
    const t2crushedshell = get("Crushed Simple Shells");
    const t3crushedshell = get("Crushed Sturdy Shells");
    const t4crushedshell = get("Crushed Fine Shells");
    const t5crushedshell = get("Crushed Exquisite Shells");

    const t1firesand = get("Basic Firesand");
    const t2firesand = get("Simple Firesand");
    const t3firesand = get("Infused Firesand");
    const t4firesand = get("Fine Firesand");
    const t5firesand = get("Exquisite Firesand");

    const needt5refinedbrick = (amount - stoneResearch) - t5refinedbrick;


    const needt5brick = needt5refinedbrick - t5brick;
    const needt4brick = (needt5brick) - t4brick;
    const needt3brick = (needt4brick) - t3brick;
    const needt2brick = (needt3brick) - t2brick;
    const needt1brick = needt2brick - t1brick;

    const needt5firesand = needt5refinedbrick - t5firesand;
    const needt4firesand = (needt5firesand *2) - t4firesand;
    const needt3firesand = (needt4firesand *2) - t3firesand;
    const needt2firesand = (needt3firesand *2) - t2firesand;
    const needt1firesand = needt2firesand - t1firesand;

    const needt5crushedshell = needt5firesand - t5crushedshell;
    const needt4crushedshell = needt4firesand - t4crushedshell;
    const needt3crushedshell = needt3firesand - t3crushedshell;
    const needt2crushedshell = needt2firesand - t2crushedshell;
    const needt1crushedshell = needt1firesand - t1crushedshell;

    const needt5gypsite = needt5firesand - t5gypsite;
    const needt4gypsite = needt4firesand - t4gypsite;
    const needt3gypsite = needt3firesand - t3gypsite;
    const needt2gypsite = needt2firesand - t2gypsite;
    const needt1gypsite = needt1firesand - t1gypsite;

    const tabledata = [
        {
            name: "Refined Brick",
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
                    have: `${t5refinedbrick} (${t5refinedbrickpackage})`,
                    need: needt5refinedbrick
                }
            ]
        },
        {
            name: "Bricks",
            tier: [
                {
                    tier: "T1",
                    have: `${t1brick} (${t1brickpackage})`,
                    need: needt1brick
                },
                {
                    tier: "T2",
                    have: `${t2brick} (${t2brickpackage})`,
                    need: needt2brick
                },
                {
                    tier: "T3",
                    have: `${t3brick} (${t3brickpackage})`,
                    need: needt3brick
                },
                {
                    tier: "T4",
                    have: `${t4brick} (${t4brickpackage})`,
                    need: needt4brick
                },
                {
                    tier: "T5",
                    have: `${t5brick} (${t5brickpackage})`,
                    need: needt5brick
                }
            ]
        },
        {
            name: "Firesand",
            tier: [
                {
                    tier: "T1",
                    have: t1firesand,
                    need: needt1firesand
                },
                {
                    tier: "T2",
                    have: t2firesand,
                    need: needt2firesand
                },
                {
                    tier: "T3",
                    have: t3firesand,
                    need: needt3firesand
                },
                {
                    tier: "T4",
                    have: t4firesand,
                    need: needt4firesand
                },
                {
                    tier: "T5",
                    have: t5firesand,
                    need: needt5firesand
                }
            ]
        },
        {
            name: "Crushed Shells",
            tier: [
                {
                    tier: "T1",
                    have: t1crushedshell,
                    need: needt1crushedshell
                },
                {
                    tier: "T2",
                    have: t2crushedshell,
                    need: needt2crushedshell
                },
                {
                    tier: "T3",
                    have: t3crushedshell,
                    need: needt3crushedshell
                },
                {
                    tier: "T4",
                    have: t4crushedshell,
                    need: needt4crushedshell
                },
                {
                    tier: "T5",
                    have: t5crushedshell,
                    need: needt5crushedshell
                }
            ]
        },
        {
            name: "Gypsite",
            tier: [
                {
                    tier: "T1",
                    have: t1gypsite,
                    need: needt1gypsite
                },
                {
                    tier: "T2",
                    have: t2gypsite,
                    need: needt2gypsite
                },
                {
                    tier: "T3",
                    have: t3gypsite,
                    need: needt3gypsite
                },
                {
                    tier: "T4",
                    have: t4gypsite,
                    need: needt4gypsite
                },
                {
                    tier: "T5",
                    have: t5gypsite,
                    need: needt5gypsite
                }
            ]
        }
    ]

</script>

{#each tabledata as insert}
<Table data={insert} />
{/each}