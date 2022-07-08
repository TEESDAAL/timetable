<script>
    export let selected_subject;
    export let subjects;
    /**
     * Removes the homework from a selected subject by index
     * @param index (int) The index of the homework to be removed
     * @param subject (object) The subject to remove the homework from
     */
    function remove_homework(subject, index) {
        console.log(subject);
        selected_subject.home_work.splice(index, 1);
        // The following lines are necessary to tell svelte that the data has changed
        selected_subject.home_work = selected_subject.home_work;
        subjects = subjects;
    }
</script>

<!-- Change what is message is displayed depending on the amount of homework -->
{#if selected_subject.home_work.length > 0}
    <h2>Homework:</h2>
{:else}
    <h3>No Homework for {selected_subject.subject_name} :)</h3>
{/if}
<ul>
    <!-- Loops through all the homework for selected_subject and displays it-->
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
