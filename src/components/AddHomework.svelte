<script>
    export let subjects;
    export let selected_subject;
    /**
     * Adds homework to a selected subject
     * @param subject_info is the subject to add the homework to
     * @param name is the name of the homework
     */
    function add_homework(subject_info, name) {
        subject_info.home_work.push(name);
        subject_info.home_work = subject_info.home_work;
        // Remove text from the input field
        homework_name = "";
        // The following lines is necessary to tell svelte that the data has changed
        subjects = subjects;
        selected_subject = selected_subject;
    }
    let homework_name = "";
</script>

<div id="add_homework">
    <input
        id="homework-name"
        bind:value={homework_name}
        type="text"
        placeholder="Add homework"
    />
    {#if homework_name.length > 0}
        <button on:click={add_homework(selected_subject, homework_name)}
            >➕</button
        >
    {/if}
</div>

<style>
    #add_homework {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
        width: 70%;
    }
</style>
