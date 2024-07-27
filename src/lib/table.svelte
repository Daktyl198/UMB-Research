<script>
    let { data } = $props();
</script>

<table>
    <tbody>
        <tr>
            <th class="name">
                {data.name}
            </th>
            <th>
                Have
            </th>
            <th>
                Need
            </th>
        </tr>
        {#each data.tier as datum}
        <tr>

            <td>{datum.tier}</td>
            <td>{datum.have}</td>
            <td>{Math.max(0, datum.need)}</td>
        </tr>
        {/each}
        
    </tbody>
</table>

<style>
    .name {
        color: #9900FF;
    }
    th {
        width: 8rem;
        background: var(--menu);
        padding: 18px 0;
    }

    td {
        padding: 18px 0;
    }

    tr {
        background-color: var(--tgradient);
    }

    tr:nth-of-type(odd) {
        background: var(--bgradient);
    }

    table {
        border: 1px solid #EEEEEE;
        text-align: center;
        margin: 4rem;
        margin-top: 2rem;
        margin-bottom: 2rem;
        display: inline-block;
    }
</style>