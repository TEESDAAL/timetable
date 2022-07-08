<script>
    import AddHomework from "./AddHomework.svelte";
    import Attendance from "./Attendance.svelte";
    import DisplayHomework from "./DisplayHomework.svelte";
    export let selected_subject;
    export let subjects;
    export let data;
    export let selected_day;
    export let selected_spell;
    export let spell_five_cancelled;

    $: {
        if (spell_five_cancelled === true && selected_spell === "Spell 5") {
            selected_subject = null;
            selected_day = null;
            selected_spell = null;
        }
    }
</script>

<section>
    <label>
        <input type="checkbox" bind:checked={spell_five_cancelled} />
        Spell five cancelled?
    </label>
    <!-- Only render subject based information if the subject is defined -->
    {#if selected_subject !== null}
        <h1>
            {selected_subject.subject_name} - {selected_day}
            {selected_spell}
        </h1>
        <p>
            {selected_subject.teacher_name} - ({selected_subject.teacher_code})
        </p>
        <p>Room: {selected_subject.room_number}</p>
        <AddHomework bind:subjects bind:selected_subject />
        <DisplayHomework bind:selected_subject bind:subjects />
        <Attendance
            bind:presence={data[selected_day][selected_spell].attendance}
            bind:data
        />
    {/if}
</section>

<style>
    section {
        display: flex;
        flex-direction: column;
        align-items: center;
        width: 20vw;
        text-align: center;
    }
</style>
