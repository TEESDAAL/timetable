<script>
	import template_data from "./timetable.json";
	import Timetable from "./components/timetable.svelte";
	import InfoBar from "./components/InfoBar.svelte";
	let data = template_data;
	let spell_five_cancelled = false;
	let subjects = data["Subjects"];
	let selected_day = "Monday";
	let selected_spell = "Spell 1";
	let selected_subject =
		data["Subjects"][data[selected_day][selected_spell].subject_name];
	console.log(selected_subject);
</script>

<main>
	<Timetable
		{data}
		{subjects}
		bind:selected_subject
		bind:selected_day
		bind:selected_spell
		{spell_five_cancelled}
	/>
	<InfoBar
		bind:selected_subject
		bind:subjects
		bind:data
		{selected_day}
		{selected_spell}
		bind:spell_five_cancelled
	/>
</main>

<style>
	main {
		display: flex;
	}
</style>
