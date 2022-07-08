<script>
	import template_data from "./timetable.json";
	import Timetable from "./components/timetable.svelte";
	import InfoBar from "./components/InfoBar.svelte";
	// This line is used to prevent svelte from editing the permanent json file
	let data = template_data;
	let spell_five_cancelled = false;
	let subjects = data["Subjects"];
	// These start of null so no subject is selected
	let selected_day = null;
	let selected_spell = null;
	let selected_subject = null;
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
		bind:selected_day
		bind:selected_spell
		bind:spell_five_cancelled
	/>
</main>

<style>
	main {
		display: flex;
	}
</style>
