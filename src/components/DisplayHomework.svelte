<script>
    export let selected_subject;
    export let subjects;
    /**
     * Removes the homework from a selected subject by index
     * @param index (int) The index of the homework to be removed
     */
    function remove_homework(index) {
        selected_subject.home_work.splice(index, 1);
        // The following lines are necessary to tell svelte that the data has changed
        selected_subject.home_work = selected_subject.home_work;
        subjects = subjects;
    }
</script>

{#if selected_subject.home_work.length > 0}
    <h2>Homework:</h2>
{:else}
    <h3>No Homework for {selected_subject.subject_name} :)</h3>
{/if}
<ul>
    {#each selected_subject.home_work as work, i}
        <li>
            {work}<span
                class="remove"
                on:click={remove_homework(selected_subject, i)}>➖</span
            >
        </li>
    {/each}
</ul>

<style>
    .remove {
        cursor: pointer;
        visibility: hidden;
    }

    li:hover .remove {
        visibility: visible;
    }
</style>
