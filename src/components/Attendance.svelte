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
    // This code is run whenever a local variable is updated
    $: {
        // This line is used to cause the svelte to update
        data = data;
    }
</script>

<div>
    <!-- Displays the attendance options and sets the
        presence variable equal to the selected value-->
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
