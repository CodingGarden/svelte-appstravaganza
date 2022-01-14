<script>
  export let playerName;
	export let playerScore = 0;

	function increaseplayerScore() {
		playerScore += 1;
	}

	function decreaseplayerScore() {
		playerScore -= 1;
		if (playerScore < 0) {
			playerScore = 0;
		}
	}
</script>

<div>
  <h2 class="center">{playerName}</h2>
  <h3 class="center">{playerScore}</h3>
  <button on:click={increaseplayerScore}>Up</button>
  <button on:click={decreaseplayerScore}>Down</button>
</div>

<style>
.center {
  text-align: center;
}
</style>