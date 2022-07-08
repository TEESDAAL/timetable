<script>
    export let subjects;
    export let data;
    export let day;
    export let spell;
    export let selected_subject;
    export let presence;
    export let selected_day;
    export let selected_spell;

    let subject = data[day][spell];
</script>

<td
    class="spell-section"
    tabindex="0"
    on:click={() => {
        selected_subject = subjects[subject.subject_name];
        selected_day = day;
        selected_spell = spell;
    }}
    ><!-- on:click sets the selected subject day and
        the spell to the info in this cell -->
    <div class="spell">
        <!-- Name of the subject -->
        <p>{subject.subject_name}</p>
        <span>
            <!-- Time in (HH:MM - HH:MM) format -->
            (
            {subject.start_time}
            - {subject.end_time}
            )
            <br />
            Room: {subjects[subject.subject_name].room_number}
        </span>
        <span>{presence}</span>
        <!-- Displays the amount of homework in a subject if it is greater than 0-->
        {#if subjects[data[day][spell].subject_name].home_work.length > 0}
            <div class="homework-alert">
                {subjects[subject.subject_name].home_work.length}
            </div>
        {/if}
    </div>
</td>

<style>
    td {
        background-color: #31574c;
        color: white;
        border-radius: 5px;
        text-align: center;
        border: 1.5px solid;
    }
    .spell {
        display: flex;
        flex-direction: column;
        align-items: center;
        position: relative;
    }
    .homework-alert {
        background-color: red;
        position: absolute;
        transform: translate(-50%, -50%);
        top: 1.5ch;
        left: calc(100% - 2ch);
        width: 2ch;
        height: 2ch;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
    }
    td span {
        font-size: 0.7em;
    }
</style>
