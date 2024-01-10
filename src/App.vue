<template>
	<main>
		<div id="game-container">
			<ol id="players" class="highlight-player">
				<Player name="Player 1" symbol="X" :isActive="activePlayer === 'X'" />
				<Player name="Player 2" symbol="O" :isActive="activePlayer === 'O'" />
			</ol>
			<GameBoard @changeActivePlayer="handleActivePlayer" />
		</div>
		<Log :moveData="moveData" />
	</main>
</template>

<script setup>
import { ref } from 'vue'
import Player from './components/Player.vue'
import Log from './components/Log.vue'
import GameBoard from './components/GameBoard.vue'

const activePlayer = ref('O')

let moveData = ref({})

const handleActivePlayer = (newActivePlayer, row, col) => {
	activePlayer.value = newActivePlayer

	moveData.value = { player: newActivePlayer, row: row, col: col }
}
</script>
