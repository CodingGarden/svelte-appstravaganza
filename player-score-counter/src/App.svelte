<script>
	import PlayerScore from './PlayerScore.svelte';

	let player1Score = 0;
	let player2Score = 0;

	function reset() {
		player1Score = 0;
		player2Score = 0;
	}
</script>

<main>
	<PlayerScore bind:playerScore={player1Score} playerName="Player 1" />
	<PlayerScore bind:playerScore={player2Score} playerName="Player 2" />
	<button on:click={reset}  class="contrast outline">RESET</button>
</main>

<style>
</style>