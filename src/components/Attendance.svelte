<script>
    export let presence;
    export let data;

    let attendance_options = [
        ["P", "Present"],
        ["L", "Late"],
        ["?", "Absent"],
        ["M", "Medical"],
        ["F", "Cancelled"],
    ];
    $: {
        data = data;
    }
</script>

<div>
    {#each attendance_options as option}
        <div style="text-align: left">
            <label>
                <input
                    type="radio"
                    bind:group={presence}
                    name="attendance"
                    value={option[0]}
                />
                {option[1]}
            </label>
        </div>
    {/each}
</div>
