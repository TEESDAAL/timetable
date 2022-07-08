<script>
    import Cell from "./Cell.svelte";
    export let data;
    export let subjects;
    export let selected_subject;
    export let selected_day;
    export let selected_spell;
    export let spell_five_cancelled;
    let possible_spells = [
        "Spell 1",
        "Spell 2",
        "Spell 3",
        "Ako",
        "Spell 4",
        "Spell 5",
    ];
</script>

<table>
    <!-- Evenly sets the width of all the columns in the table-->
    <colgroup>
        <col
            style="width: calc(80vw / {Object.keys(data).slice(0, -1).length +
                1});"
            span={Object.keys(data).slice(0, -1).length + 1}
        />
    </colgroup>
    <tr>
        <!-- Empty th is so the top right of the table is blank -->
        <th id="empty" />
        <!-- Loop through all the days of the school week
        slice is to remove the subjects from the list-->
        {#each Object.keys(data).slice(0, -1) as day}
            <th>{day}</th>
        {/each}
    </tr>
    <!-- Loop through all the spells and query each day for the spell -->
    {#each possible_spells as spell}
        <tr>
            <!-- Doesn't display the last row in the table
            if spell five is cancelled. -->
            <!-- Since tables are formatted by rows this code gets each spell
            then for that spell query each day for the subject-->
            {#if spell_five_cancelled && spell === "Spell 5"}
                <th
                    colspan={Object.keys(data).slice(0, -1).length + 1}
                    align="center"
                    id="spell_five_cancelled"
                >
                    Spell five cancelled
                </th>
            {:else}
                <th>{spell}</th>
            {/if}
            <!-- Loop through each day of the school week -->
            {#each Object.keys(data).slice(0, -1) as day}
                {#if data[day][spell] === undefined}
                    <td class="free-spell" />
                {:else if spell_five_cancelled && spell === "Spell 5"}
                    <td class="free-spell" />
                {:else}
                    <Cell
                        {subjects}
                        bind:data
                        bind:selected_subject
                        bind:day
                        bind:spell
                        bind:presence={data[day][spell].attendance}
                        bind:selected_day
                        bind:selected_spell
                    />
                {/if}
            {/each}
        </tr>
    {/each}
</table>

<style>
    * {
        margin: 0;
        padding: 0;
    }
    :root {
        --td-color: #31574c;
        --th-color: #a23530;
        --table-width: 75vw;
        --table-height: calc(100vh - 3px);
        --cell-width: calc(var(--table-width) / 6);
    }
    table {
        margin: 1.5px;
        border-spacing: 0;
        height: var(--table-height);
    }
    th {
        color: white;
        border-radius: 5px;
        background-color: var(--th-color);
        padding: 10px;
        border: 1.5px solid white;
    }
    :is(#empty, .free-spell) {
        visibility: hidden;
    }
</style>
