<template>
	<main id="game-container">
		<ol id="players">
			<Player name="Player 1" symbol="X" />
			<Player name="Player 2" symbol="O" />
		</ol>
	</main>
</template>

<script setup>
import Player from './components/Player.vue'
</script>
