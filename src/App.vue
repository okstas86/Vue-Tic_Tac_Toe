<template>
	<main id="game-container">
		<ol id="players" class="highlight-player">
			<Player name="Player 1" symbol="X" :isActive="activePlayer === 'X'" />
			<Player name="Player 2" symbol="O" :isActive="activePlayer === 'O'" />
		</ol>
		<GameBoard @changeActivePlayer="handleActivePlayer" />
	</main>
</template>

<script setup>
import { ref } from 'vue'
import Player from './components/Player.vue'
import GameBoard from './components/GameBoard.vue'

const activePlayer = ref('O')

const handleActivePlayer = newActivePlayer => {
	activePlayer.value = newActivePlayer
}
</script>
