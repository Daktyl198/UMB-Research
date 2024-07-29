<script>
    import Header from "./lib/header.svelte";
    import Masonry from "./pages/masonry.svelte";
    import Smithing from "./pages/smithing.svelte";
    import Leatherworking from "./pages/leatherworking.svelte";
    import Tailoring from "./pages/tailoring.svelte";
    import Carpentry from "./pages/carpentry.svelte";
    import Scholar from "./pages/scholar.svelte";

    const currentPage = window.location.pathname.substring(1);

    const api = import.meta.env.VITE_API_URL;
    const urls = api.split(",");

    let ready = $state(false);
    let data = $state({});

    function get(query) {
        return data[query] || 0;
    }

    async function fetchData(url) {
        fetch(url)
            .then(response => response.json())
            .then(json => {
                json.inventorys.buildings.forEach((input) => {
                if (input.item == undefined) return;

                const name = input.item.name;

                if (name != undefined) {
                    if (data[name] == undefined) {data[name] = 0};

                    data[name] += Number(input.quantity);
                }
                });
            })
            .then(() => ready += 1);
    }

    urls.forEach(url => fetchData(url));

</script>

<Header />
<div class="notice">The numbers in (parenthesis) are the amount of that item currently in cargo form somewhere</div>
<main>
    {#if ready == urls.length}
        {#if currentPage === "Masonry"}
            <Masonry {data} {get}/>
        {:else if currentPage === "Smithing"}
            <Smithing {data} {get}/>
        {:else if currentPage === "Leatherworking"}
            <Leatherworking {data} {get}/>
        {:else if currentPage === "Tailoring"}
            <Tailoring {data} {get}/>
        {:else if currentPage === "Carpentry"}
            <Carpentry {data} {get}/>
        {:else if currentPage === "Scholar"}
            <Scholar {data} {get}/>
        {:else}     

            <h2>Masonry</h2>
            <Masonry {data} {get}/>

            <hr>

            <h2>Smithing</h2>
            <Smithing {data} {get}/>
            
            <hr>

            <h2>Tailoring</h2>
            <Tailoring {data} {get}/>

            <hr>

            <h2>Carpentry</h2>
            <Carpentry {data} {get}/>
        
            <hr>
            
            <h2>Leatherworking</h2>
            <Leatherworking {data} {get}/>

            <hr>

            <h2>Scholar</h2>
            <Scholar {data} {get}/>
            
        {/if}

    {:else}
        <h2>Loading</h2>
    {/if}
</main>


<style>
    .notice {
        color: var(--text);
        font-size: 0.9em;
        font-style: italic;
        text-align: center;
        margin-top: 1em;
    }

    main {
        background: var(--bg);
        text-align: center;
        max-width: 75vw;
        margin-left: auto;
        margin-right: auto;
    }

    h2 {
        text-decoration: underline;
        font-weight: medium;
    }
    
    hr {
        height: 1px;
        color: var(--text);
        background: var(--text);
        font-size: 0;
        border: 0;
    }

</style>