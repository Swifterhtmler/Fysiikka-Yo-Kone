<script>
	import { goto } from '$app/navigation';
</script>

<div class="pomodoro-container">
	<h1>Pomodoro Timer</h1>
	<button on:click={() => goto('/')}>← Takaisin</button>
</div>

<style>
	.pomodoro-container {
		padding: 20px;
		text-align: center;
	}
</style>
